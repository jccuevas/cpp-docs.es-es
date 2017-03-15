---
title: "Controlar las notificaciones de informaci&#243;n sobre herramientas | Microsoft Docs"
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
  - "CToolBarCtrl (clase), controlar notificaciones"
  - "notificaciones, información sobre herramientas"
  - "información sobre herramientas [C++], notificaciones"
  - "TOOLTIPTEXT (estructura)"
ms.assetid: ddb93b5f-2e4f-4537-8053-3453c86e2bbb
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Controlar las notificaciones de informaci&#243;n sobre herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando especifica el estilo de `TBSTYLE_TOOLTIPS` , la barra de herramientas crea y administra un control tooltip.  Una información sobre herramientas es una pequeña ventana emergente que contiene una línea de texto que describe un botón de la barra de herramientas.  La información sobre herramientas se oculta, produciendo sólo cuando el usuario coloca el cursor en un botón de la barra de herramientas y deja allí para aproximadamente la mitad segundo.  La información sobre herramientas aparece cerca del cursor.  
  
 Antes de que se muestre la información sobre herramientas, el mensaje de notificación de **TTN\_NEEDTEXT** se envía a la ventana propietaria de la barra de herramientas para recuperar el texto descriptivo para el botón.  Si la ventana propietaria de la barra de herramientas es una ventana de `CFrameWnd` , la información sobre herramientas se muestran sin ningún esfuerzo adicional, porque `CFrameWnd` tiene un controlador predeterminado para la notificación de **TTN\_NEEDTEXT** .  Si la ventana propietaria de la barra de herramientas no se deriva de `CFrameWnd`, como una vista del cuadro de diálogo o el formulario, debe agregar una entrada al mensaje de la ventana propietaria asignado y proporcionar un controlador de notificación en el mapa de mensajes.  La entrada del mapa de mensajes de la ventana propietaria es la siguiente:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/CPP/handling-tool-tip-notifications_1.cpp)]  
  
## Comentarios  
 `memberFxn`  
 La función miembro que se llamará cuando el texto es necesario para el botón.  
  
 Observe que el id. de una información sobre herramientas siempre es 0.  
  
 Además de notificación de **TTN\_NEEDTEXT** , un control de información sobre herramientas puede enviar notificaciones siguientes a un control de barra de herramientas:  
  
|Notificación|Significado|  
|------------------|-----------------|  
|**TTN\_NEEDTEXTA**|El control de información sobre herramientas requiere el texto ASCII \(Windows 95 solo\)|  
|**TTN\_NEEDTEXTW**|El control de información sobre herramientas requiere el texto Unicode \(Windows NT solo\)|  
|**TBN\_HOTITEMCHANGE**|Indica que el elemento \(resaltado\) activo ha cambiado.|  
|**NM\_RCLICK**|Indica que el usuario ha hecho clic con el botón secundario en un botón.|  
|**TBN\_DRAGOUT**|Indica que el usuario ha hecho clic en el botón y que ha arrastrado el puntero del botón.  Permite una aplicación para implementar una operación de arrastrar y colocar de un botón de la barra de herramientas.  Al recibir esta notificación, la aplicación se iniciará la operación de arrastrar y colocar.|  
|**TBN\_DROPDOWN**|Indica que el usuario ha hecho clic en un botón que utiliza el estilo de **TBSTYLE\_DROPDOWN** .|  
|**TBN\_GETOBJECT**|Indica que el usuario mover el puntero sobre un botón que utiliza el estilo de **TBSTYLE\_DROPPABLE** .|  
  
 Para una función de controlador de ejemplo y más información sobre cómo habilitar información sobre herramientas, vea [Información sobre herramientas](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
## Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)