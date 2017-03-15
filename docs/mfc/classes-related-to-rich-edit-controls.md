---
title: "Clases relacionadas con controles Rich Edit | Microsoft Docs"
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
  - "clases [C++], relacionadas con controles Rich Edit"
  - "CRichEditCtrl (clase), clases relacionadas"
  - "clase CRichEditCtrlItem y CRichEditCtrl"
  - "CRichEditDoc (clase), controles Rich Edit"
  - "CRichEditView (clase), y CRichEditCtrl"
  - "controles Rich Edit, y CRichEditDoc"
  - "controles Rich Edit, y CRichEditItem"
  - "controles Rich Edit, y CRichEditView"
  - "controles Rich Edit, clases relacionadas con"
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Clases relacionadas con controles Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CRichEditView](../mfc/reference/cricheditview-class.md), [CRichEditDoc](../mfc/reference/cricheditdoc-class.md), y las clases de [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) proporcionan la funcionalidad del control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) en el contexto del documento de MFC o de la arquitectura de la vista.  `CRichEditView` mantiene el texto y la característica de formato de texto.  `CRichEditDoc` mantiene la lista de elementos de OLE de cliente que están en la vista.  `CRichEditCntrItem` proporciona acceso de contenedor\- al elemento OLE de cliente.  Para modificar el contenido de `CRichEditView`, utilice [CRichEditView::GetRichEditCtrl](../Topic/CRichEditView::GetRichEditCtrl.md) para tener acceso al control rich edit subyacente.  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)