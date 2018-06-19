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
ms.openlocfilehash: 7d0e4710c74c12bf62cd19df6a053aea9ac35eaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348454"
---
# <a name="message-categories"></a>Categorías de mensaje
¿Qué tipos de mensajes puede escribir controladores para hay tres categorías principales:  
  
1.  mensajes de Windows  
  
     Esto incluye principalmente aquellos mensajes que empiezan con la **WM_** prefijo, excepto para **WM_COMMAND**. Mensajes de Windows se controlan mediante ventanas y vistas. Estos mensajes suelen tengan parámetros que se usan para determinar cómo controlar el mensaje.  
  
2.  Notificaciones del control  
  
     Esto incluye **WM_COMMAND** mensajes de notificación de controles y otras ventanas secundarias a sus ventanas primarias. Por ejemplo, un control de edición envía su elemento primario un **WM_COMMAND** de mensaje que contenga el **EN_CHANGE** código de notificación de controles cuando el usuario ha realizado una acción que puede haber modificado el texto del control de edición. Controlador de la ventana para el mensaje responde al mensaje de notificación de manera adecuada, por ejemplo, recupera el texto del control.  
  
     El marco de trabajo enruta los mensajes de notificación de controles como otro **WM_** mensajes. Sin embargo, es una excepción, el **BN_CLICKED** mensaje de notificación de controles enviado por los botones cuando el usuario hace clic en ellos. Este mensaje se tratan de manera especial como un mensaje de comando y se enrute al igual que otros comandos.  
  
3.  Mensajes de comando  
  
     Esto incluye **WM_COMMAND** mensajes de notificación de objetos de interfaz de usuario: menús, botones de barra de herramientas y teclas de aceleración. El marco de trabajo procesa los comandos de manera diferente a otros mensajes, y puede controlarse mediante varios tipos de objetos, como se explica en [destinos de comando](../mfc/command-targets.md).  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Mensajes de Windows y los mensajes de notificación de controles  
 Mensajes de las categorías 1 y 2: mensajes de Windows y notificaciones de control, se controlan mediante windows: objetos de clases derivadas de la clase `CWnd`. Esto incluye `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, y sus propias clases derivadas de estas clases base. Estos objetos encapsulan un `HWND`, un identificador de una ventana de Windows.  
  
##  <a name="_core_command_messages"></a> Mensajes de comando  
 Mensajes de la categoría 3, comandos, pueden controlarse mediante una gran variedad de objetos: documentos, plantillas de documento y el propio objeto de aplicación además de ventanas y vistas. Cuando un comando afecta directamente a algún objeto en particular, tiene sentido hacer que ese objeto controlar el comando. Por ejemplo, el comando Abrir en el menú archivo está asociado lógicamente con la aplicación: la aplicación abre un documento específico tras recibir el comando. Por lo tanto, el controlador para el comando Abrir es una función miembro de la clase de aplicación. Para obtener más información sobre comandos y cómo se enrutan a objetos, consulte [cómo el marco de trabajo llama a un controlador](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

