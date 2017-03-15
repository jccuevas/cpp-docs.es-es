---
title: "Recibir notificaciones de los controles comunes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_NOTIFY"
  - "WM_NOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles comunes [C++], notificaciones"
  - "controles [MFC], notificaciones"
  - "notificaciones, controles comunes"
  - "ON_NOTIFY (macro)"
  - "OnNotify (método)"
  - "recibir notificaciones de los controles comunes"
  - "controles comunes de Windows [C++], notificaciones"
  - "WM_NOTIFY (mensaje)"
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Recibir notificaciones de los controles comunes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles comunes son ventanas secundarias que envían mensajes de notificación a la ventana primaria a eventos, como entrada del usuario, aparecen en el control.  
  
 La aplicación se basa en estos mensajes de notificación para determinar qué acciones las desea el usuario tome.  La mayoría de los controles comunes envían mensajes de notificación como mensajes de **WM\_NOTIFY** .  Los controles de Windows envían la mayoría de los mensajes de notificación como mensajes de **WM\_COMMAND** .  [CWnd::OnNotify](../Topic/CWnd::OnNotify.md) es el controlador del mensaje de **WM\_NOTIFY** .  Como con `CWnd::OnCommand`, la implementación de `OnNotify` envía el mensaje de notificación a `OnCmdMsg` para administrar en mapas de mensajes.  La entrada de mensaje\- mapa para administrar notificaciones es `ON_NOTIFY`.  Para obtener más información, vea [Nota técnica 61: Mensajes de ON\_NOTIFY y de WM\_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md).  
  
 Como alternativa, una clase derivada puede controlar sus propios mensajes de notificación usando “reflexión de mensaje”. Para obtener más información, vea [Nota técnica 62: Mensaje Reflexión para Controles de Windows](../mfc/tn062-message-reflection-for-windows-controls.md).  
  
## Recuperar la posición del cursor en un mensaje de notificación  
 En ocasiones, resulta útil determinar la posición actual del cursor a algunos mensajes de notificación son recibidos por un control común.  Por ejemplo, sería útil determinar la ubicación del cursor actual cuando un control común recibe un mensaje de notificación de **NM\_RCLICK** .  
  
 Hay una manera sencilla de lograrlo llamando a `CWnd::GetCurrentMessage`.  Sin embargo, este método recupera solo la posición del cursor cuando se envió el mensaje.  Dado que el cursor puede haberse movido puesto que el mensaje se envió debe llamar a **CWnd::GetCursorPos** para obtener la posición actual del cursor.  
  
> [!NOTE]
>  `CWnd::GetCurrentMessage` únicamente debe llamarse dentro de un controlador de mensajes.  
  
 Agregue el código siguiente al cuerpo del controlador de mensaje de notificación \(en este ejemplo, **NM\_RCLICK**\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/CPP/receiving-notification-from-common-controls_1.cpp)]  
  
 En este punto, la ubicación del cursor del mouse se almacena en el objeto de `cursorPos` .  
  
## Vea también  
 [Crear y usar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)