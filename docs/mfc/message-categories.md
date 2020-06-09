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
ms.openlocfilehash: 3875a6931b4380f0531e4c1786de6dddfccb76ca
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625468"
---
# <a name="message-categories"></a>Categorías de mensaje

En qué tipos de mensajes se escriben Controladores para hay tres categorías principales:

1. mensajes de Windows

   Esto incluye principalmente los mensajes que comienzan con el prefijo **WM_** , excepto WM_COMMAND. Windows y las vistas controlan los mensajes de Windows. Estos mensajes suelen tener parámetros que se usan para determinar cómo administrar el mensaje.

1. Notificaciones del control

   Esto incluye WM_COMMAND mensajes de notificación de los controles y otras ventanas secundarias a sus ventanas principales. Por ejemplo, un control de edición envía a su elemento primario un mensaje WM_COMMAND que contiene el código de notificación de control EN_CHANGE cuando el usuario ha realizado una acción que puede haber alterado el texto en el control de edición. El controlador de la ventana para el mensaje responde al mensaje de notificación de alguna manera adecuada, como recuperar el texto del control.

   El marco de trabajo enruta los mensajes de notificación de control como otros mensajes de **WM_** . Sin embargo, una excepción es el mensaje de notificación de control BN_CLICKED que envían los botones cuando el usuario hace clic en ellos. Este mensaje se trata especialmente como un mensaje de comando y se enruta como otros comandos.

1. Mensajes de comandos

   Esto incluye WM_COMMAND mensajes de notificación de objetos de la interfaz de usuario: menús, botones de barra de herramientas y teclas de aceleración. El marco de trabajo procesa los comandos de forma diferente a otros mensajes y los puede controlar más tipos de objetos, como se explica en [destinos de comandos](command-targets.md).

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Mensajes de Windows y mensajes de notificación de control

Windows controla los mensajes de las categorías 1 y 2 (mensajes de Windows y notificaciones de control): objetos de clases derivadas de la clase `CWnd` . Esto incluye `CFrameWnd` , `CMDIFrameWnd` , `CMDIChildWnd` , `CView` , `CDialog` y sus propias clases derivadas de estas clases base. Estos objetos encapsulan un `HWND` , un identificador de una ventana de Windows.

## <a name="command-messages"></a><a name="_core_command_messages"></a>Mensajes de comandos

Los mensajes de categoría 3: comandos: se pueden controlar mediante una variedad más amplia de objetos: documentos, plantillas de documento y el propio objeto de aplicación además de ventanas y vistas. Cuando un comando afecta directamente a algún objeto determinado, tiene sentido hacer que ese objeto controle el comando. Por ejemplo, el comando abrir del menú archivo está asociado lógicamente a la aplicación: la aplicación abre un documento especificado al recibir el comando. Por lo tanto, el controlador del comando Open es una función miembro de la clase Application. Para obtener más información sobre los comandos y cómo se enrutan a los objetos, vea [cómo el marco llama a un controlador](how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Consulte también

[Mensajes y comandos en el marco](messages-and-commands-in-the-framework.md)
