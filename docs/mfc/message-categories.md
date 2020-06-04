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
ms.openlocfilehash: 686d5eef4aaa67785aa56133d820b637fbf4bb86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364755"
---
# <a name="message-categories"></a>Categorías de mensaje

¿Qué tipos de mensajes se escriben controladores para Hay tres categorías principales:

1. mensajes de Windows

   Esto incluye principalmente los mensajes que comienzan con el prefijo **WM_,** excepto los WM_COMMAND. Los mensajes de Windows se controlan mediante ventanas y vistas. Estos mensajes a menudo tienen parámetros que se utilizan para determinar cómo controlar el mensaje.

1. Notificaciones del control

   Esto incluye WM_COMMAND mensajes de notificación de controles y otras ventanas secundarias a sus ventanas primarias. Por ejemplo, un control de edición envía a su elemento primario un mensaje de WM_COMMAND que contiene el código de notificación de control EN_CHANGE cuando el usuario ha realizado una acción que puede haber modificado el texto en el control de edición. El controlador de la ventana para el mensaje responde al mensaje de notificación de alguna manera adecuada, como recuperar el texto en el control.

   El marco de trabajo enruta los mensajes de notificación de control como otros mensajes **WM_.** Una excepción, sin embargo, es el BN_CLICKED mensaje de notificación de control enviado por botones cuando el usuario hace clic en ellos. Este mensaje se trata especialmente como un mensaje de comando y se enruta como otros comandos.

1. Mensajes de comando

   Esto incluye WM_COMMAND mensajes de notificación de objetos de interfaz de usuario: menús, botones de barra de herramientas y teclas de aceleración. El marco de trabajo procesa los comandos de forma diferente a otros mensajes y se pueden controlar mediante más tipos de objetos, como se explica en Destinos de [comando](../mfc/command-targets.md).

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Mensajes de Windows y mensajes de control-notificación

Los mensajes de las categorías 1 y 2 — Mensajes de Windows y notificaciones de control — se controlan mediante windows: objetos de clases derivadas de la clase `CWnd`. Esto `CFrameWnd`incluye `CMDIFrameWnd` `CMDIChildWnd`, `CView` `CDialog`, , , , y sus propias clases derivadas de estas clases base. Estos objetos `HWND`encapsulan un identificador , un identificador de una ventana de Windows.

## <a name="command-messages"></a><a name="_core_command_messages"></a>Mensajes de comando

Los mensajes de la categoría 3 — comandos — pueden ser manejados por una variedad más amplia de objetos: documentos, plantillas de documento y el propio objeto de aplicación, además de ventanas y vistas. Cuando un comando afecta directamente a algún objeto en particular, tiene sentido que ese objeto controle el comando. Por ejemplo, el comando Abrir del menú Archivo está asociado lógicamente a la aplicación: la aplicación abre un documento especificado al recibir el comando. Por lo tanto, el controlador del comando Open es una función miembro de la clase de aplicación. Para obtener más información sobre los comandos y cómo se enrutan a objetos, vea Cómo el marco de trabajo [llama a un controlador](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Consulte también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)
