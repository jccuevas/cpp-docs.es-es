---
title: CMFCCaptionButton Clase
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: fb47e4373bf53e66dd4af17c89fe2f761858fbfd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367752"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton Clase

La `CMFCCaptionButton` clase implementa un botón que se muestra en la barra de título para un panel de acoplamiento o una ventana de marco pequeño. Normalmente, el marco de trabajo crea botones de título automáticamente.

## <a name="syntax"></a>Sintaxis

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|Nombre|Descripción|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Construye un CMFCCaptionButton objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|Devuelve el comando representado por el botón.|
|[CMFCCaptionButton::GetIconID](#geticonid)|Devuelve el identificador de imagen asociado al botón.|
|[CMFCCaptionButton::GetRect](#getrect)|Devuelve el rectángulo ocupado por el botón.|
|[CMFCCaptionButton::GetSize](#getsize)|Devuelve el ancho y alto del botón.|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Indica si la altura de la barra de título está establecida en tamaño mini.|
|[CMFCCaptionButton::Move](#move)|Establece la ubicación de dibujo del botón y el estado de la ventana.|
|[CMFCCaptionButton::OnDraw](#ondraw)|Dibuja el botón de título.|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Establece el tamaño mini de la barra de título.|

## <a name="remarks"></a>Observaciones

Puede derivar una clase de [CPaneFrameWnd (clase)](../../mfc/reference/cpaneframewnd-class.md) y utilizar el método protected, `AddButton`, para agregar botones de título a una ventana de marco mini.

CPaneFrameWnd.h define los iDE de comando para dos tipos de botones de título:

- AFX_CAPTION_BTN_PIN, que muestra un botón de pasador cuando el panel de acoplamiento admite el modo de ocultación automática.

- AFX_CAPTION_BTN_CLOSE, que muestra un botón **Cerrar** cuando el panel se puede cerrar u ocultar.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se `CMFCCaptionButton` muestra cómo construir un objeto y establecer el tamaño mínimo de la barra de título.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcaptionbutton.h

## <a name="cmfccaptionbuttoncmfccaptionbutton"></a><a name="cmfccaptionbutton"></a>CMFCCaptionButton::CMFCCaptionButton

Construye un objeto `CMFCCaptionButton`.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>Parámetros

*nHit*<br/>
[en] El comando asociado al botón.

*bLeftAlign*<br/>
[en] Especifica si el botón está alineado a la izquierda.

En la tabla siguiente se enumeran los valores posibles para el *nHit* parámetro.

|Value|Get-Help|
|-----------|-------------|
|AFX_HTCLOSE|Botón Cerrar.|
|HTMINBUTTON|Minimizar botón.|
|HTMAXBUTTON|Botón Maximizar.|
|AFX_HTLEFTBUTTON|Botón de flecha izquierda.|
|AFX_HTRIGHTBUTTON|Botón de flecha derecha.|
|AFX_HTMENU|Botón de menú de flecha hacia abajo.|
|HTNOWHERE|El valor predeterminado; no representa ningún comando.|

### <a name="remarks"></a>Observaciones

De forma predeterminada, los botones de título no están asociados a un comando.

Los botones de título se alinean a la derecha o a la izquierda.

## <a name="cmfccaptionbuttongethit"></a><a name="gethit"></a>CMFCCaptionButton::GetHit

Devuelve el comando representado por el botón.

```
UINT GetHit() const;
```

### <a name="return-value"></a>Valor devuelto

El comando representado por el botón.

En la tabla siguiente se enumeran los posibles valores devueltos.

|Value|Get-Help|
|-----------|-------------|
|AFX_HTCLOSE|Botón Cerrar.|
|HTMINBUTTON|Minimizar botón.|
|HTMAXBUTTON|Botón Maximizar.|
|AFX_HTLEFTBUTTON|Botón de flecha izquierda.|
|AFX_HTRIGHTBUTTON|Botón de flecha derecha.|
|AFX_HTMENU|Botón de menú de flecha hacia abajo.|
|HTNOWHERE|El valor predeterminado; no representa ningún comando.|

## <a name="cmfccaptionbuttongeticonid"></a><a name="geticonid"></a>CMFCCaptionButton::GetIconID

Devuelve el identificador de imagen asociado al botón.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>Parámetros

*bHorz*<br/>
[en] TRUE para los iDE de imagen de flecha izquierda o derecha; FALSE para los iDE de imagen de flecha arriba o abajo.

*bMaximized*<br/>
[en] TRUE para un identificador de imagen de maximización; FALSE para un identificador de imagen de minimizar.

### <a name="return-value"></a>Valor devuelto

El ID de imagen.

### <a name="remarks"></a>Observaciones

Los parámetros especifican los ID de imagen para minimizar o maximizar los botones de título.

## <a name="cmfccaptionbuttongetrect"></a><a name="getrect"></a>CMFCCaptionButton::GetRect

Devuelve el rectángulo ocupado por el botón.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>Valor devuelto

El rectángulo que representa la ubicación del botón.

### <a name="remarks"></a>Observaciones

Si no puede ver el botón, el tamaño devuelto es 0.

## <a name="cmfccaptionbuttongetsize"></a><a name="getsize"></a>CMFCCaptionButton::GetSize

Devuelve el ancho y alto del botón.

```
static CSize GetSize();
```

### <a name="return-value"></a>Valor devuelto

Las dimensiones externas del botón.

### <a name="remarks"></a>Observaciones

El tamaño devuelto incluye el margen del botón y el borde.

## <a name="cmfccaptionbuttonisminiframebutton"></a><a name="isminiframebutton"></a>CMFCCaptionButton::IsMiniFrameButton

Indica si la altura de la barra de título está establecida en tamaño mini.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el título se establece en tamaño mini; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cmfccaptionbuttonmove"></a><a name="move"></a>CMFCCaptionButton::Move

Establece la ubicación de dibujo del botón y el estado de la ventana.

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parámetros

*ptTo*<br/>
[en] La nueva ubicación.

*bOcultar*<br/>
[en] Si desea mostrar el botón.

## <a name="cmfccaptionbuttonondraw"></a><a name="ondraw"></a>CMFCCaptionButton::OnDraw

Dibuja el botón de título.

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo para el botón.

*bActive*<br/>
[en] Si desea dibujar una imagen de botón activa.

*bHorz*<br/>
[en] Reservado para su uso en una clase derivada.

*bMaximized*<br/>
[en] Si desea dibujar una imagen de botón maximizada.

*bDiscapacitados*<br/>
[en] Si desea dibujar una imagen de botón habilitada.

### <a name="remarks"></a>Observaciones

El *bMaximized* parámetro se utiliza cuando el botón es un botón de maximizar o minimizar.

## <a name="cmfccaptionbuttonsetminiframebutton"></a><a name="setminiframebutton"></a>CMFCCaptionButton::SetMiniFrameButton

Establece el tamaño mini de la barra de título.

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parámetros

*Bset*<br/>
[en] TRUE para la altura de la barra de título mini; FALSE para la altura predeterminada de la barra de título.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd (clase)](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
