---
title: Configuración de Intune para la aplicación Classroom para iOS
titleSuffix: Microsoft Intune
description: Conozca la configuración de Intune que puede usar para controlar los valores de configuración de la aplicación Classroom en los dispositivos iOS.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/9/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: derriw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 40549d8fa9bead312f39ca9a782fb555e1022cd6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180415"
---
# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>Configuración de Intune para la aplicación Classroom para iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]
>[!NOTE]
>La configuración de Intune para la aplicación Classroom quedó obsoleta en Intune. Este artículo solo se aplica a los usuarios que tienen perfiles educativos existentes en Intune.

## <a name="introduction"></a>Introducción
[Classroom](https://itunes.apple.com/app/id1085319084) es una aplicación que ayuda a los profesores a guiar el aprendizaje y controlar los dispositivos de los estudiantes en el aula. Por ejemplo, la aplicación permite a los profesores:

- Abrir aplicaciones en los dispositivos de los estudiantes
- Bloquear y desbloquear la pantalla de un iPad
- Ver la pantalla del iPad de un estudiante
- Navegar por los iPad de los estudiantes hasta un marcador o el capítulo de un libro
- Mostrar la pantalla del iPad de un estudiante en un televisor Apple

Para configurar el aula en el dispositivo, debe crear y configurar un perfil de dispositivo de educación de iOS para Intune.

## <a name="before-you-start"></a>Antes de empezar

Tenga en cuenta lo siguiente antes de comenzar a configurar estas opciones:

- Tanto los iPad de los profesores como de los estudiantes deben estar inscritos en Intune.
- Asegúrese de que haya instalado la aplicación [Classroom de Apple](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) en el dispositivo del profesor. Puede instalar la aplicación manualmente o usar la [administración de aplicaciones de Intune](app-management.md).
- Debe configurar los certificados para autenticar las conexiones entre los dispositivos de profesores y estudiantes (consulte el paso 2, Crear y asignar un perfil Educación de iOS en Intune).
- Los iPad de los profesores y estudiantes deben estar en la misma red Wi-Fi y también tener habilitado Bluetooth.
- La aplicación Classroom se ejecuta en iPad supervisados con iOS 9.3 o una versión posterior.
- En esta versión, Intune admite la administración de un escenario 1:1, donde cada estudiante tiene su propio iPad exclusivo.


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Paso 1: importar los datos de la escuela en Azure Active Directory

Use School Data Sync (SDS) de Microsoft para importar los registros de la escuela desde un sistema de información de estudiantes (SIS) existente a Azure Active Directory (Azure AD).
SDS sincroniza la información de su SIS y la almacena en Azure AD. Azure AD es un sistema de administración de Microsoft que ayuda a organizar los usuarios y los dispositivos. Luego, puede utilizar estos datos para administrar sus estudiantes y clases. [Obtenga más información sobre cómo implementar SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Cómo importar datos con SDS

Puede importar información a SDS mediante uno de los siguientes métodos:

- [Archivos CSV](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1): exporte manualmente y compile archivos de valores separados por comas (.csv)
- [API de PowerSchool](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f): proveedor de SIS que simplifica la sincronización con Azure AD
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab): formato CSV que puede exportar y convertir para sincronizar con Azure AD

### <a name="find-out-more"></a>Obtenga más información

- [Obtener más información sobre la experiencia completa de sincronización de datos locales de escuelas en Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Obtener más información sobre School Data Sync de Microsoft](https://sds.microsoft.com/)
- [Obtener más información sobre las licencias en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>Paso 2: crear y asignar un perfil Educación de iOS en Intune

### <a name="configure-general-settings"></a>Configuración de las opciones generales

1. Inicie sesión en [Azure Portal](https://portal.azure.com).
2. Elija **All services** (Todos los servicios)  > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3. En el panel **Intune**, elija **Configuración del dispositivo**.
2. En el panel **Configuración del dispositivo**, en la sección **Administrar**, elija **Perfiles**.
5.  En el panel Perfiles, elija **Crear perfil**.
6.  En el panel **Crear perfil**, escriba un **Nombre** y una **Descripción** para el perfil Educación de iOS.
7.  En la lista desplegable **Plataforma**, elija **iOS**.
8.  En la lista desplegable **Tipo de perfil**, elija **Educación**.
9.  Elija **Configuración** > **Configurar**.


En la siguiente sección, creará certificados para establecer una relación de confianza entre los iPad de profesores y estudiantes. Se utilizan certificados para autenticar sin problemas y de forma silenciosa las conexiones entre los dispositivos sin tener que escribir nombres de usuario ni contraseñas.

>[!IMPORTANT]
>Los certificados de profesores y estudiantes que utilice deben ser emitidos por diferentes entidades de certificación (CA). Debe crear dos nuevas CA subordinadas conectadas a la infraestructura de certificados existente; una para los profesores y otra para los estudiantes.

Los perfiles de educación de iOS solo admiten certificados PFX. No se admiten certificados SCEP.

Los certificados creados deben admitir la autenticación de servidor y autenticación de usuario.

### <a name="configure-teacher-certificates"></a>Configuración de certificados de profesores

En el panel **Educación**, elija **Certificados de profesor**.

#### <a name="configure-teacher-root-certificate"></a>Configuración de certificado raíz de profesor

En **Certificado de raíz de profesor**, elija el botón Examinar. Seleccione el certificado de raíz con una de las siguientes extensiones:
- Extensión .cer (DER o con codificación Base64) 
- Extensión. P7B (con o sin cadena completa)

#### <a name="configure-teacher-pkcs12-certificate"></a>Configuración de certificados de profesores PKCS#12

En **Teacher PKCS#12 certificate** (Certificado de profesor PKCS#12), configure los siguientes valores:

- **Formato de nombre de sujeto**: Intune pone automáticamente el prefijo **leader** a los nombres comunes de los certificados de profesor. Los nombres comunes de los certificados de estudiantes tienen el prefijo **member**.
- **Entidad de certificación**: entidad de certificación (CA) empresarial que se ejecuta en una edición Enterprise de Windows Server 2008 R2 o versión posterior. No se admiten CA independientes. 
- **Nombre de la entidad de certificación**: escriba el nombre de la entidad de certificación.
- **Nombre de plantilla de certificado**: escriba el nombre de una plantilla de certificado que se haya agregado a una CA emisora. 
- **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
- **Período de validez del certificado**: especifique la cantidad de tiempo que queda antes de que expire el certificado.
Puede especificar un valor inferior al período de validez de la plantilla de certificado especificada, pero no superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora.

Cuando haya terminado la configuración de los certificados, haga clic en **Aceptar**.

### <a name="configure-student-certificates"></a>Configuración de certificados de estudiantes

1.  En el panel **Educación**, elija **Certificados de alumno**.
2.  En el panel **Certificados de alumno** de la lista **Tipos de certificados de dispositivo de alumno**, elija **1:1**.

#### <a name="configure-student-root-certificate"></a>Configuración de certificado raíz de estudiantes

En **Certificado de raíz de alumno**, elija el botón Examinar. Seleccione el certificado de raíz con una de las siguientes extensiones:
- Extensión .cer (DER o con codificación Base64) 
- Extensión. P7B (con o sin cadena completa)

#### <a name="configure-student-pkcs12-certificate"></a>Configuración de certificados de estudiantes PKCS#12

En **Student PKCS#12 certificate** (Certificado de estudiante PKCS#12), configure los siguientes valores:

- **Formato de nombre de sujeto**: Intune pone automáticamente el prefijo **leader** a los nombres comunes de los certificados de profesor. Los nombres comunes de los certificados de estudiantes tienen el prefijo **member**.
- **Entidad de certificación**: entidad de certificación (CA) empresarial que se ejecuta en una edición Enterprise de Windows Server 2008 R2 o versión posterior. No se admiten CA independientes. 
- **Nombre de la entidad de certificación**: escriba el nombre de la entidad de certificación.
- **Nombre de plantilla de certificado**: escriba el nombre de una plantilla de certificado que se haya agregado a una CA emisora. 
- **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
- **Período de validez del certificado**: especifique la cantidad de tiempo que queda antes de que expire el certificado.
Puede especificar un valor inferior al período de validez de la plantilla de certificado especificada, pero no superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora.

Cuando haya terminado la configuración de los certificados, haga clic en **Aceptar**.

## <a name="finish-up"></a>Finalizar

1.  En el panel **Educación**, elija Aceptar.
2.  En el panel **Crear perfil**, elija **Crear**.
    
Se creará el perfil y aparecerá en el panel con la lista de perfiles.

Asigne el perfil a los dispositivos de estudiante en los grupos de aula que se crearon al sincronizar los datos de la escuela con Azure AD (consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

## <a name="next-steps"></a>Pasos siguientes

Ahora cuando los profesores utilicen la aplicación Classroom, tendrán el control total sobre los dispositivos de los estudiantes.

Para obtener más información sobre la aplicación Classroom, vea [Ayuda de Classroom](https://help.apple.com/classroom/ipad/2.0/) en el sitio web de Apple.

Si quiere configurar dispositivos iPad compartidos para los estudiantes, vea [Cómo configurar las opciones de educación de Intune para los dispositivos iPad compartidos](education-settings-configure-ios-shared.md).
