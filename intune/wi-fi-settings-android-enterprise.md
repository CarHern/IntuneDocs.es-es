---
title: Configuración de Wi-Fi para dispositivos Android Enterprise y de pantalla completa
titleSuffix: Microsoft Intune
description: Cree o agregue un perfil de configuración de dispositivos Wi-Fi para Android Enterprise y el Quiosco de Android. Vea las diferentes configuraciones, como la adición de certificados, la elección de un tipo EAP y la selección de un método de autenticación en Microsoft Intune. Para dispositivos del quiosco, escriba también la clave precompartida de la red.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 1424cd43c6ccde17724a4165fe74def4da291e29
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112364"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>Incorporación de la configuración de Wi-Fi en Microsoft Intune para dispositivos que ejecutan Android Enterprise y el Quiosco de Android

Puede crear un perfil con una configuración específica de Wi-Fi y después implementar este perfil en los dispositivos Android Enterprise y del Quiosco de Android. Microsoft Intune ofrece muchas características, incluidas la autenticación en la red, con el uso de una clave precompartida, y mucho más.

Ambas se describen en este artículo.

## <a name="before-you-begin"></a>Antes de comenzar

[Creación de un perfil de dispositivo en Microsoft Intune](device-profile-create.md).

## <a name="device-owner-only---kiosk"></a>Solo el propietario del dispositivo: quiosco

Seleccione esta opción si usa un dispositivo Android Enterprise como un quiosco.

- **Nombre de red**: escriba un nombre para esta conexión Wi-Fi. Este valor es el nombre que ven los usuarios cuando exploran la lista de conexiones disponibles en sus dispositivos.
- **SSID**: abreviatura de **identificador de conjunto de servicios**. Esta configuración es el nombre real de la red inalámbrica a la que se conectan los dispositivos. Sin embargo, los usuarios solo ven el **nombre de red** que ha configurado al elegir la conexión.
- **Conectar automáticamente**: elija **Habilitar** para conectarse automáticamente a esta red cuando el dispositivo está en el intervalo. Elija **Deshabilitar** para impedir que los dispositivos se conecten automáticamente.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.
- **Tipo de Wi-Fi**: seleccione el protocolo de seguridad para autenticarse en la red Wi-Fi. Las opciones son:

  - **Abierta (sin autenticación)**: use esta opción solo si la red no es segura.
  - **Clave precompartida por WEP**: escriba la contraseña en **Clave precompartida**. Una vez configurada la red de su organización, también se configuran una contraseña o una clave de red. Escriba esta contraseña o clave de red para el valor PSK.
  - **Clave precompartida por WPA**: escriba la contraseña en **Clave precompartida**. Una vez configurada la red de su organización, también se configuran una contraseña o una clave de red. Escriba esta contraseña o clave de red para el valor PSK.

Haga clic en **Aceptar** para guardar los cambios.

## <a name="work-profile-only"></a>Solo perfil de trabajo

### <a name="basic-settings"></a>Configuración básica

- **Tipo de Wi-Fi**: Elija **Básica**.
- **SSID**: abreviatura de **identificador de conjunto de servicios**. Esta configuración es el nombre real de la red inalámbrica a la que se conectan los dispositivos.
- **Conectar automáticamente**: elija **Habilitar** para conectarse automáticamente a esta red cuando el dispositivo está en el intervalo. Elija **Deshabilitar** para impedir que los dispositivos se conecten automáticamente.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.

## <a name="enterprise-profile"></a>Perfil de empresa

- **Tipo de Wi-Fi**: elija **Empresa**.
- **SSID**: abreviatura de **identificador de conjunto de servicios**. Esta configuración es el nombre real de la red inalámbrica a la que se conectan los dispositivos.
- **Conectar automáticamente**: elija **Habilitar** para conectarse automáticamente a esta red cuando el dispositivo está en el intervalo. Elija **Deshabilitar** para impedir que los dispositivos se conecten automáticamente.
- **Red oculta**: elija **Habilitar** para ocultar esta red en la lista de redes disponibles en el dispositivo. No se difunde el SSID. Elija **Deshabilitar** para mostrar esta red en la lista de redes disponibles en el dispositivo.
- **Tipo de EAP**: elija el tipo Protocolo de autenticación extensible (EAP) que se usa para autenticar conexiones inalámbricas seguras. Las opciones son: 

  - **EAP-TLS**: Indique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija un perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente** - **Certificado cliente para la autenticación del cliente (certificado de identidad)**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

  - **EAP-TTLS**: Indique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija un perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método que no es EAP (identidad interna)**: elija cómo autenticar la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi.

          Las opciones son: **Contraseña no cifrada (PAP)**, **Protocolo de autenticación por desafío mutuo (CHAP)**, **Microsoft CHAP (MS-CHAP)** o **Microsoft CHAP versión 2 (MS-CHAP v2)**

      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

        Haga clic en **Aceptar** para guardar los cambios.

      - **Privacidad de identidad (identidad externa)**: escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

  - **PEAP**: Indique también:

    - **Confianza del servidor** - **Certificado raíz para validación del servidor**: elija un perfil de certificado raíz de confianza existente. Este certificado se presenta al servidor cuando el cliente se conecta a la red y se usa para autenticar la conexión.

      Haga clic en **Aceptar** para guardar los cambios.

    - **Autenticación de cliente**: elija un **método de autenticación**. Las opciones son:

      - **Nombre de usuario y contraseña**: pida al usuario un nombre de usuario y una contraseña para autenticar la conexión. Indique también:
        - **Método no EAP para la autenticación (identidad interna)**: elija cómo autenticar la conexión. Asegúrese de elegir el mismo protocolo que está configurado en su red Wi-Fi.

          Las opciones son: **Ninguno** o **Microsoft CHAP versión 2 (MS-CHAP v2)**

      - **Certificados**: elija el perfil de certificado de cliente SCEP o PKCS que también se implementa en el dispositivo. Este certificado es la identidad presentada por el dispositivo al servidor para autenticar la conexión.

        Haga clic en **Aceptar** para guardar los cambios.

      - **Privacidad de identidad (identidad externa)**: escriba el texto que se envía como respuesta a una solicitud de identidad EAP. Este texto puede ser cualquier valor, como `anonymous`. Durante la autenticación, esta identidad anónima se envía inicialmente, seguida de la identificación real enviada en un túnel seguro.

Seleccione **Aceptar** > **Crear** para guardar los cambios. El perfil se crea y se muestra en la lista de perfiles.

## <a name="next-steps"></a>Pasos siguientes

Se crea el perfil, pero no hacen nada. A continuación, [asigne este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Más recursos

- Vea las opciones disponibles para dispositivos Android en [Configuración de Wi-Fi para dispositivos que ejecutan Android](wi-fi-settings-android.md).
- [Introducción a la configuración de Wi-Fi](wi-fi-settings-configure.md), incluidas otras plataformas.