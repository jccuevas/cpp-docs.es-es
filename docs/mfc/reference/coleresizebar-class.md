---
title: Clase COleResizeBar
ms.date: 11/04/2016
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
ms.openlocfilehash: beb0c37b6ac23310b7d5c8506fbdaf677dd74d8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376154"
---
# <a name="coleresizebar-class"></a>Clase COleResizeBar

Un tipo de barra de control que admite el cambio de tamaño de elementos de OLE en contexto.

## <a name="syntax"></a>Sintaxis

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Construye un objeto `COleResizeBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleResizeBar::Crear](#create)|Crea e inicializa una ventana secundaria de `COleResizeBar` Windows y la asocia al objeto.|

## <a name="remarks"></a>Observaciones

`COleResizeBar`los objetos aparecen como un [CRectTracker](../../mfc/reference/crecttracker-class.md) con un borde sombreado y controladores de cambio de tamaño externo.

`COleResizeBar`los objetos suelen ser miembros incrustados de objetos de ventana de marco derivados de la [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) clase.

Para obtener más información, consulte el artículo [Activación](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coleresizebarcoleresizebar"></a><a name="coleresizebar"></a>COleResizeBar::COleResizeBar

Construye un objeto `COleResizeBar`.

```
COleResizeBar();
```

### <a name="remarks"></a>Observaciones

Llame `Create` para crear el objeto de barra de cambio de tamaño.

## <a name="coleresizebarcreate"></a><a name="create"></a>COleResizeBar::Crear

Crea una ventana secundaria y `COleResizeBar` la asocia con el objeto.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana principal de la barra de cambio de tamaño.

*dwStyle*<br/>
Especifica los atributos de estilo de [ventana.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

*nID*<br/>
El ID de la ventana secundaria de la barra de cambio de tamaño.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se creó la barra de cambio de tamaño; de lo contrario 0.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase COleServerDoc](../../mfc/reference/coleserverdoc-class.md)
