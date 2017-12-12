---
title: "Aplicación de directivas de cumplimiento en los dispositivos administrados por Jamf"
titlesuffix: Azure portal
description: Use el cumplimiento para ayudar a proteger los dispositivos administrados por Jamf.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6184552ce901ffc062f0453f169ec992049ae69b
ms.sourcegitcommit: 82088d297eef629e3da6011681ead442ae7e25f7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2017
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Aplicación del cumplimiento en equipos Mac administrados con Jamf Pro

|Se aplica a: Intune en Azure Portal |
|--|
|¿Busca información sobre Intune en el portal clásico? [Vaya aquí](/intune/introduction-intune?toc=/intune-classic/toc.json).|
| |

|Actualmente en versión preliminar privada|
|--|
|Las características que se describen en este tema solo están disponibles para los clientes que dispongan actualmente de la versión preliminar privada. Este mensaje se eliminará cuando se haya publicado para todos los clientes.|
| |

Puede usar Azure Active Directory y las directivas de acceso condicional de Microsoft Intune garantizan que los usuarios finales son compatibles con los requisitos de la organización. Puede aplicar estas directivas en los equipos Mac que se [administran con Jamf Pro](conditional-access-integrate-jamf.md). Esto requiere acceso tanto a la consola de Intune como a la consola de Jamf Pro.

## <a name="set-up-device-compliance-policies-in-intune"></a>Configuración de las directivas de cumplimiento de dispositivos en Intune

1. Abra Microsoft Azure y, luego, navegue a **Intune** > **Cumplimiento de dispositivos** > **Directivas**. Puede crear directivas para macOS, incluida la elección de una serie de acciones (por ejemplo, el envío de correos electrónicos de advertencia) a usuarios y grupos no compatibles.
2. Busque los grupos deseados y, luego, aplíqueles las directivas.

## <a name="require-the-company-portal-app-for-macos"></a>Requerir la aplicación Portal de empresa para macOS

1. En un dispositivo macOS, vaya a https://aka.ms/macoscompanyportal para descargar la versión actual de la aplicación Portal de empresa para macOS.
2. Abra Jamf Pro y navegue a **Administración de equipos** > **Paquetes**.
3. Cree un paquete con la aplicación Portal de empresa para macOS y, luego, haga clic en **Guardar**.
4. Abra **Equipos** > **Directivas** y seleccione **Nuevo**.
5. Use la carga **General** para configurar los valores de la directiva, incluida la frecuencia de desencadenador y ejecución.
6. Seleccione la carga **Paquetes** y haga clic en **Configurar**.
7. Haga clic en **Agregar** para seleccionar el paquete con la aplicación Portal de empresa.
8. Elija **Instalar** en el menú desplegable **Acción**.
9. Configure los valores del paquete.
10. Haga clic en la pestaña **Ámbito** para especificar en qué equipos se debe instalar la aplicación Portal de empresa. Haga clic en **Guardar**. La directiva ejecutará dispositivos con ámbito la próxima vez que el desencadenador seleccionado se produzca en el equipo y cumpla con los criterios establecidos en la carga **General**.

## <a name="direct-your-users-to-register-jamf-pro-managed-devices-with-azure-active-directory"></a>Dirija a los usuarios al registro de los dispositivos administrados por Jamf Pro con Azure Active Directory

> [!NOTE]
> Debe [implementar Portal de empresa](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos) para macOS antes de pasar por los pasos siguientes.  

Los usuarios finales deben iniciar la aplicación Portal de empresa a través del autoservicio de Jamf para registrar el dispositivo con Azure AD como un dispositivo administrado por Jamf Pro.

1. En Jamf Pro, navegue a **Equipos** > **Directivas** y cree una directiva nueva para el registro de dispositivos.
2. Configure la carga **Acceso condicional**, incluida la frecuencia de desencadenador y ejecución. Establezca la prioridad en **Después**.
3. Haga clic en la pestaña **Ámbito** y establezca el ámbito de la directiva en todos los dispositivos de destino.
4. Haga clic en la pestaña **Autoservicio** para hacer que la directiva esté disponible en el autoservicio de Jamf. Incluya la directiva en la categoría **Cumplimiento de dispositivos**. Haga clic en **Guardar**.