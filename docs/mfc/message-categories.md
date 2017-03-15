---
title: "Categor&#237;as de mensaje | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mensajes de comandos [C++]"
  - "mensajes de notificación de controles"
  - "controles [MFC], notificaciones"
  - "control de mensajes [C++], tipo de mensaje"
  - "mensajes [C++], categorías"
  - "mensajes [C++], Windows"
  - "mensajes de Windows [C++], categorías"
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Categor&#237;as de mensaje
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

¿Para qué tipo de mensajes escribe controladores?  Hay tres categorías principales:  
  
1.  Mensajes de Windows  
  
     Esto incluye principalmente esos mensajes a partir del prefijo de **WM\_** , a excepción de **WM\_COMMAND**.  Los mensajes de Windows se administran mediante las ventanas y las vistas.  Estos mensajes tienen a menudo parámetros que se utilizan para determinar cómo procesar el mensaje.  
  
2.  Notificaciones del control  
  
     Esto incluye los mensajes de notificación de **WM\_COMMAND** de controles y otras ventanas secundarias a sus ventanas primarias.  Por ejemplo, un control de edición envía su elemento primario un mensaje de **WM\_COMMAND** que contiene el código de la CONTROL\- notificación de **EN\_CHANGE** cuando el usuario ha realizado una acción que podrían haber modificado el texto del control de edición.  El controlador de la ventana para el mensaje responde al mensaje de notificación de alguna manera adecuada, como recuperar el texto del control.  
  
     El marco enruta mensajes de la CONTROL\- notificación como otros mensajes de **WM\_** .  Una excepción, sin embargo, es el mensaje de la CONTROL\- notificación de **BN\_CLICKED** enviado por los botones cuando el usuario haga clic en.  Este mensaje se trata especialmente como mensaje de comando y se distribuye como otros comandos.  
  
3.  Mensajes de comando  
  
     Esto incluye los mensajes de notificación de **WM\_COMMAND** de objetos de la interfaz de usuario: menús, botones de la barra de herramientas, y teclas de aceleración.  El marco procesa comandos de manera diferente de otros mensajes, y se pueden controlar por varias clases de objetos, como se explica en [Destinos de comando](../mfc/command-targets.md).  
  
##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Mensajes de Windows y mensajes de la CONTROL\-notificación  
 Los mensajes en las categorías 1 y 2 — los mensajes de Windows y las notificaciones del control \)se administran mediante las ventanas: objetos de clases derivadas de la clase `CWnd`.  Esto incluye `CFrameWnd`, `CMDIFrameWnd`, `CMDIChildWnd`, `CView`, `CDialog`, y dispone de clases derivadas de estas clases base.  Tales objetos encapsulan `HWND`, un identificador de una ventana de Windows.  
  
##  <a name="_core_command_messages"></a> Mensajes de comando  
 Los mensajes de la categoría 3 — comandos — se pueden controlar mediante una gran variedad de objetos: documentos, plantillas de documento, y el objeto application propio además de las ventanas y vistas.  Cuando un comando afecta directamente a algún objeto determinado, tiene sentido de tener ese controlador de objeto el comando.  Por ejemplo, asocia el comando abierto en el menú archivo lógicamente a la aplicación: la aplicación abre un documento especificado de recibir el comando.  El controlador para el comando abierto es tan una función miembro de clase de aplicación.  Para obtener más información sobre comandos y cómo se enrutan a objetos, vea [Cómo el marco de trabajo llama a un controlador](../mfc/how-the-framework-calls-a-handler.md).  
  
## Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)