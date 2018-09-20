---
title: COleResizeBar (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
dev_langs:
- C++
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf1e2b447b4cfe0e2f503d2263354f3537bbb849
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391389"
---
# <a name="coleresizebar-class"></a>COleResizeBar (clase)

Un tipo de barra de control que admite el cambio de tamaño de elementos de OLE en contexto.

## <a name="syntax"></a>Sintaxis

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Construye un objeto `COleResizeBar`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleResizeBar::Create](#create)|Crea y la inicializa en una ventana secundaria de Windows y la asocia a la `COleResizeBar` objeto.|

## <a name="remarks"></a>Comentarios

`COleResizeBar` los objetos aparecen como un [CRectTracker](../../mfc/reference/crecttracker-class.md) controladores de tamaño con un borde sombreado y externo.

`COleResizeBar` los objetos son normalmente incrustados miembros de objetos de ventana de marco derivados de la [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md) clase.

Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

##  <a name="coleresizebar"></a>  COleResizeBar::COleResizeBar

Construye un objeto `COleResizeBar`.

```
COleResizeBar();
```

### <a name="remarks"></a>Comentarios

Llame a `Create` para crear el objeto de la barra de cambio de tamaño.

##  <a name="create"></a>  COleResizeBar::Create

Crea una ventana secundaria y lo asocia a la `COleResizeBar` objeto.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Puntero a la ventana primaria de la barra de cambio de tamaño.

*dwStyle*<br/>
Especifica el [estilo de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributos.

*nID*<br/>
Identificador de ventana secundaria de la barra de cambio de tamaño.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha creado la barra de cambio de tamaño; en caso contrario, es 0.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC SUPERPAD](../../visual-cpp-samples.md)<br/>
[CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc (clase)](../../mfc/reference/coleserverdoc-class.md)
