---
title: "Operaciones de portapapeles en los controles Rich Edit | Microsoft Docs"
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
  - "Portapapeles, operaciones en CRichEditCtrl"
  - "operaciones de copia en los controles Rich Edit"
  - "CRichEditCtrl (clase), opciones de Portapapeles"
  - "CRichEditCtrl (clase), operación de pegado"
  - "operación de cortar de la clase CRichEditCtrl"
  - "pegar datos del Portapapeles"
  - "controles Rich Edit, opciones de Portapapeles"
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operaciones de portapapeles en los controles Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La aplicación puede pegar el contenido del portapapeles en un control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) mediante el mejor formato del Portapapeles disponible o un formato de Portapapeles concreto.  También puede determinar si un control rich edit es capaz de pegar un formato de Portapapeles.  
  
 Puede copiar o cortar el contenido de la selección actual utilizando la función miembro de [copiar](../Topic/CRichEditCtrl::Copy.md) o de [Cortado](../Topic/CRichEditCtrl::Cut.md) .  De igual forma, puede pegar el contenido del portapapeles en un control rich edit utilizando la función miembro de [Pegar](../Topic/CRichEditCtrl::Paste.md) .  El control pega el primer formato disponibles que reconoce, que probablemente el formato más descriptivo.  
  
 Para pegar un formato de Portapapeles específico, puede utilizar la función miembro de [PasteSpecial](../Topic/CRichEditCtrl::PasteSpecial.md) .  Esta función resulta útil para las aplicaciones con un comando de pegar especial que permite al usuario seleccionar el formato del Portapapeles.  Puede utilizar la función miembro de [CanPaste](../Topic/CRichEditCtrl::CanPaste.md) para determinar si un formato determinado reconocido por el control.  
  
 También puede utilizar `CanPaste` para determinar si un formato de Portapapeles disponible es reconocido por un control rich edit.  Esta función es útil en el controlador de `OnInitMenuPopup` .  Una aplicación puede habilitar o gris el comando pegar dependiendo de si el control puede pegar cualquier formato disponibles.  
  
 Formatos del Portapapeles enriquecidos del registro de controles de edición dos: el formato de texto enriquecido y un formato denominado el texto y los objetos RichEdit.  Una aplicación puede registrar estos formatos mediante la función de [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) , especificando los valores de **CF\_RTF** y de **CF\_RETEXTOBJ** .  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)