---
title: Control de lista y vista de lista | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CListView class [MFC], and CListCtrl
- views [MFC], list and list control
- CListCtrl class [MFC], and CListView
- list views [MFC]
- list controls [MFC], List view
ms.assetid: 7aee1c48-b158-4399-be0b-be366993665e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46c9d559d642b6edf926b9feb49332ef7ec2924a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="list-control-and-list-view"></a>Control de lista y vista de lista
Para mayor comodidad, MFC encapsula el control de lista de dos maneras. Puede usar controles de lista:  
  
-   Directamente, incrustando una [CListCtrl](../mfc/reference/clistctrl-class.md) objeto en una clase de cuadro de diálogo.  
  
-   De forma indirecta, mediante el uso de la clase [CListView](../mfc/reference/clistview-class.md).  
  
 `CListView`facilita la integración de un control de lista con la arquitectura documento/vista MFC, encapsulando el control gran parte como [CEditView](../mfc/reference/ceditview-class.md) encapsula un control de edición: el control rellena el área de superficie completo de una vista MFC. (La vista *es* el control, se convierte en `CListView`.)  
  
 A `CListView` objeto hereda de [CCtrlView](../mfc/reference/cctrlview-class.md) y su base de clases y agrega una función miembro para recuperar el control de lista subyacente. Usar miembros de vista para trabajar con la vista como una vista. Use la [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl) función de miembro para obtener acceso a funciones miembro del control de lista. Utilice a estos miembros para:  
  
-   Agregar, eliminar o manipular "elementos" de la lista.  
  
-   Establecer u obtener atributos del control de lista.  
  
 Para obtener una referencia a la `CListCtrl` subyacente un `CListView`, llame a `GetListCtrl` desde la clase de vista de lista:  
  
 [!code-cpp[NVC_MFCListView#4](../atl/reference/codesnippet/cpp/list-control-and-list-view_1.cpp)]  
  
 En este tema se describe dos formas de usar el control de lista.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

