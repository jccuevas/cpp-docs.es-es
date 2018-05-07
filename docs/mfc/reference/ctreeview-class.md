---
title: Clase CTreeView | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d19d4958de2f7909f2072b2ae2f59c00e63d65a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ctreeview-class"></a>Clase CTreeView
Simplifica el uso del control de árbol y de [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), la clase que encapsula la funcionalidad de control de árbol, con la arquitectura de vista-documento de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CTreeView : public CCtrlView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTreeView::CTreeView](#ctreeview)|Construye un objeto `CTreeView`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTreeView:: GetTreeCtrl](#gettreectrl)|Devuelve el control de árbol asociado a la vista.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre esta arquitectura, vea la información general para la [CView](../../mfc/reference/cview-class.md) clase y las referencias cruzadas citadas no existe.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CTreeView`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcview.h  
  
##  <a name="ctreeview"></a>  CTreeView::CTreeView  
 Construye un objeto `CTreeView`.  
  
```  
CTreeView();
```  
  
##  <a name="gettreectrl"></a>  CTreeView:: GetTreeCtrl  
 Devuelve una referencia al control de árbol asociado a la vista.  
  
```  
CTreeCtrl& GetTreeCtrl() const;  
```  
  
## <a name="see-also"></a>Vea también  
 [Clase de CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [Clase de CCtrlView](../../mfc/reference/cctrlview-class.md)   
 [CTreeCtrl (clase)](../../mfc/reference/ctreectrl-class.md)
