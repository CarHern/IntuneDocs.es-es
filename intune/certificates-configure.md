---
title: Creación de un perfil de certificado en Microsoft Intune - Azure | Microsoft Docs
description: Para sus dispositivos, agregue o cree un perfil de certificado configurando un entorno de certificados PKCS o SCEP, exporte el certificado público, cree el perfil en Azure Portal y asigne el SCEP o PKCS a los perfiles de certificado de Microsoft Intune en Azure Portal
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 1a70e8a5e9ad973f5d2c94a146a9f263f461d0ab
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180568"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Configuración de un perfil de certificado para sus dispositivos en Microsoft Intune

A los usuarios se les concede acceso a los recursos corporativos a través de VPN, Wi-Fi o perfiles de correo electrónico. Mediante los certificados, estas conexiones se pueden autenticar. Cuando se usan certificados, no es necesario que los usuarios finales escriban nombres de usuario ni contraseñas para autenticarse.

Puede usar Intune para asignar estos certificados a los dispositivos que administra. Intune permite asignar y administrar los siguientes tipos de certificado:

- Protocolo de inscripción de certificados simple (SCEP)
- PKCS#12 (o PFX)

Cada uno de estos tipos de certificado tiene sus propios requisitos previos y de infraestructura.

## <a name="overview"></a>Introducción

1. Asegúrese de que se ha configurado la infraestructura de certificados correcta. Puede usar [certificados SCEP](certificates-scep-configure.md) y [certificados PKCS](certficates-pfx-configure.md).

2. Instale un certificado raíz o certificado de entidad de certificación (CA) intermedia en cada dispositivo para que el dispositivo reconozca la legitimidad de la entidad de certificación. Para ello, cree y asigne un **perfil de certificado de confianza**. Al asignar este perfil, los dispositivos que se administran con Intune solicitan y reciben el certificado raíz. Debe crear un perfil independiente para cada plataforma. Existen perfiles de certificado de confianza para las siguientes plataformas:

    - iOS 8.0 y versiones posteriores
    - macOS 10.11 y versiones posteriores
    - Android 4.0 y versiones posteriores
    - Perfil de trabajo Android
    - Windows 8.1 y posterior
    - Windows Phone 8.1 y versiones posteriores
    - Windows 10 y versiones posteriores

3. Cree perfiles de certificados para que los dispositivos soliciten un certificado para la autenticación del acceso al correo electrónico y a las redes VPN y Wi-Fi. Puede crear y asignar un perfil de certificado **PKCS** o **SCEP** para dispositivos que ejecutan las siguientes plataformas:

   - iOS 8.0 y versiones posteriores
   - Android 4.0 y versiones posteriores
   - Perfil de trabajo Android
   - Windows 10 para escritorios y Windows 10 Mobile y versiones posteriores

   Solo puede usar un perfil de certificado **SCEP** para dispositivos que ejecutan las siguientes plataformas:

   - macOS 10.9 y versiones posteriores
   - Windows Phone 8.1 y versiones posteriores

Cree un perfil independiente para cada plataforma de dispositivo. Cuando cree el perfil, asócielo con el perfil de certificado raíz de confianza que creó previamente.

### <a name="further-considerations"></a>Otras consideraciones

- Si no dispone de una entidad de certificación empresarial, debe crear una.
- Si usa perfiles SCEP, configure un servidor de Servicio de inscripción de dispositivos de red (NDES).
- Si planea usar perfiles SCEP o PKCS, descargue y configure Microsoft Intune Certificate Connector.


## <a name="step-1-configure-your-certificate-infrastructure"></a>Paso 1: configurar la infraestructura de certificados

Consulte uno de los temas siguientes para configurar la infraestructura de cada tipo de perfil de certificado:

- [Configuración y administración de certificados SCEP con Intune](certificates-scep-configure.md)
- [Configuración y administración de certificados PKCS con Intune](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>Paso 2: exportar el certificado de CA raíz de confianza

Exporte el certificado de entidades de certificación raíz de confianza como un certificado público (.cer) desde la CA emisora o desde cualquier dispositivo que confíe en esta. No exporte la clave privada (.pfx).

Este certificado se importa al configurar un perfil de certificado de confianza.

## <a name="step-3-create-trusted-certificate-profiles"></a>Paso 3: crear perfiles de certificado de confianza
Cree un perfil de certificado de confianza para poder crear un perfil de certificado SCEP o PKCS. Necesitará un perfil de certificado de confianza y un perfil SCEP o PKCS para cada plataforma de dispositivo. Los pasos para crear certificados de confianza son similares en todas las plataformas de dispositivos.

1. Inicie sesión en el [Portal de Azure](https://portal.azure.com).
2. Seleccione **Todos los servicios**, filtre por **Intune** y seleccione **Microsoft Intune**.
3. Seleccione **Configuración del dispositivo** > **Administrar** > **Perfiles** > **Crear perfil**.
4. Escriba un **Nombre** y una **Descripción** para el perfil de certificado de confianza.
5. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado de confianza. Las opciones son:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 y versiones posteriores**
    - **Windows 10 y versiones posteriores**

6. En la lista desplegable **Tipos de perfil**, elija **Certificado de confianza**.
7. Busque el certificado que guardó en la tarea 1 y haga clic en **Aceptar**.
8. Solo para dispositivos Windows 8.1 y Windows 10, seleccione el **almacén de destino** del certificado de confianza. Las opciones son:

    - **Almacén de certificados de equipo - Raíz**
    - **Almacén de certificados de equipo - Intermedio**
    - **Almacén de certificados de usuario - Intermedio**

9. Cuando haya terminado, elija **Aceptar**, vuelva al panel **Crear perfil** y seleccione **Crear**.

Se creará el perfil y aparecerá en la lista. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](device-profile-assign.md).

Es posible que los dispositivos Android muestren un mensaje que indica que un tercero ha instalado un certificado de confianza.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Paso 4: crear perfiles de certificado SCEP o PKCS

Consulte uno de los temas siguientes para configurar y asignar cada tipo de perfil de certificado:

- [Configuración y administración de certificados SCEP con Intune](certificates-scep-configure.md)
- [Configuración y administración de certificados PKCS con Intune](certficates-pfx-configure.md)

Después de haber creado un perfil de certificado de confianza, cree perfiles de certificado SCEP o PKCS para cada plataforma que quiera usar. Al crear un perfil de certificado SCEP, escriba un perfil de certificado de confianza para esa misma plataforma. Este paso vincula los dos perfiles de certificado, aunque todavía deberá asignar cada perfil por separado.

## <a name="next-steps"></a>Pasos siguientes
[Asignar perfiles de dispositivo](device-profile-assign.md)  
[Usar S/MIME para firmar y cifrar mensajes de correo electrónico](certificates-s-mime-encryption-sign.md)  
[Uso de la entidad de certificación de terceros](certificate-authority-add-scep-overview.md)
