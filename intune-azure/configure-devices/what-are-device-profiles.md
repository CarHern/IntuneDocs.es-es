---
title: "¿Qué son los perfiles de dispositivo de Microsoft Intune? | Versión preliminar de Intune Azure | Microsoft Docs"
description: "Versión preliminar de Intune Azure: conozca sobre los perfiles de dispositivo de Intune y cómo pueden ayudarle a administrar y proteger los dispositivos de su empresa."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89afae81076d563f4ebba289f8fa82eaea6ab234
ms.openlocfilehash: 0e126c067b5c212ae5bfe1cf69e01128a00b1c8e


---

# <a name="what-are-device-profiles"></a>¿Qué son los perfiles de dispositivo?
<!--- This topic doesn't really answer the topic title: What are device profiles?" It needs to answer that question, then it can go on to discuss what profiles are in Intune and how to use them. Linda--->

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Use la carga de trabajo **Configurar dispositivos** de Microsoft Intune para administrar la configuración y las características de todos los dispositivos administrados.

Cuando abra esta carga de trabajo, verá las siguientes opciones:

- **Overview** (Información general): esta página le proporciona información de estado e informes que le ayudan a supervisar las configuraciones de los dispositivos que ha asignado a usuarios y dispositivos.
- **Administrar perfiles**: en esta sección puede crear perfiles de configuración de dispositivo. Puede encontrar una lista debajo de todos los tipos de perfil que se pueden crear.
- **Setup Certificate Authority** (Configurar la entidad de certificación): este flujo de trabajo le guía por los pasos necesarios para configurar certificados. Deberá hacer esto si quiere trabajar con perfiles de certificado de Intune.

## <a name="getting-started"></a>Introducción

El flujo de trabajo para la creación de perfiles de dispositivo es similar para todos los perfiles. Lea [How to create Microsoft Intune device configuration profiles](/intune-azure/configure-devices/how-to-create-device-profiles) (Cómo crear perfiles de configuración de dispositivo de Microsoft Intune) para más información sobre cómo crear perfiles. Luego, lea la información específica sobre la creación de configuraciones para cada tipo de perfil.

Puede administrar las siguientes funcionalidades de sus dispositivos:

## <a name="device-restrictions"></a>Restricciones de dispositivos
Las restricciones de dispositivos permiten controlar una amplia variedad de configuraciones y características que se distribuyen en diversas categorías, como seguridad, explorador, hardware y configuración de uso compartido. Por ejemplo, puede crear un perfil de restricción de dispositivos que impida que los usuarios de dispositivos iOS accedan a la cámara del dispositivo.
Para más información, consulte [How to configure device restriction settings](how-to-configure-device-restrictions.md) (Configuración de la restricción de dispositivos). Compatible con Android, iOS, macOS, Windows 10 y Windows 10 Team.

## <a name="email"></a>Correo electrónico
Los perfiles de correo electrónico le permiten crear, implementar y supervisar la configuración de correo electrónico de Exchange ActiveSync en los dispositivos que administra. Al implementar esta configuración, se garantiza la coherencia, se reducen las llamadas al soporte técnico y se permite a los usuarios finales acceder al correo electrónico de la empresa en sus dispositivos personales sin necesidad de ninguna configuración por su parte.
Para más información, consulte [How to configure email settings](how-to-configure-email-settings.md) (Configuración del correo electrónico). Compatible con Android, iOS, Windows Phone 8.1 y Windows 10.

## <a name="wi-fi"></a>Wi-Fi
Use perfiles de Wi-Fi para implementar la configuración de red inalámbrica para los usuarios y dispositivos de la organización. Al implementar un perfil de Wi-Fi, los usuarios tendrán acceso a su red Wi-Fi corporativa sin tener que configurarla ellos mismos.
Para más información, consulte [How to configure Wi-Fi settings](how-to-configure-wi-fi-settings.md) (Configuración de Wi-Fi). Compatible con Android, iOS, macOS y Windows 8.1 (solo importación).

## <a name="vpn"></a>VPN
Las redes privadas virtuales (VPN) ofrecen a los usuarios un acceso remoto seguro a la red de la empresa. Los dispositivos utilizan un perfil de conexión VPN para iniciar una conexión con el servidor VPN. Use los perfiles de VPN para implementar la configuración de VPN para los usuarios y dispositivos de su organización, para que puedan conectarse de forma fácil y segura a la red.
Para más información, consulte [How to configure VPN settings](how-to-configure-vpn-settings.md) (Configuración de VPN).
Compatible con Android, iOS, macOS, Windows Phone 8.1, Windows 8.1 y Windows 10.

## <a name="certificates"></a>Certificados
Este tipo de perfil le permite configurar certificados SCEP y PKCS de confianza, que se pueden asignar a dispositivos y usarse para la autenticación de perfiles de Wi-Fi, VPN y correo electrónico.
Para más información, consulte [How to configure certificates](how-to-configure-certificates.md) (Configuración de certificados). Compatible con Android, iOS, Windows Phone 8.1, Windows 8.1 y Windows 10.

## <a name="education"></a>Education
Le ayuda a especificar los certificados correctos para el uso del dispositivo iOS en el entorno educativo.
Para más información, consulte [How to configure Intune education settings for iOS devices](education-settings-for-ios.md) (Configuración de dispositivos iOS para el entorno educativo). Solo compatible con iOS.

## <a name="edition-upgrade"></a>Actualización de la edición
Este tipo de perfil le permite actualizar automáticamente dispositivos que ejecutan algunas versiones de Windows 10 a una edición más reciente. Para más información, consulte [How to configure Windows 10 edition upgrades](how-to-configure-windows-10-edition-upgrade.md) (Configuración de actualizaciones de ediciones de Windows 10). Solo compatible con Windows 10.

## <a name="windows-information-protection"></a>Windows Information Protection
Windows Information Protection ayuda a protegerse contra la pérdida potencial de datos sin interferir con la experiencia de empleado. También ayuda a proteger los datos y aplicaciones empresariales ante las pérdidas de datos accidentales en dispositivos propiedad de la empresa y personales que los empleados llevan al trabajo sin necesidad de realizar cambios en su entorno u otras aplicaciones.
Para más información, consulte [How to configure Windows Information Protection](how-to-configure-windows-information-protection.md) (Configuración de Windows Information Protection). Solo compatible con Windows 10.

## <a name="custom"></a>Personalizada
La configuración personalizada le permite asignar valores de configuración del dispositivo que no están integrados en Intune. Por ejemplo, en dispositivos Android, puede especificar valores de OMA-URI que configuran el dispositivo. Para dispositivos iOS, puede importar un archivo de configuración creado Apple Configurator.
Para más información, consulte [How to configure custom settings](how-to-configure-custom-settings.md) (Configuración personalizada). Compatible con Android, iOS, macOS y Windows Phone 8.1.



<!--HONumber=Feb17_HO1-->

