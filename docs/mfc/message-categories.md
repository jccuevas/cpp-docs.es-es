---
title: Categorías de mensajes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 051fe93ef689959b0a0beb2b1b0f213adc942446
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929652"
---
# <a name="message-categories"></a>Categorías de mensaje
¿Qué tipos de mensajes puede escribir controladores para hay tres categorías principales:  
  
1.  mensajes de Windows  
  
     Esto incluye principalmente aquellos mensajes que empiezan con la **WM_** prefijo, excepto WM_COMMAND. Mensajes de Windows se controlan mediante ventanas y vistas. Estos mensajes suelen tengan parámetros que se usan para determinar cómo controlar el mensaje.  
  
2.  Notificaciones del control  
  
     Esto incluye mensajes de notificación WM_COMMAND de controles y otras ventanas secundarias a sus ventanas primarias. Por ejemplo, un control de edición envía a su elemento primario un mensaje WM_COMMAND que contiene el código de notificación del control EN_CHANGE cuando el usuario ha realizado una acción que puede haber modificado el texto del control de edición. Controlador de la ventana para el mensaje responde al mensaje de notificación de manera adecuada, por ejemplo, recupera el texto del control.  
  
     El marco de trabajo enruta los mensajes de notificación de controles como otro **WM_** mensajes. Una excepción, sin embargo, es el mensaje de notificación de control BN_CLICKED enviado por los botones cuando el usuario hace clic en ellos. Este mensaje se tratan de manera especial como un mensaje de comando y se enrute al igual que otros comandos.  
  
3.  Mensajes de comando  
  
     Esto incluye mensajes de notificación WM_COMMAND de objetos de interfaz de usuario: menús, botones de barra de herramientas y teclas de aceleración. El marco de trabajo procesa los comandos de manera diferente a otros mensajes, y puede controlarse mediante varios tipos de objetos, como se explica en [destinos de comando](../mfc/command-targets.md).  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Mensajes de Windows y los mensajes de notificación de controles  
 Mensajes de las categorías 1 y 2: mensajes de Windows y notificaciones de control, se controlan mediante windows: objetos de clases derivadas de la clase `CWnd`. Esto incluye `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, y sus propias clases derivadas de estas clases base. Estos objetos encapsulan un `HWND`, un identificador de una ventana de Windows.  
  
##  <a name="_core_command_messages"></a> Mensajes de comando  
 Mensajes de la categoría 3, comandos, pueden controlarse mediante una gran variedad de objetos: documentos, plantillas de documento y el propio objeto de aplicación además de ventanas y vistas. Cuando un comando afecta directamente a algún objeto en particular, tiene sentido hacer que ese objeto controlar el comando. Por ejemplo, el comando Abrir en el menú archivo está asociado lógicamente con la aplicación: la aplicación abre un documento específico tras recibir el comando. Por lo tanto, el controlador para el comando Abrir es una función miembro de la clase de aplicación. Para obtener más información sobre comandos y cómo se enrutan a objetos, consulte [cómo el marco de trabajo llama a un controlador](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

