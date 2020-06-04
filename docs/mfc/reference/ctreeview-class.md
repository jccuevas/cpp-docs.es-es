---
title: Clase CTreeView
ms.date: 11/04/2016
f1_keywords:
- CTreeView
- AFXCVIEW/CTreeView
- AFXCVIEW/CTreeView::CTreeView
- AFXCVIEW/CTreeView::GetTreeCtrl
helpviewer_keywords:
- CTreeView [MFC], CTreeView
- CTreeView [MFC], GetTreeCtrl
ms.assetid: 5df583a6-d69f-42ca-9d8d-57e04558afff
ms.openlocfilehash: 2ef93152c83d3bbec2b89ada0596ee612b24701b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373294"
---
# <a name="ctreeview-class"></a>Clase CTreeView

Simplifica el uso del control de árbol y de [CTreeCtrl](../../mfc/reference/ctreectrl-class.md), la clase que encapsula la funcionalidad de control de árbol, con la arquitectura de vista de documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CTreeView : public CCtrlView
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTreeView::CTreeView](#ctreeview)|Construye un objeto `CTreeView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTreeView::GetTreeCtrl](#gettreectrl)|Devuelve el control de árbol asociado a la vista.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre esta arquitectura, vea la información general de la clase [CView](../../mfc/reference/cview-class.md) y las referencias cruzadas citadas allí.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CTreeView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcview.h

## <a name="ctreeviewctreeview"></a><a name="ctreeview"></a>CTreeView::CTreeView

Construye un objeto `CTreeView`.

```
CTreeView();
```

## <a name="ctreeviewgettreectrl"></a><a name="gettreectrl"></a>CTreeView::GetTreeCtrl

Devuelve una referencia al control de árbol asociado a la vista.

```
CTreeCtrl& GetTreeCtrl() const;
```

## <a name="see-also"></a>Consulte también

[Clase CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[Clase CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[CTreeCtrl (clase)](../../mfc/reference/ctreectrl-class.md)
