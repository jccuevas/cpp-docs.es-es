---
title: Clase CTreeView | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
dev_langs: C++
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7530569d5e5313ebfcbdaf92ebd245962b9e443c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
##  <a name="ctreeview"></a>CTreeView::CTreeView  
 Construye un objeto `CTreeView`.  
  
```  
CTreeView();
```  
  
##  <a name="gettreectrl"></a>CTreeView:: GetTreeCtrl  
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
