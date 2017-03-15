---
title: "Control de lista y vista de lista | Microsoft Docs"
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
  - "CListCtrl (clase), y CListView"
  - "CListView (clase), y CListCtrl"
  - "controles de lista, vista de lista"
  - "vistas de lista"
  - "vistas, lista y control de lista"
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Control de lista y vista de lista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Por comodidad, MFC encapsula el control de lista de dos maneras.  Puede utilizar los controles de lista:  
  
-   Directamente, insertar un objeto de [CListCtrl](../mfc/reference/clistctrl-class.md) en una clase de diálogo.  
  
-   Indirectamente, mediante la clase [CListView](../mfc/reference/clistview-class.md).  
  
 `CListView` facilita integrar un control de lista con la arquitectura documento\/vista de MFC, encapsular el control mucho mientras [CEditView](../mfc/reference/ceditview-class.md) encapsula un control de edición: el control rellena el área expuesta completa de una vista MFC. \(La vista de Z *es* el control, conversión a `CListView`.\)  
  
 Un objeto de `CListView` hereda de [CCtrlView](../mfc/reference/cctrlview-class.md) y sus clases base y agrega una función miembro para recuperar el control de lista subyacente.  Utilice los miembros de la vista para ejecutar la vista como una vista.  Utilice la función miembro de [GetListCtrl](../Topic/CListView::GetListCtrl.md) para obtener acceso a las funciones miembro de control list.  Utilice estos miembros:  
  
-   Agregar, eliminar, o manipule “los elementos” en la lista.  
  
-   Determinado o obtener los atributos del control de lista.  
  
 Para obtener una referencia a `CListCtrl` que es la base de `CListView`, llame a `GetListCtrl` de la clase de vista de lista:  
  
 [!code-cpp[NVC_MFCListView#4](../mfc/codesnippet/CPP/list-control-and-list-view_1.cpp)]  
  
 Este tema describe las dos maneras de utilizar el control de lista.  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)