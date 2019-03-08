---
title: CMFCCaptionButton (clase)
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
ms.openlocfilehash: 2020f6cb2f0feec28996f69791899c648600b600
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57301056"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton (clase)

La `CMFCCaptionButton` clase implementa un botón que se muestra en la barra de título de un panel acoplable o una ventana de marco reducido. Normalmente, el marco de trabajo crea botones de título automáticamente.

## <a name="syntax"></a>Sintaxis

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|nombre|Descripción|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|Construye un objeto CMFCCaptionButton.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|Devuelve el comando representado por el botón.|
|[CMFCCaptionButton::GetIconID](#geticonid)|Devuelve el identificador de la imagen asociado con el botón.|
|[CMFCCaptionButton::GetRect](#getrect)|Devuelve el rectángulo ocupado por el botón.|
|[CMFCCaptionButton::GetSize](#getsize)|Devuelve el ancho y alto del botón.|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|Indica si se establece el alto de la barra de título en tamaño mini.|
|[CMFCCaptionButton::Move](#move)|Establece la ubicación del botón draw y el estado de mostrar la ventana.|
|[CMFCCaptionButton::OnDraw](#ondraw)|Dibuja el botón de título.|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|Establece el tamaño de la barra de título mini.|

## <a name="remarks"></a>Comentarios

Puede derivar una clase de [CPaneFrameWnd (clase)](../../mfc/reference/cpaneframewnd-class.md) y utilice el método protegido, `AddButton`, para agregar los botones de título en una ventana de marco flotante.

CPaneFrameWnd.h define los identificadores de comando para dos tipos de botones de título:

- AFX_CAPTION_BTN_PIN, que muestra un botón de anclaje cuando el panel de acoplamiento admite el modo de ocultación automática.

- AFX_CAPTION_BTN_CLOSE, que muestra un **cerrar** cuando se puede cerrar u ocultar el panel.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un `CMFCCaptionButton` de objeto y establecer el tamaño de la barra de título mini.

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcaptionbutton.h

##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton

Construye un objeto `CMFCCaptionButton`.

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>Parámetros

*nHit*<br/>
[in] El comando asociado con el botón.

*bLeftAlign*<br/>
[in] Especifica si el botón está alineado a la izquierda.

En la tabla siguiente se enumera los valores posibles para el *nHit* parámetro.

|Valor|Comando|
|-----------|-------------|
|AFX_HTCLOSE|Botón Cerrar.|
|HTMINBUTTON|Botón Minimizar.|
|HTMAXBUTTON|Botón Maximizar.|
|AFX_HTLEFTBUTTON|Botón de flecha izquierda.|
|AFX_HTRIGHTBUTTON|Botón de flecha derecha.|
|AFX_HTMENU|Presionado el botón de menú de flecha.|
|HTNOWHERE|El valor predeterminado; no representa ningún comando.|

### <a name="remarks"></a>Comentarios

De forma predeterminada, los botones de título no están asociados con un comando.

Los botones de título están alineados en la izquierda o derecha.

##  <a name="gethit"></a>  CMFCCaptionButton::GetHit

Devuelve el comando representado por el botón.

```
UINT GetHit() const;
```

### <a name="return-value"></a>Valor devuelto

El comando representado por el botón.

En la tabla siguiente se enumera los posibles valores devueltos.

|Valor|Comando|
|-----------|-------------|
|AFX_HTCLOSE|Botón Cerrar.|
|HTMINBUTTON|Botón Minimizar.|
|HTMAXBUTTON|Botón Maximizar.|
|AFX_HTLEFTBUTTON|Botón de flecha izquierda.|
|AFX_HTRIGHTBUTTON|Botón de flecha derecha.|
|AFX_HTMENU|Presionado el botón de menú de flecha.|
|HTNOWHERE|El valor predeterminado; no representa ningún comando.|

##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID

Devuelve el identificador de la imagen asociado con el botón.

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>Parámetros

*bHorz*<br/>
[in] TRUE para imágenes de flecha izquierda o derecha de los identificadores; FALSE para arriba o hacia abajo de la imagen de la flecha identificadores.

*bMaximized*<br/>
[in] TRUE para un Id. de imagen de maximizar; FALSE para un identificador de la imagen de minimizar.

### <a name="return-value"></a>Valor devuelto

El identificador de la imagen.

### <a name="remarks"></a>Comentarios

Los parámetros especifican los identificadores de las imágenes para minimizar o maximizar los botones de título.

##  <a name="getrect"></a>  CMFCCaptionButton::GetRect

Devuelve el rectángulo ocupado por el botón.

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>Valor devuelto

El rectángulo que representa la ubicación del botón.

### <a name="remarks"></a>Comentarios

Si no ve el botón, el tamaño devuelto es 0.

##  <a name="getsize"></a>  CMFCCaptionButton::GetSize

Devuelve el ancho y alto del botón.

```
static CSize GetSize();
```

### <a name="return-value"></a>Valor devuelto

Las dimensiones externas del botón.

### <a name="remarks"></a>Comentarios

El tamaño devuelto incluye el borde y margen de botón.

##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton

Indica si se establece el alto de la barra de título en tamaño mini.

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el título se establece en mini tamaño; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="move"></a>  CMFCCaptionButton::Move

Establece la ubicación del botón draw y el estado de mostrar la ventana.

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parámetros

*ptTo*<br/>
[in] La nueva ubicación.

*bHide*<br/>
[in] Si se debe mostrar el botón.

##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw

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
[in] Puntero a un contexto de dispositivo para el botón.

*bActive*<br/>
[in] Si se debe dibujar una imagen del botón activo.

*bHorz*<br/>
[in] Reservado para uso en una clase derivada.

*bMaximized*<br/>
[in] Si se debe dibujar una imagen del botón maximizada.

*bDisabled*<br/>
[in] Si se debe dibujar una imagen del botón habilitado.

### <a name="remarks"></a>Comentarios

El *bMaximized* parámetro se utiliza cuando el botón es un maximizar o minimizar botón.

##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton

Establece el tamaño de la barra de título mini.

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parámetros

*bSet*<br/>
[in] TRUE para el alto de la barra de título mini; FALSE para el alto predeterminado de la barra de título.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd (clase)](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)
