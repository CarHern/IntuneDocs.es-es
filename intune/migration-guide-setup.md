---
title: Configuración básica de Microsoft Intune
description: En este artículo se indican los pasos necesarios para configurar Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 4cec5c593fd4191a9d73e77b13fd38df81a7fe8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179752"
---
# <a name="basic-setup"></a>Configuración básica

Después de evaluar el entorno, ha llegado la hora de configurar Microsoft Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dependencias externas para una implementación de Intune

### <a name="identity"></a>Identidad

Intune exige Azure Active Directory (AAD) como proveedor de agrupaciones de identidades y de usuarios. Más información acerca de:

-  [¿Requisitos de identidad?](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

-   [Requisitos de sincronización de directorios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

-   [Requisitos de la autenticación multifactor (MFA)](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)

-   [Planeación de grupos de usuarios y dispositivos](users-add.md)

-   [Creación de grupos de usuarios y dispositivos](groups-get-started.md)

Si su organización ya usa Office 365, Intune debe usar el mismo entorno de Azure Active Directory.

### <a name="pki-optional"></a>PKI (opcional)

Si piensa usar autenticación basada en certificados para perfiles de VPN, Wi-Fi o correo electrónico con Intune, tendrá que asegurarse de que tiene una [infraestructura PKI específica](certificates-configure.md) lista para crear e implementar perfiles de certificado. Obtenga más información sobre la configuración de certificados en Intune:

-   [Cómo configurar la infraestructura de certificados para SCEP](/intune/certificates-scep-configure).

-   [Cómo configurar la infraestructura de certificados para PFX](/intune/certficates-pfx-configure).


## <a name="task-list-for-an-intune-setup"></a>Lista de tareas para una configuración de Intune

### <a name="task-1-intune-subscription"></a>Tarea 1: Suscripción a Intune

Para poder migrar a Intune, necesita primero una suscripción a Intune.

-   Puede visitar [esta página](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0), que le ofrece instrucciones sobre cómo:

    -   Crear una suscripción a Intune vinculada a un nuevo inquilino de AAD.

    -   Vincular la suscripción a Intune iniciando sesión en un inquilino existente de AAD.

### <a name="task-2-assign-intune-user-licenses"></a>Tarea 2: asignar licencias de usuario de Intune

-   Aprenda a [asignar licencias de usuario de Intune](licenses-assign.md).

-   Si ha creado un inquilino de Azure Active Directory, aprenda a [crear otros usuarios o a sincronizar un usuario desde su Active Directory (AD) local.](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Tarea 3: Establecer Intune como entidad de MDM

Intune puede administrarse mediante el portal de Azure o la consola de la rama actual de Configuration Manager. Salvo que tenga que integrar Intune con una implementación de la rama actual de Configuration Manager, le recomendamos que administre Intune desde [Azure Portal](https://portal.azure.com).

Establezca **Intune** como entidad de MDM para habilitar el portal de Intune Azure. El uso de otra entidad de MDM permite a Intune transferir la administración de MDM a consolas de administración de Microsoft alternativas. Estos casos no son frecuentes.

> [!IMPORTANT]
> Si va a transferir la administración de dispositivos móviles a Intune por primera vez, debe establecer Intune como entidad de MDM.

Aprenda a [establecer la entidad de administración de dispositivos móviles](mdm-authority-set.md).

## <a name="next-step"></a>Paso siguiente

Configure las [directivas de administración de dispositivos y aplicaciones](migration-guide-configure-policies.md).
