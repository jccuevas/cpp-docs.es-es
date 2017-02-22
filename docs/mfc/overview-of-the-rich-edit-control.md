---
title: "Informaci&#243;n general del control Rich Edit | Microsoft Docs"
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
  - "controles Rich Edit"
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Informaci&#243;n general del control Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Si utiliza un control rich edit en un cuadro de diálogo \(independientemente de si la aplicación es SDI, MDI, o diálogo\- basado\), debe llamar a [AfxInitRichEdit](../Topic/AfxInitRichEdit.md) una vez antes de que se muestre el cuadro de diálogo.  Un lugar típico para llamar a esta función es la función miembro de `InitInstance` del programa.  No necesita llamarlo para cada vez que se muestra el cuadro de diálogo, solo la primera vez.  No tiene que llamar a `AfxInitRichEdit` si trabaja con `CRichEditView`.  
  
 Los controles rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) proporcionan una interfaz de programación para dar formato al texto.  Sin embargo, una aplicación debe implementar cualquier componente de la interfaz de usuario necesario colocar operaciones de formato a disposición del usuario.  Es decir, el control rich edit permite cambiar los atributos de caracteres o del párrafo de texto seleccionado.  Algunos ejemplos de los atributos de caracteres están en negrita, cursiva, familia de fuentes, y tamaño en puntos.  Los ejemplos de los atributos de párrafo incluyen la alineación, márgenes, y las tabulaciones.  Sin embargo, depende de usted para proporcionar la interfaz de usuario, si eso es botones de la barra de herramientas, elementos de menú, cuadro de diálogo o de carácter de formato.  También hay funciones para ver el control rich edit para los atributos de la selección actual.  Utilice estas funciones para mostrar las configuraciones actuales para los atributos, por ejemplo, estableciendo una marca de verificación en la interfaz de usuario de comandos si la selección tiene el atributo negrita formato de caracteres.  
  
 Para obtener más información sobre el carácter y el formato de párrafo, vea [Formato de caracteres](../mfc/character-formatting-in-rich-edit-controls.md) y [Formato de párrafo](../mfc/paragraph-formatting-in-rich-edit-controls.md) más adelante en este tema.  
  
 Los controles rich edit admiten casi todas las operaciones y mensajes de notificación utilizados con controles de edición de varias líneas.  Así, las aplicaciones que utilizan con los controles de edición se pueden cambiar fácilmente para utilizar los controles rich edit.  Aplicaciones de permisos adicionales de mensajes y de notificaciones para tener acceso a la funcionalidad única a los controles rich edit.  Para obtener información sobre los controles de edición, vea [CEdit](../mfc/reference/cedit-class.md).  
  
 Para obtener más información sobre notificaciones, vea [Notificaciones de un control Rich edit](../mfc/notifications-from-a-rich-edit-control.md) más adelante en este tema.  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)