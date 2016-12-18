---
title: "Notificaciones de un control Rich Edit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl (clase), notificaciones"
  - "mensajes, notificación"
  - "notificaciones, de CRichEditCtrl"
  - "controles Rich Edit, notificaciones"
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Notificaciones de un control Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los mensajes de notificación proporcionan los eventos que afectan a un control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\).  Pueden ser procesados por la ventana primaria o, mediante la reflexión de mensaje, por el control rich edit propio.  Los controles rich edit admiten todos los mensajes de notificación utilizados con controles de edición junto con varios adicionales.  Puede determinar qué mensajes de notificación un control rich edit envían su ventana primaria estableciendo su “máscara de evento”.  
  
 Para establecer la máscara de evento de un control rich edit, utilice la función miembro de [SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md) .  Puede recuperar la máscara de suceso actual para un control rich edit utilizando la función miembro de [GetEventMask](../Topic/CRichEditCtrl::GetEventMask.md) .  
  
 Los párrafos siguientes se muestran varias notificaciones específicas y sus usos:  
  
-   **EN\_MSGFILTER** que administra la notificación de **EN\_MSGFILTER** permite una clase, o control rich edit o la ventana primaria, filtra toda la entrada del teclado y de mouse al control.  El controlador puede evitar que el mensaje del teclado o del mouse se procese o puede cambiar el mensaje modificando la estructura especificada de [MSGFILTER](http://msdn.microsoft.com/library/windows/desktop/bb787936) .  
  
-   Identificador de**EN\_PROTECTED**el mensaje de notificación de **EN\_PROTECTED** para detectar cuándo el usuario intenta modificar el texto protegido.  Para marcar un intervalo de texto como protected, puede establecer el efecto protegido de caracteres.  Para obtener más información, vea [Formato de caracteres en los controles Rich edit](../mfc/character-formatting-in-rich-edit-controls.md).  
  
-   **EN\_DROPFILES** puede permitir al usuario para quitar los archivos en un control rich edit procesando el mensaje de notificación de **EN\_DROPFILES** .  La estructura especificada de [ENDROPFILES](http://msdn.microsoft.com/library/windows/desktop/bb787895) contiene información sobre los archivos que están interrumpidos.  
  
-   **EN\_SELCHANGE** una aplicación puede detectar cuando la selección actual cambia procesando el mensaje de notificación de **EN\_SELCHANGE** .  El mensaje de notificación especifica una estructura de [SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb787952) que contiene información sobre la nueva selección.  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)