---
title: Categorías de mensaje
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: e8b7385a233c2074fe9bfc491d89de7629c730c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50619861"
---
# <a name="message-categories"></a>Categorías de mensaje

¿Qué tipos de mensajes al escribir controladores para tres categorías principales:

1. mensajes de Windows

   Esto incluye principalmente aquellos mensajes que empiezan con el **WM_** prefijo, excepto WM_COMMAND. Mensajes de Windows se controlan mediante ventanas y vistas. Estos mensajes suelen tengan los parámetros que se usan para determinar cómo tratar el mensaje.

1. Notificaciones del control

   Esto incluye los mensajes de notificación WM_COMMAND de controles y otras ventanas secundarias a sus ventanas primarias. Por ejemplo, un control de edición envía a su elemento primario de un mensaje WM_COMMAND, que contiene el código de notificación de control EN_CHANGE cuando el usuario ha realizado una acción que puede haber modificado el texto del control de edición. Controlador de la ventana para el mensaje responde al mensaje de notificación de alguna manera adecuada, como recuperar el texto del control.

   El marco de trabajo enruta los mensajes de notificación de control como otro **WM_** mensajes. Una excepción, sin embargo, es el mensaje de notificación de control BN_CLICKED enviado por los botones cuando el usuario hace clic en ellos. Este mensaje se tratan de manera especial como un mensaje de comando y se enruta al igual que otros comandos.

1. Mensajes de comandos

   Esto incluye mensajes de notificación de WM_COMMAND de objetos de la interfaz de usuario: menús, botones de barra de herramientas y teclas de aceleración. El marco de trabajo procesa los comandos de manera diferente a otros mensajes, y puede controlarse mediante más tipos de objetos, como se explica en [destinos de comando](../mfc/command-targets.md).

##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Mensajes de Windows y los mensajes de notificación de Control

Los mensajes de las categorías 1 y 2, los mensajes de Windows y notificaciones de control, se controlan mediante windows: objetos de clases derivadas de la clase `CWnd`. Esto incluye `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, y sus propias clases derivan de estas clases base. Estos objetos encapsulan un `HWND`, un identificador de una ventana de Windows.

##  <a name="_core_command_messages"></a> Mensajes de comandos

Los mensajes de la categoría 3, comandos, puede controlarse mediante una amplia variedad de objetos: documentos, plantillas de documento y el objeto de aplicación además de ventanas y vistas. Cuando un comando afecta directamente a algún objeto en particular, tiene sentido tener ese objeto de controlar el comando. Por ejemplo, el comando Abrir en el menú archivo está asociado lógicamente a la aplicación: la aplicación abre un documento al recibir el comando especificado. Por lo tanto, el controlador para el comando Abrir es una función miembro de la clase de aplicación. Para obtener más información sobre los comandos y cómo se enrutan a los objetos, consulte [cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Vea también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

