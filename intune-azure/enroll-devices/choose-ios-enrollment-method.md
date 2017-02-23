---
title: "Elegir cómo inscribir dispositivos iOS en Intune | Versión preliminar de Intune Azure | Documentos de Microsoft"
description: "Versión preliminar de Intune Azure: aprenda a configurar la inscripción de dispositivos iOS en Microsoft Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: c228601451b33238d0f6929987dcdec3a5e56e8d


---

# <a name="choose-how-to-enroll-ios-devices"></a>Elegir cómo inscribir dispositivos iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

En este tema se describen los métodos que puede usar para inscribir dispositivos iOS y los requisitos previos para la inscripción.

Use la siguiente información para decidir qué método usar para inscribir dispositivos iOS. Todos los métodos siguientes, excepto BYOD, son para la inscripción de dispositivos corporativos.

**Requisito previo:** se requiere un [certificado de Apple Push Notification Service](get-an-apple-mdm-push-certificate.md).

## <a name="user-owned-ios-devices-byod"></a>Dispositivos iOS corporativos (BYOD)

Si los usuarios quieren inscribir sus dispositivos personales, BYOD (traiga su propio dispositivo), el único método de inscripción disponible es que descarguen la aplicación Portal de empresa para iOS desde la App Store y sigan las instrucciones de inscripción de la aplicación. Una vez inscritos, los usuarios pueden conectarse a la red de empresa, unirse al dominio o a Azure Active Directory y obtener acceso a los recursos corporativos.

## <a name="apple-configurator"></a>Apple Configurator

Puede inscribir dispositivos iOS mediante la exportación de un perfil de inscripción corporativo y, luego, la conexión de esos dispositivos móviles a un equipo Mac que ejecuta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017). Apple Configurator admite dos formas de inscripción:

- **Inscripción con el Asistente de configuración**: restablece la configuración de fábrica del dispositivo y lo prepara para que el nuevo usuario del dispositivo lo configure. En este método, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute Apple Configurator para preconfigurar la inscripción. Después, los dispositivos se entregan a los usuarios, que ejecutan el proceso del Asistente de configuración. Este proceso configura el dispositivo con las credenciales profesionales o educativas de los usuarios y completa el proceso de inscripción. Para más información, consulte [Inscripción de dispositivos iOS con Apple Configurator y el Asistente de configuración](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md).

- **Inscripción directa**: crea un archivo compatible con Apple Configurator para su uso durante la preparación del dispositivo. No se restablece la configuración de fábrica del dispositivo inscrito, y no está asociado a ningún usuario. Para inscribir dispositivos, el administrador debe conectar el dispositivo iOS mediante USB a un equipo Mac que ejecute Apple Configurator. Para obtener más información, consulte [Inscribir directamente dispositivos iOS mediante Apple Configurator](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md).

## <a name="use-the-device-enrollment-program-dep"></a>Usar el Programa de inscripción de dispositivos (DEP)

DEP implementa un perfil de inscripción "de forma inalámbrica" en los dispositivos que se adquieren a través de DEP. Cuando un usuario ejecuta el Asistente de configuración en el dispositivo, el dispositivo se inscribe en Intune. Los usuarios no pueden anular la inscripción de dispositivos inscritos a través de DEP. Para más información, consulte [Inscripción de dispositivos iOS mediante el Programa de inscripción de dispositivos](enroll-ios-devices-using-device-enrollment-program.md).

## <a name="use-the-device-enrollment-manager-dem"></a>Uso del administrador de inscripción de dispositivos (DEM)
El administrador de inscripción de dispositivos es un tipo de cuenta de usuario que puede inscribir y administrar hasta 1000 dispositivos. Agregue usuarios existentes a la cuenta de DEM para proporcionarles estas funcionalidades. En cada dispositivo que el usuario de DEM inscribe usa una sola licencia de Intune. Para más información, consulte [Inscripción de dispositivos con el administrador de inscripción de dispositivos](enroll-devices-using-device-enrollment-manager.md).



<!--HONumber=Feb17_HO1-->

