---
title: "Default Control Events | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Dialog editor, default control events"
  - "controls [C++], default control events"
  - "events [C++], controls"
  - "dialog box controls, events"
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Default Control Events
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los siguientes controles tienen los eventos predeterminados indicados a continuación:  
  
|Nombre del control|Evento predeterminado|  
|------------------------|---------------------------|  
|Animate|**ACN\_START**|  
|Check Box|**BN\_CLICKED**|  
|Combo Box|**CBN\_SELCHANGE**|  
|Personalizar|**TTN\_GETDISPINFO**|  
|Date time picker|**DTN\_DATETIMECHANGE**|  
|Cuadro de edición|**EN\_CHANGE**|  
|Cuadro de grupo|\(No aplicable\)|  
|Hot key|**NM\_OUTOFMEMORY**|  
|Dirección IP|**IPN\_FIELDCHANGED**|  
|List|**LVN\_ITEMCHANGE**|  
|Cuadro de lista|**LBN\_SELCHANGE**|  
|Month calendar|**MCN\_SELCHANGE**|  
|Picture|\(No aplicable\)|  
|Progress|**NM\_CUSTOMDRAW**|  
|Push button|**BN\_CLICKED**|  
|Radio button|**BN\_CLICKED**|  
|Rich edit|**EN\_CHANGE**|  
|Scroll bar|**NM\_THEMECHANGED**|  
|Slider|**NM\_CUSTOMDRAW**|  
|Spin|**UDN\_DELTAPOS**|  
|Static Text|\(No aplicable\)|  
|Tab|**TCN\_SELCHANGE**|  
|Tree|**TVN\_SELCHANGE**|  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
## Requisitos  
 Win32  
  
## Vea también  
 [Defining Member Variables for Dialog Controls](../mfc/defining-member-variables-for-dialog-controls.md)   
 [Tipos de mensajes asociados a objetos de la interfaz de usuario](../mfc/reference/message-types-associated-with-user-interface-objects.md)   
 [Editar un controlador de mensajes](../mfc/reference/editing-a-message-handler.md)   
 [Definir un controlador de mensajes para un mensaje reflejado](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)   
 [Declarar una variable basada en una clase de control nueva](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)   
 [Reemplazar una función virtual](../ide/overriding-a-virtual-function-visual-cpp.md)