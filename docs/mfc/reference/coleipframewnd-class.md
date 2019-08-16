---
title: COleIPFrameWnd (clase)
ms.date: 11/04/2016
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
ms.openlocfilehash: 483998529b83d9b28c6ab1b219c4f5288dbd8ec7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503831"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd (clase)

Base para la ventana de la edición en contexto de la aplicación.

## <a name="syntax"></a>Sintaxis

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Construye un objeto `COleIPFrameWnd`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Lo llama el marco de trabajo cuando un elemento se activa para la edición en contexto.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Lo llama el marco de trabajo para cambiar la posición de la ventana de edición en contexto.|

## <a name="remarks"></a>Comentarios

Esta clase crea y coloca barras de control dentro de la ventana de documento de la aplicación contenedora. También controla las notificaciones generadas por un objeto [COleResizeBar](../../mfc/reference/coleresizebar-class.md) incrustado cuando el usuario cambia el tamaño de la ventana de edición en contexto.

Para obtener más información sobre `COleIPFrameWnd`el uso de, vea el artículo [activación](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd

Construye un `COleIPFrameWnd` objeto e inicializa su información de estado en contexto, que se almacena en una estructura de tipo OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oifi) en el Windows SDK.

##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars

El marco de trabajo `OnCreateControlBars` llama a la función cuando un elemento se activa para la edición en contexto.

```
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,
    CWnd* pWndDoc);

virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,
    CFrameWnd* pWndDoc);
```

### <a name="parameters"></a>Parámetros

*pWndFrame*<br/>
Puntero a la ventana de marco de la aplicación contenedora.

*pWndDoc*<br/>
Puntero a la ventana de nivel de documento del contenedor. Puede ser NULL si el contenedor es una aplicación SDI.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ejecuta correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada no hace nada. Invalide esta función para realizar cualquier procesamiento especial necesario cuando se crean barras de control.

##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame

El marco de trabajo `RepositionFrame` llama a la función miembro para colocar las barras de control y cambiar la posición de la ventana de edición en contexto para que todo esté visible.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parámetros

*lpPosRect*<br/>
Puntero a una `RECT` estructura o un `CRect` objeto que contiene las coordenadas de la posición actual de la ventana de marco en contexto, en píxeles, con respecto al área cliente.

*lpClipRect*<br/>
Puntero a una `RECT` estructura o un `CRect` objeto que contiene las coordenadas actuales del rectángulo de recorte en contexto, en píxeles, con respecto al área cliente.

### <a name="remarks"></a>Comentarios

El diseño de las barras de control en la ventana del contenedor difiere del que realiza una ventana de marco no OLE. La ventana de marco no OLE calcula las posiciones de las barras de control y otros objetos a partir de un tamaño de ventana de marco determinado, como en una llamada a [CFrameWnd:: RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). El área cliente es lo que queda después de restar espacio para las barras de control y otros objetos. Por `COleIPFrameWnd` otro lado, una ventana coloca las barras de herramientas de acuerdo con un área cliente determinada. En otras palabras, `CFrameWnd::RecalcLayout` funciona "desde fuera de," mientras que `COleIPFrameWnd::RepositionFrame` funciona "desde el interior".

## <a name="see-also"></a>Vea también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)
