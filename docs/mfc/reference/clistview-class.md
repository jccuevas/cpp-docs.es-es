---
title: Clase CListView
ms.date: 11/04/2016
f1_keywords:
- CListView
- AFXCVIEW/CListView
- AFXCVIEW/CListView::CListView
- AFXCVIEW/CListView::GetListCtrl
- AFXCVIEW/CListView::RemoveImageList
helpviewer_keywords:
- CListView [MFC], CListView
- CListView [MFC], GetListCtrl
- CListView [MFC], RemoveImageList
ms.assetid: 7626bdb2-a1b8-4eab-b631-6743710a8432
ms.openlocfilehash: ae1a76e4cdd052ff44dcbd69d467c51741bcc2ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370150"
---
# <a name="clistview-class"></a>Clase CListView

Simplifica el uso del control de lista y de [CListCtrl](../../mfc/reference/clistctrl-class.md), la clase que encapsula la funcionalidad de control de lista, con la arquitectura de vista de documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CListView : public CCtrlView
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CListView::CListView](#clistview)|Construye un objeto `CListView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CListView::GetListCtrl](#getlistctrl)|Devuelve el control de lista asociado a la vista.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CListView::RemoveImageList](#removeimagelist)|Elimina la lista de imágenes especificada de la vista de lista.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre esta arquitectura, vea la información general de la clase [CView](../../mfc/reference/cview-class.md) y las referencias cruzadas citadas allí.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CListView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcview.h

## <a name="clistviewclistview"></a><a name="clistview"></a>CListView::CListView

Construye un objeto `CListView`.

```
CListView();
```

## <a name="clistviewgetlistctrl"></a><a name="getlistctrl"></a>CListView::GetListCtrl

Llame a esta función miembro para obtener una referencia al control de lista asociado a la vista.

```
CListCtrl& GetListCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia al control de lista asociado a la vista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCListView#7](../../atl/reference/codesnippet/cpp/clistview-class_1.cpp)]

## <a name="clistviewremoveimagelist"></a><a name="removeimagelist"></a>CListView::RemoveImageList

Elimina la lista de imágenes especificada de la vista de lista.

```
void RemoveImageList(int nImageList);
```

### <a name="parameters"></a>Parámetros

*nImageList*<br/>
El índice de base cero de la imagen que se va a quitar.

## <a name="see-also"></a>Consulte también

[EJEMPLO DE MFC ROWLIST](../../overview/visual-cpp-samples.md)<br/>
[Clase CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CCtrlView](../../mfc/reference/cctrlview-class.md)
