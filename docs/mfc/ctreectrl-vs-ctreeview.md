---
title: "CTreeCtrl frente a CTreeView | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CTreeCtrl"
  - "CTreeView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl (clase), frente a la clase CTreeView"
  - "clase CTreeView, frente a la clase CTreeCtrl"
  - "controles de árbol, y vista de árbol"
  - "controles de vista de árbol"
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTreeCtrl frente a CTreeView
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC proporciona dos clases que encapsulan los controles de árbol: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md).  Cada clase es útil en escenarios diferentes.  
  
 Utilice `CTreeCtrl` cuando necesita un control nivel de ventana secundaria; por ejemplo, en un cuadro de diálogo.  Debería especialmente para utilizar `CTreeCtrl` si hay otros controles secundarios en la ventana, como en un cuadro de diálogo típico.  
  
 Utilice `CTreeView` si desea que el control de árbol para actuar como una ventana de vista en arquitectura documento\/vista así como un control de árbol.  `CTreeView` ocupa toda el área de cliente de una ventana de marco o de la ventana divisora.  Automáticamente se cambia el tamaño cuando se cambia el tamaño de la ventana primaria, y puede procesar mensajes de comando de menú, de teclas de aceleración, las barras de herramientas.  Puesto que un control de árbol contiene los datos necesarios para el árbol, el objeto document correspondiente no tiene que ser complicado — podría usar incluso [CDocument](../mfc/reference/cdocument-class.md) como el tipo de documento de plantilla de documento.  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)