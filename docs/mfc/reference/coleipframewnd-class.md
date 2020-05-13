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
ms.openlocfilehash: 01e259cf01c42add26088b0cbd2f6dab311eb9b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374956"
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd (clase)

Base para la ventana de la edición en contexto de la aplicación.

## <a name="syntax"></a>Sintaxis

```
class COleIPFrameWnd : public CFrameWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Construye un objeto `COleIPFrameWnd`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Llamado por el marco de trabajo cuando se activa un elemento para la edición in situ.|
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Llamado por el marco de trabajo para cambiar la posición de la ventana de edición in situ.|

## <a name="remarks"></a>Observaciones

Esta clase crea y coloca barras de control dentro de la ventana de documento de la aplicación contenedora. También controla las notificaciones generadas por un objeto [COleResizeBar](../../mfc/reference/coleresizebar-class.md) incrustado cuando el usuario cambia el tamaño de la ventana de edición in situ.

Para obtener más `COleIPFrameWnd`información sobre el uso , consulte el artículo [Activación](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`COleIPFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coleipframewndcoleipframewnd"></a><a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd

Construye un `COleIPFrameWnd` objeto e inicializa su información de estado in situ, que se almacena en una estructura de tipo OLEINPLACEFRAMEINFO.

```
COleIPFrameWnd();
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [OLEINPLACEFRAMEINFO](/windows/win32/api/oleidl/ns-oleidl-oleinplaceframeinfo) en el Windows SDK.

## <a name="coleipframewndoncreatecontrolbars"></a><a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars

El marco `OnCreateControlBars` de trabajo llama a la función cuando se activa un elemento para la edición in situ.

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

Distinto de cero en el éxito; de lo contrario, 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada. Reemplace esta función para realizar cualquier procesamiento especial necesario cuando se crean barras de control.

## <a name="coleipframewndrepositionframe"></a><a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame

El marco `RepositionFrame` de trabajo llama a la función miembro para establecer barras de control y cambiar la posición de la ventana de edición en contexto para que todo sea visible.

```
virtual void RepositionFrame(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Parámetros

*lpPosRect*<br/>
Puntero a `RECT` una `CRect` estructura o a un objeto que contiene las coordenadas de posición actual de la ventana de marco in situ, en píxeles, en relación con el área de cliente.

*lpClipRect*<br/>
Puntero a `RECT` una `CRect` estructura o a un objeto que contenga las coordenadas actuales del rectángulo delimitador de la ventana de marco in situ, en píxeles, en relación con el área de cliente.

### <a name="remarks"></a>Observaciones

El diseño de las barras de control en la ventana contenedora difiere del realizado por una ventana de marco no OLE. La ventana de marco no OLE calcula las posiciones de las barras de control y otros objetos a partir de un tamaño de ventana de marco determinado, como en una llamada a [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). El área de cliente es lo que queda después de que se resta espacio para las barras de control y otros objetos. Una `COleIPFrameWnd` ventana, por otro lado, coloca las barras de herramientas de acuerdo con un área de cliente determinada. En otras `CFrameWnd::RecalcLayout` palabras, funciona "desde afuera `COleIPFrameWnd::RepositionFrame` hacia adentro", mientras que trabaja "de adentro hacia afuera".

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)
