---
title: CScrollView (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
dev_langs:
- C++
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f259e190daa07ff3f6ed91a0ea92f60cbdfcbd29
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435968"
---
# <a name="cscrollview-class"></a>CScrollView (clase)

Un [CView](../../mfc/reference/cview-class.md) con capacidades de desplazamiento.

## <a name="syntax"></a>Sintaxis

```
class CScrollView : public CView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Construye un objeto `CScrollView`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Indica si la vista de desplazamiento tiene barras de desplazamiento horizontal y vertical.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Rellena el área de una vista fuera del área desplazable.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Obtiene la posición de desplazamiento actual en unidades de dispositivo.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Obtiene el modo de asignación actual, el tamaño total y los tamaños de página y de línea de la vista desplazable. Los tamaños están en unidades de dispositivo.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Obtiene la posición de desplazamiento actual en unidades lógicas.|
|[CScrollView::GetTotalSize](#gettotalsize)|Obtiene el tamaño total de la vista de desplazamiento en unidades lógicas.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Hace que el tamaño de la vista para dictar el tamaño de su marco.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Desplaza la vista a un momento dado, especificado en unidades lógicas.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Coloca la vista de desplazamiento en modo de escala para el ajuste.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Establece el modo de asignación, tamaño total y cantidades de desplazamiento horizontal y vertical de la vista de desplazamiento.|

## <a name="remarks"></a>Comentarios

Puede controlar estándar desplazamiento usted mismo en cualquier clase derivada de `CView` invalidando el mensaje asigna [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funciones miembro. Pero `CScrollView` agrega las siguientes características para su `CView` capacidades:

- Administra los tamaños de ventana y la ventanilla y modos de asignación.

- Se desplaza automáticamente en respuesta a mensajes de la barra de desplazamiento.

- Se desplaza automáticamente en respuesta a los mensajes desde el teclado, un mouse sin desplazamiento o la rueda de IntelliMouse.

Para desplazarse automáticamente en respuesta a los mensajes del teclado, agregar un mensaje WM_KEYDOWN y comprobar VK_DOWN, VK_PREV y llamada [SetScrollPos](/windows/desktop/api/winuser/nf-winuser-setscrollpos).

Puede controlar la rueda del mouse usted mismo desplazamiento invalidando el mensaje asigna [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) y [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) funciones miembro. Tal como están para `CScrollView`, estas funciones miembro admiten el comportamiento recomendado para [WM_MOUSEWHEEL](/windows/desktop/inputdev/wm-mousewheel), el mensaje de rotación de la rueda.

Para aprovechar las ventajas de desplazamiento automático, derive la clase de vista de `CScrollView` en lugar de desde `CView`. Cuando la vista se crea por primera vez, si desea calcular el tamaño de la vista desplazable, en función del tamaño del documento, llamada la `SetScrollSizes` función miembro desde el reemplazo de uno de ellos [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) o [ CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Debe escribir su propio código para consultar el tamaño del documento. Para obtener un ejemplo, vea el [ejemplo Scribble](../../visual-cpp-samples.md).)

La llamada a la `SetScrollSizes` función miembro establece el modo de asignación de la vista, las dimensiones de la vista de desplazamiento y los importes en desplazamiento horizontal y vertical total. Todos los tamaños están en unidades lógicas. Normalmente se calcula el tamaño lógico de la vista de datos almacenados en el documento, pero en algunos casos es posible que desee especificar un tamaño fijo. Para obtener ejemplos de ambos enfoques, consulte [CScrollView::SetScrollSizes](#setscrollsizes).

Especifique los importes en desplazamiento horizontal y vertical en unidades lógicas. De forma predeterminada, si el usuario hace clic en un eje de la barra de desplazamiento fuera del cuadro de desplazamiento, `CScrollView` se desplaza por una "página". Si el usuario hace clic en una flecha de desplazamiento en los extremos de una barra de desplazamiento, `CScrollView` se desplaza una "línea". De forma predeterminada, una página es 1/10 del tamaño total de la vista; una línea es 1/10 del tamaño de página. Invalidar estos valores predeterminados al pasar tamaños personalizados en el `SetScrollSizes` función miembro. Por ejemplo, puede establecer el tamaño horizontal a una fracción del ancho del tamaño total y el tamaño vertical en el alto de una línea en la fuente actual.

En lugar de desplazarse, `CScrollView` puede escalar automáticamente la vista para el tamaño de ventana actual. En este modo, la vista no tiene ninguna barra de desplazamiento y la vista lógica se estira o se encoge para ajustarse exactamente a área de cliente de la ventana. Para utilizar esta capacidad de escalado para ajustar, llame a [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Llame al `SetScaleToFitSize` o `SetScrollSizes`, pero no ambos.)

Antes de la `OnDraw` se llama a la función miembro de la clase de vista derivada, `CScrollView` ajusta automáticamente el origen de la ventanilla para el `CPaintDC` objeto de contexto de dispositivo que pasa a `OnDraw`.

Para ajustar el origen de la ventanilla de la ventana desplazable, `CScrollView` invalida [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Este ajuste es automática para el `CPaintDC` contexto de dispositivo que `CScrollView` pasa a `OnDraw`, pero se debe llamar a `CScrollView::OnPrepareDC` usted mismo para los otros contextos de dispositivo use, como un `CClientDC`. Puede invalidar `CScrollView::OnPrepareDC` para establecer el lápiz, color de fondo y otros atributos de dibujo, pero llamar a la clase base para realizar el escalado.

Las barras de desplazamiento pueden aparecer en tres lugares en relación con una vista, tal como se muestra en los casos siguientes:

- Las barras de desplazamiento de estilo de ventana estándar se pueden establecer para la vista mediante el WS_HSCROLL y WS_VSCROLL[Windows estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles).

- También se pueden agregar controles de barra de desplazamiento en el marco que contiene la vista, en cuyo caso el marco de trabajo reenvía mensajes WM_HSCROLL y WM_VSCROLL desde la ventana de marco en la vista activa actualmente.

- El marco de trabajo también reenvía desplazar los mensajes de un `CSplitterWnd` control divisor al panel divisor actualmente activo (una vista). Cuando se coloca en un [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) con barras de desplazamiento compartido, un `CScrollView` objeto usará las compartido en lugar de crear su propio.

Para obtener más información sobre el uso de `CScrollView`, consulte [arquitectura documento/vista](../../mfc/document-view-architecture.md) y [derivadas vista de clases disponibles en MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="checkscrollbars"></a>  CScrollView::CheckScrollBars

Llame a esta función miembro para determinar si la vista de desplazamiento tiene barras horizontales y verticales.

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parámetros

*bHasHorzBar*<br/>
Indica que la aplicación tiene una barra de desplazamiento horizontal.

*bHasVertBar*<br/>
Indica que la aplicación tiene una barra de desplazamiento vertical.

##  <a name="cscrollview"></a>  CScrollView::CScrollView

Construye un objeto `CScrollView`.

```
CScrollView();
```

### <a name="remarks"></a>Comentarios

Debe llamar a `SetScrollSizes` o `SetScaleToFitSize` antes el desplazamiento es utilizable vista.

##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect

Llame a `FillOutsideRect` para rellenar el área de la vista que aparece fuera del área desplazable.

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Contexto de dispositivo en el que el rellenado consiste en realizarse.

*pBrush*<br/>
Pincel que está el área que se debe rellenar.

### <a name="remarks"></a>Comentarios

Use `FillOutsideRect` en la vista de desplazamiento `OnEraseBkgnd` función de controlador para evitar que vuelva a dibujar excesivo en segundo plano.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition

Llamar a `GetDeviceScrollPosition` cuando necesite las posiciones actuales de horizontales y verticales de los cuadros de desplazamiento en las barras de desplazamiento.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Valor devuelto

La posición horizontal y vertical (en unidades de dispositivo) de los cuadros de desplazamiento como una `CPoint` objeto.

### <a name="remarks"></a>Comentarios

Este par de coordenadas corresponde a la ubicación en el documento al que se ha desplazado la esquina superior izquierda de la vista. Esto es útil para la compensación de las posiciones de dispositivo de mouse a las posiciones de dispositivo de vista de desplazamiento.

`GetDeviceScrollPosition` Devuelve valores de unidades de dispositivo. Si desea que las unidades lógicas, utilice `GetScrollPosition` en su lugar.

##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes` Obtiene el modo de asignación actual, el tamaño total y los tamaños de página y de línea de la vista desplazable.

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parámetros

*nMapMode*<br/>
Devuelve el modo de asignación actual para esta vista. Para obtener una lista de valores posibles, vea `SetScrollSizes`.

*sizeTotal*<br/>
Devuelve el tamaño total actual de la vista de desplazamiento en unidades de dispositivo.

*sizePage*<br/>
Devuelve las cantidades horizontales y verticales actuales para desplazarse en cada dirección en respuesta a un mouse haga clic en un eje de la barra de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

*sizeLine*<br/>
Devuelve las cantidades horizontales y verticales actuales para desplazarse en cada dirección en respuesta a un mouse haga clic en una flecha de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

### <a name="remarks"></a>Comentarios

Los tamaños están en unidades de dispositivo. Raramente se llama a esta función miembro.

##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition

Llamar a `GetScrollPosition` cuando necesite las posiciones actuales de horizontales y verticales de los cuadros de desplazamiento en las barras de desplazamiento.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Valor devuelto

La posición horizontal y vertical (en unidades lógicas) de los cuadros de desplazamiento como una `CPoint` objeto.

### <a name="remarks"></a>Comentarios

Este par de coordenadas corresponde a la ubicación en el documento al que se ha desplazado la esquina superior izquierda de la vista.

`GetScrollPosition` Devuelve valores de las unidades lógicas. Si desea que las unidades de dispositivo, use `GetDeviceScrollPosition` en su lugar.

##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize

Llame a `GetTotalSize` para obtener el tamaño horizontal y vertical actual de la vista de desplazamiento.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño total de la vista de desplazamiento en unidades lógicas. El tamaño horizontal está en el `cx` miembro de la `CSize` valor devuelto. Es el tamaño vertical de la `cy` miembro.

##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit

Llame a `ResizeParentToFit` para permitir que el tamaño de la vista dicte el tamaño de su ventana de marco.

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bShrinkOnly*<br/>
El tipo de cambio de tamaño para llevar a cabo. El valor predeterminado es TRUE, reduce la ventana de marco si son apropiadas. Para las vistas de gran tamaño o ventanas de marco pequeño seguirá apareciendo las barras de desplazamiento. Un valor FALSE hace que la vista siempre para cambiar el tamaño de la ventana de marco exactamente. Esto puede ser algo peligroso, ya que la ventana de marco podría obtener demasiado grande para que quepa en la ventana de marco MDI (interfaz) de varios documentos o en la pantalla.

### <a name="remarks"></a>Comentarios

Esto se recomienda únicamente para las vistas en ventanas de marco secundario MDI. Use `ResizeParentToFit` en el `OnInitialUpdate` función de controlador de la derivada `CScrollView` clase. Para obtener un ejemplo de esta función miembro, vea [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit` se da por supuesto que se ha establecido el tamaño de la ventana de vista. Si el tamaño de la ventana de vista no se estableció cuando `ResizeParentToFit` es llamado, obtendrá una aserción. Para asegurarse de que esto no sucede, realizar la siguiente llamada antes de llamar a `ResizeParentToFit`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition

Llame a `ScrollToPosition` para desplazarse a un momento dado en la vista.

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parámetros

*PT*<br/>
El punto de desplazamiento, en unidades lógicas. El `x` miembro debe ser un valor positivo (mayor o igual a 0, hasta el tamaño total de la vista). Lo mismo puede decirse de la `y` miembro cuando el modo de asignación es MM_TEXT. El `y` es negativo en los modos de asignación distintos MM_TEXT miembro.

### <a name="remarks"></a>Comentarios

La vista se desplazará por lo que este punto está en la esquina superior izquierda de la ventana. No se debe llamar a esta función miembro si la vista se escala para ajustarse.

##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize

Llamar a `SetScaleToFitSize` cuando desee escalar automáticamente el tamaño de la ventanilla para el tamaño de ventana actual.

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parámetros

*sizeTotal*<br/>
Los tamaños horizontales y verticales para que la vista es escalar. Tamaño de la vista de desplazamiento se mide en unidades lógicas. El tamaño horizontal se encuentra en la `cx` miembro. El tamaño vertical se encuentra en la `cy` miembro. Ambos `cx` y `cy` debe ser mayor o igual que 0.

### <a name="remarks"></a>Comentarios

Con las barras de desplazamiento, sólo una parte de la vista lógica puede aparecer en cualquier momento. Pero con la capacidad de escalado para ajustar la vista no tiene ninguna barra de desplazamiento y la vista lógica se estira o se encoge para ajustarse exactamente a área de cliente de la ventana. Cuando se cambia el tamaño de la ventana, la vista obtiene sus datos a escala en función del tamaño de la ventana nueva.

Normalmente a colocar la llamada a `SetScaleToFitSize` en la invalidación de la vista `OnInitialUpdate` función miembro. Si no desea que el escalado automático, llame a la `SetScrollSizes` función miembro en su lugar.

`SetScaleToFitSize` puede usarse para implementar una operación "Zoom Fit". Use `SetScrollSizes` para reinicializar el desplazamiento.

`SetScaleToFitSize` se da por supuesto que se ha establecido el tamaño de la ventana de vista. Si el tamaño de la ventana de vista no se estableció cuando `SetScaleToFitSize` es llamado, obtendrá una aserción. Para asegurarse de que esto no sucede, realizar la siguiente llamada antes de llamar a `SetScaleToFitSize`:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes

Llamar a `SetScrollSizes` cuando la vista está a punto de actualizarse.

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parámetros

*nMapMode*<br/>
El modo de asignación que establezca para esta vista. Los posibles valores incluyen:

|Modo de asignación|Unidad lógica|Eje y positivo extiende...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 píxel|Hacia abajo|
|MM_HIMETRIC|0,01 mm|Hacia arriba|
|MM_TWIPS|1/1440 en|Hacia arriba|
|MM_HIENGLISH|0,001 pda|Hacia arriba|
|MM_LOMETRIC|0,1 mm|Hacia arriba|
|MM_LOENGLISH|0,01 pda|Hacia arriba|

Todos estos modos se definen mediante Windows. Dos modos de asignación estándar, MM_ISOTROPIC y MM_ANISOTROPIC, no se utilizan para `CScrollView`. La biblioteca de clases proporciona la `SetScaleToFitSize` función miembro para el escalado de la vista al tamaño de ventana. Columna de tres en la tabla anterior describe la orientación de coordenadas.

*sizeTotal*<br/>
El tamaño total de la vista de desplazamiento. El `cx` miembro contiene la medida horizontal. El `cy` miembro contiene la extensión vertical. Los tamaños están en unidades lógicas. Ambos `cx` y `cy` debe ser mayor o igual que 0.

*sizePage*<br/>
Haga clic en las cantidades horizontal y verticales para desplazarse en cada dirección en respuesta a un mouse en un eje de la barra de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

*sizeLine*<br/>
Haga clic en las cantidades horizontal y verticales para desplazarse en cada dirección en respuesta a un mouse en una flecha de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

### <a name="remarks"></a>Comentarios

Llame en el reemplazo del `OnUpdate` función miembro para ajustar las características de desplazamiento cuando, por ejemplo, el documento se muestra inicialmente o cuando cambia de tamaño.

Normalmente obtendrá información sobre el tamaño de documento asociado de la vista mediante una llamada a una función de miembro de documento, quizás denominada `GetMyDocSize`, que se proporciona con la clase derivada de documento. El código siguiente muestra este enfoque:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Como alternativa, es posible que a veces es necesario establecer un tamaño fijo, como se muestra en el código siguiente:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Debe establecer el modo de asignación a cualquiera de los modos de asignación de Windows, excepto MM_ISOTROPIC o MM_ANISOTROPIC. Si desea usar un modo de asignación sin restricciones, llame a la `SetScaleToFitSize` función miembro en lugar de `SetScrollSizes`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC DIBLOOK](../../visual-cpp-samples.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd (clase)](../../mfc/reference/csplitterwnd-class.md)
