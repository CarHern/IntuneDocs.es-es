---
title: Solicitar y proporcionar asistencia remota para PC de Windows | Microsoft Intune
description: "Describe los pasos de administración de TI y usuario final para proporcionar asistencia remota para PC de Windows e iniciar un PC de forma remota."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: ab954204fffa6ad67a4a0d0f5e2e521c795eae31


---

# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>Solicitar y proporcionar asistencia remota para equipos con Windows

Microsoft Intune puede usar el software [TeamViewer](https://www.teamviewer.com), comprado por separado, para que usted pueda ofrecer asistencia remota a los usuarios que estén ejecutando el cliente de software de Intune. Cuando un usuario solicita ayuda a Microsoft Intune Center, usted recibe una alerta, puede aceptar la solicitud y, luego, proporcionar asistencia. Esta funcionalidad reemplaza la funcionalidad de asistencia remota de Windows existente en Intune.


## <a name="before-you-start"></a>Antes de empezar

Antes de empezar a establecer las solicitudes de asistencia remota y responderlas, asegúrese de haber cumplido los requisitos previos siguientes:

- Debe haber [registrado una cuenta de TeamViewer](https://login.teamviewer.com/LogOn#register) para iniciar sesión en el sitio web de TeamViewer.
- Debe administrar los equipos Windows mediante [el cliente de equipos Windows](manage-windows-pcs-with-microsoft-intune.md)
- Se pueden administrar todos los sistemas operativos de equipos Windows que Intune admite.

## <a name="configure-the-teamviewer-connector"></a>Configurar el conector de TeamViewer

1. En la [consola de administración de Microsoft Intune](https://manage.microsoft.com), seleccione **Administración**.
2. En el área de trabajo **Administración**, elija **TeamViewer**.
3. En la página **TeamViewer**, en **Conector de TeamViewer**, elija **Habilitar**.
4. En el cuadro de diálogo **Habilitar TeamViewer**, lea los términos de licencia y, después, haga clic en **Aceptar**. Si aún no tiene una licencia de TeamViewer, elija **Comprar una licencia de TeamViewer**.
5. Una vez abierta la ventana del explorador de TeamViewer, inicie sesión en el sitio con sus credenciales de TeamViewer.
6. En el sitio de TeamViewer, lea y acepte las opciones para permitir que Intune se conecte con TeamViewer.
7. En la consola de Intune, compruebe que el elemento **Conector de TeamViewer** aparece como **Habilitado**.


## <a name="open-a-remote-assistance-request-end-user"></a>Abrir una solicitud de asistencia remota (usuario final)

1. En un equipo Windows de cliente, abra **Microsoft Intune Center**.
2. En **Asistencia remota**, elija **Solicitar asistencia remota**.
3. Después de aprobar la solicitud (ver abajo), TeamViewer se abre en el cliente. El usuario debe aceptar los mensajes en los que se indique que el explorador web está intentando abrir la aplicación TeamViewer.
4. El usuario ve un mensaje en el que se le pregunta si usted puede controlar el equipo de dicho usuario. Él debe aceptar este mensaje para continuar.
5. Durante la sesión de asistencia remota, el usuario ve una ventana que muestra que usted está conectado. Si el usuario cierra esta ventana, la sesión remota finaliza.

## <a name="respond-to-a-remote-assistance-request"></a>Responder a una solicitud de asistencia remota

1. Cuando un usuario envía una solicitud de asistencia remota, usted puede verlo en el área de trabajo **Alertas**, en **Supervisión** > **Asistencia remota**. Por ejemplo:
> ![Captura de pantalla de una solicitud de asistencia remota](./media/team-viewer.png)

<br>Si no contesta a una solicitud pasadas 4 horas, se quita.
2. Para aceptar la solicitud, elija **Aprobar solicitud e iniciar asistencia remota**.
3. En el cuadro de diálogo **Hay una nueva solicitud de asistencia remota pendiente**, elija **Aceptar la solicitud de asistencia remota**. Si aún no están instaladas, TeamViewer instalará las aplicaciones necesarias en el equipo.
4. Después, TeamViewer notifica al usuario final que usted quiere tomar el control de su equipo. Después de que el usuario ha aceptado la solicitud, la ventana de TeamViewer se abre y usted puede controlar el equipo.

Durante una sesión de asistencia remota, puede usar todos los comandos de TeamViewer disponibles para controlar el equipo remoto. Para obtener ayuda con estos comandos, descargue el [Manual de control remoto](http://www.teamviewer.com/en/support/documents/) desde el sitio web de TeamViewer.

## <a name="close-the-remote-assistance-session"></a>Cerrar la sesión de asistencia remota

En el menú **Acciones** de la ventana **TeamViewer**, elija **Finalizar sesión**.

## <a name="remotely-restart-a-windows-pc"></a>Reiniciar un PC Windows de forma remota
Cuando ayuda a los usuarios con problemas, debe reiniciar su PC de forma remota de vez en cuando. Utilice los pasos siguientes para reiniciar de forma remota un PC de Windows.

1.  En la [consola de administración de Microsoft Intune](https://manage.microsoft.com/), seleccione **Grupos** &gt; **Todos los dispositivos** (u otro grupo que contenga el equipo que quiera reiniciar).

2.  Seleccione uno o más equipos y, después, seleccione **Tareas remotas** &gt; **Reiniciar el equipo**.

3.  Para ver el estado de la tarea, seleccione **Tareas remotas** en la esquina inferior derecha de la página.

4.  En el cuadro de diálogo **Estado de la tarea** , revise las tareas remotas actuales, el estado de la tarea, el nombre del dispositivo y los errores notificados.

### <a name="see-also"></a>Consulte también

[Tareas comunes de administración de equipos Windows con el cliente de software de Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->

