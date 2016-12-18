---
title: "Formato de los caracteres en los controles Rich Edit | Microsoft Docs"
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
  - "CRichEditCtrl (clase), formato de caracteres en"
  - "aplicar formato [C++], caracteres"
  - "controles Rich Edit, formato de caracteres en"
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Formato de los caracteres en los controles Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar funciones miembro de control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) a los caracteres de formato e información del formato de recuperación.  Por caracteres, puede especificar el tipo de letra, el tamaño, el color, y efectos como negrita, cursiva, y protected.  
  
 Puede aplicar formato de caracteres utilizando [SetSelectionCharFormat](../Topic/CRichEditCtrl::SetSelectionCharFormat.md) y el miembro de [SetWordCharFormat](../Topic/CRichEditCtrl::SetWordCharFormat.md) funciona.  Para determinar el formato de caracteres actual para el texto seleccionado, utilice la función miembro de [GetSelectionCharFormat](../Topic/CRichEditCtrl::GetSelectionCharFormat.md) .  La estructura de [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) se utiliza con estas funciones miembro para especificar atributos de caracteres.  Uno de los miembros importantes de **CHARFORMAT** es **dwMask**.  En `SetSelectionCharFormat` y `SetWordCharFormat`, **dwMask** especifica que los atributos de caracteres se establecidos por esta llamada de función.  informes de`GetSelectionCharFormat` los atributos del primer carácter de la selección; **dwMask** especifica los atributos que son coherentes en la selección.  
  
 También puede obtener y establecer el “formato de caracteres predeterminado”, que es el formato aplicado a cualquier carácter posteriormente insertado.  Por ejemplo, si una aplicación establece el formato de caracteres predeterminado en negrita y los tipos de usuario a un carácter, ese carácter está en negrita.  Para obtener y establecer formato de caracteres predeterminado, utilice [GetDefaultCharFormat](../Topic/CRichEditCtrl::GetDefaultCharFormat.md) y el miembro de [SetDefaultCharFormat](../Topic/CRichEditCtrl::SetDefaultCharFormat.md) funciona.  
  
 El atributo “protected” de caracteres no cambia la apariencia del texto.  Si los intentos de modificar protegieron texto, un control rich edit envía su ventana primaria un mensaje de notificación de **EN\_PROTECTED** , lo que la ventana principal permite o evitar el cambio.  Para recibir este mensaje de notificación, debe habilitarlo utilizando la función miembro de [SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md) .  Para obtener más información sobre la máscara de eventos, vea [Notificaciones de un control Rich edit](../mfc/notifications-from-a-rich-edit-control.md), más adelante en este tema.  
  
 El color de primer plano es un atributo de carácter, pero el color de fondo es una propiedad de control rich edit.  Para establecer el color de fondo, utilice la función miembro de [SetBackgroundColor](../Topic/CRichEditCtrl::SetBackgroundColor.md) .  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)