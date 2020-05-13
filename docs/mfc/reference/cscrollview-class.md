---
title: CScrollView (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 5d0eb163fae2aa5fc63470e1c499311ab1a402a6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754423"
---
# <a name="cscrollview-class"></a>CScrollView (clase)

Un [CView](../../mfc/reference/cview-class.md) con capacidades de desplazamiento.

## <a name="syntax"></a>Sintaxis

```
class CScrollView : public CView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Construye un objeto `CScrollView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Indica si la vista de desplazamiento tiene barras de desplazamiento horizontales y verticales.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Rellena el área de una vista fuera del área de desplazamiento.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Obtiene la posición de desplazamiento actual en las unidades de dispositivo.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Obtiene el modo de asignación actual, el tamaño total y los tamaños de línea y página de la vista desplazable. Los tamaños están en las unidades de dispositivo.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Obtiene la posición de desplazamiento actual en unidades lógicas.|
|[CScrollView::GetTotalSize](#gettotalsize)|Obtiene el tamaño total de la vista de desplazamiento en unidades lógicas.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Hace que el tamaño de la vista dicte el tamaño de su marco.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Desplaza la vista a un punto determinado, especificado en unidades lógicas.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Coloca la vista de desplazamiento en modo de escala a ajuste.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Establece el modo de asignación, el tamaño total y las cantidades de desplazamiento horizontal y vertical de la vista de desplazamiento.|

## <a name="remarks"></a>Observaciones

Puede controlar el desplazamiento estándar usted mismo `CView` en cualquier clase derivada de reemplazando el asignado mensaje [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funciones miembro. Pero `CScrollView` añade las siguientes `CView` características a sus capacidades:

- Administra los tamaños de ventanas y ventanas gráficas y los modos de asignación.

- Se desplaza automáticamente en respuesta a los mensajes de la barra de desplazamiento.

- Se desplaza automáticamente en respuesta a los mensajes del teclado, un mouse que no se desplaza o la rueda IntelliMouse.

Para desplazarse automáticamente en respuesta a los mensajes del teclado, agregue un mensaje de WM_KEYDOWN y pruebe VK_DOWN, VK_PREV y llame a [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos).

Puede controlar el desplazamiento de la rueda del mouse mediante la invalidación de las funciones miembro [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) y [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) asignados por mensaje. Como son `CScrollView`para , estas funciones miembro admiten el comportamiento recomendado para [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel), el mensaje de rotación de la rueda.

Para aprovechar las ventajas del desplazamiento `CScrollView` automático, `CView`derive la clase de vista en lugar de de . Cuando se crea la vista por primera vez, si desea calcular el tamaño de `SetScrollSizes` la vista desplazable en función del tamaño del documento, llame a la función miembro desde la invalidación de [CView::OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) o [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate). (Debe escribir su propio código para consultar el tamaño del documento. Para obtener un ejemplo, vea el [ejemplo Scribble](../../overview/visual-cpp-samples.md).)

La llamada `SetScrollSizes` a la función miembro establece el modo de asignación de la vista, las dimensiones totales de la vista de desplazamiento y las cantidades que se desplazarán horizontal y verticalmente. Todos los tamaños están en unidades lógicas. El tamaño lógico de la vista se calcula normalmente a partir de los datos almacenados en el documento, pero en algunos casos es posible que desee especificar un tamaño fijo. Para obtener ejemplos de ambos enfoques, vea [CScrollView::SetScrollSizes](#setscrollsizes).

Especifique los importes que se desplazarán horizontal y verticalmente en unidades lógicas. De forma predeterminada, si el usuario hace clic en `CScrollView` un eje de la barra de desplazamiento fuera del cuadro de desplazamiento, desplaza una "página." Si el usuario hace clic en una flecha `CScrollView` de desplazamiento en cualquiera de los extremos de una barra de desplazamiento, desplaza una "línea." De forma predeterminada, una página es 1/10 del tamaño total de la vista; una línea es 1/10 del tamaño de página. Invalide estos valores predeterminados `SetScrollSizes` pasando tamaños personalizados en la función miembro. Por ejemplo, puede establecer el tamaño horizontal en una fracción del ancho del tamaño total y el tamaño vertical en el alto de una línea de la fuente actual.

En lugar de `CScrollView` desplazarse, puede escalar automáticamente la vista al tamaño de ventana actual. En este modo, la vista no tiene barras de desplazamiento y la vista lógica se estira o se retrasa para ajustarse exactamente al área de cliente de la ventana. Para utilizar esta capacidad de escalado para ajustar, llame a [CScrollView::SetScaleToFitSize](#setscaletofitsize). (Llame `SetScaleToFitSize` a `SetScrollSizes`cualquiera o , pero no a ambos.)

Antes `OnDraw` de llamar a la función `CScrollView` miembro de la clase `CPaintDC` de vista derivada, ajusta `OnDraw`automáticamente el origen de la ventana gráfica para el objeto de contexto de dispositivo que pasa a .

Para ajustar el origen de la `CScrollView` ventana gráfica para la ventana de desplazamiento, reemplaza [CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Este ajuste es `CPaintDC` automático para `CScrollView` el `OnDraw`contexto del dispositivo `CScrollView::OnPrepareDC` que pasa a , pero debe `CClientDC`llamarse a sí mismo para cualquier otro contexto de dispositivo que utilice, como un archivo . Puede anular `CScrollView::OnPrepareDC` para establecer el lápiz, el color de fondo y otros atributos de dibujo, pero llame a la clase base para realizar la escala.

Las barras de desplazamiento pueden aparecer en tres lugares en relación con una vista, como se muestra en los siguientes casos:

- Las barras de desplazamiento de estilo de ventana estándar se pueden establecer para la vista mediante la WS_HSCROLL y WS_VSCROLL[Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)de Windows .

- Los controles de barra de desplazamiento también se pueden agregar al marco que contiene la vista, en cuyo caso el marco de trabajo reenvía WM_HSCROLL y WM_VSCROLL mensajes desde la ventana de marco a la vista activa actualmente.

- El marco de trabajo también `CSplitterWnd` reenvía los mensajes de desplazamiento de un control divisor al panel divisor activo actualmente (una vista). Cuando se coloca en un [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) con barras de desplazamiento compartidas, un `CScrollView` objeto usará los compartidos en lugar de crear los suyos propios.

Para obtener más `CScrollView`información sobre el uso de , vea Arquitectura de [documento/vista](../../mfc/document-view-architecture.md) y Clases de [vista derivadas disponibles en MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cscrollviewcheckscrollbars"></a><a name="checkscrollbars"></a>CScrollView::CheckScrollBars

Llame a esta función miembro para determinar si la vista de desplazamiento tiene barras horizontales y verticales.

```cpp
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>Parámetros

*bHasHorzBar*<br/>
Indica que la aplicación tiene una barra de desplazamiento horizontal.

*bHasVertBar*<br/>
Indica que la aplicación tiene una barra de desplazamiento vertical.

## <a name="cscrollviewcscrollview"></a><a name="cscrollview"></a>CScrollView::CScrollView

Construye un objeto `CScrollView`.

```
CScrollView();
```

### <a name="remarks"></a>Observaciones

Debe llamar `SetScrollSizes` a `SetScaleToFitSize` una o antes de que se pueda usar la vista de desplazamiento.

## <a name="cscrollviewfilloutsiderect"></a><a name="filloutsiderect"></a>CScrollView::FillOutsideRect

Llame `FillOutsideRect` para rellenar el área de la vista que aparece fuera del área de desplazamiento.

```cpp
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Contexto del dispositivo en el que se va a realizar el llenado.

*Pbrush*<br/>
Cepillo con el que se va a rellenar el área.

### <a name="remarks"></a>Observaciones

Utilícelo `FillOutsideRect` en la función de controlador de la vista de `OnEraseBkgnd` desplazamiento para evitar el repintado excesivo de fondo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

## <a name="cscrollviewgetdevicescrollposition"></a><a name="getdevicescrollposition"></a>CScrollView::GetDeviceScrollPosition

Llame `GetDeviceScrollPosition` cuando necesite las posiciones horizontales y verticales actuales de los cuadros de desplazamiento en las barras de desplazamiento.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Las posiciones horizontales y verticales (en unidades de dispositivo) de los cuadros de desplazamiento como un `CPoint` objeto.

### <a name="remarks"></a>Observaciones

Este par de coordenadas corresponde a la ubicación del documento al que se ha desplazado la esquina superior izquierda de la vista. Esto es útil para compensar las posiciones del dispositivo del ratón a las posiciones del dispositivo de vista de desplazamiento.

`GetDeviceScrollPosition`devuelve valores en unidades de dispositivo. Si desea unidades `GetScrollPosition` lógicas, utilice en su lugar.

## <a name="cscrollviewgetdevicescrollsizes"></a><a name="getdevicescrollsizes"></a>CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes`obtiene el modo de asignación actual, el tamaño total y los tamaños de línea y página de la vista desplazable.

```cpp
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
Devuelve las cantidades horizontales y verticales actuales para desplazarse en cada dirección en respuesta a un clic del ratón en un eje de barra de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

*sizeLine*<br/>
Devuelve las cantidades horizontales y verticales actuales para desplazarse en cada dirección en respuesta a un clic del ratón en una flecha de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

### <a name="remarks"></a>Observaciones

Los tamaños están en las unidades de dispositivo. Rara vez se llama a esta función miembro.

## <a name="cscrollviewgetscrollposition"></a><a name="getscrollposition"></a>CScrollView::GetScrollPosition

Llame `GetScrollPosition` cuando necesite las posiciones horizontales y verticales actuales de los cuadros de desplazamiento en las barras de desplazamiento.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Las posiciones horizontales y verticales (en unidades lógicas) de los cuadros de desplazamiento como un `CPoint` objeto.

### <a name="remarks"></a>Observaciones

Este par de coordenadas corresponde a la ubicación del documento al que se ha desplazado la esquina superior izquierda de la vista.

`GetScrollPosition`devuelve valores en unidades lógicas. Si desea unidades `GetDeviceScrollPosition` de dispositivo, utilice en su lugar.

## <a name="cscrollviewgettotalsize"></a><a name="gettotalsize"></a>CScrollView::GetTotalSize

Llame `GetTotalSize` para recuperar los tamaños horizontales y verticales actuales de la vista de desplazamiento.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño total de la vista de desplazamiento en unidades lógicas. El tamaño horizontal `cx` está en `CSize` el miembro del valor devuelto. El tamaño vertical `cy` está en el miembro.

## <a name="cscrollviewresizeparenttofit"></a><a name="resizeparenttofit"></a>CScrollView::ResizeParentToFit

Llame `ResizeParentToFit` para que el tamaño de la vista dicte el tamaño de su ventana de marco.

```cpp
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bShrinkOnly*<br/>
El tipo de cambio de tamaño para realizar. El valor predeterminado, TRUE, reduce la ventana de marco si procede. Las barras de desplazamiento seguirán apareciendo para vistas grandes o ventanas de marco pequeño. Un valor de FALSE hace que la vista siempre cambie el tamaño de la ventana de marco exactamente. Esto puede ser algo peligroso ya que la ventana de marco podría llegar a ser demasiado grande para caber dentro de la ventana de marco de interfaz de documento múltiple (MDI) o la pantalla.

### <a name="remarks"></a>Observaciones

Esto se recomienda solo para vistas en ventanas de marco secundario MDI. Utilícelo `ResizeParentToFit` en `OnInitialUpdate` la función `CScrollView` de controlador de la clase derivada. Para obtener un ejemplo de esta función miembro, vea [CScrollView::SetScrollSizes](#setscrollsizes).

`ResizeParentToFit`supone que se ha establecido el tamaño de la ventana de vista. Si no se ha establecido `ResizeParentToFit` el tamaño de la ventana de vista cuando se llama, obtendrá una aserción. Para asegurarse de que esto no suceda, realice la siguiente llamada antes de llamar: `ResizeParentToFit`

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewscrolltoposition"></a><a name="scrolltoposition"></a>CScrollView::ScrollToPosition

Llamada `ScrollToPosition` para desplazarse a un punto determinado de la vista.

```cpp
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
El punto al que desplazarse, en unidades lógicas. El `x` miembro debe ser un valor positivo (mayor o igual que 0, hasta el tamaño total de la vista). Lo mismo es `y` cierto para el miembro cuando se MM_TEXT el modo de asignación. El `y` miembro es negativo en los modos de asignación distintos de MM_TEXT.

### <a name="remarks"></a>Observaciones

La vista se desplazará para que este punto se encuentra en la esquina superior izquierda de la ventana. No se debe llamar a esta función miembro si la vista se escala para ajustarse.

## <a name="cscrollviewsetscaletofitsize"></a><a name="setscaletofitsize"></a>CScrollView::SetScaleToFitSize

Llame `SetScaleToFitSize` cuando desee escalar automáticamente el tamaño de la ventana gráfica al tamaño de ventana actual.

```cpp
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parámetros

*sizeTotal*<br/>
Los tamaños horizontal y vertical a los que se va a escalar la vista. El tamaño de la vista de desplazamiento se mide en unidades lógicas. El tamaño horizontal está `cx` contenido en el miembro. El tamaño vertical está `cy` contenido en el miembro. Ambos `cx` `cy` y debe ser mayor o igual que 0.

### <a name="remarks"></a>Observaciones

Con las barras de desplazamiento, solo una parte de la vista lógica puede estar visible en cualquier momento. Pero con la capacidad de ajuste de escala, la vista no tiene barras de desplazamiento y la vista lógica se estira o se retrasa para ajustarse exactamente al área de cliente de la ventana. Cuando se cambia el tamaño de la ventana, la vista dibuja sus datos a una nueva escala en función del tamaño de la ventana.

Normalmente colocará la llamada `SetScaleToFitSize` en la invalidación `OnInitialUpdate` de la función miembro de la vista. Si no desea el escalado `SetScrollSizes` automático, llame a la función miembro en su lugar.

`SetScaleToFitSize`se puede utilizar para implementar una operación "Zoom to Fit". Se `SetScrollSizes` utiliza para reinicializar el desplazamiento.

`SetScaleToFitSize`supone que se ha establecido el tamaño de la ventana de vista. Si no se ha establecido `SetScaleToFitSize` el tamaño de la ventana de vista cuando se llama, obtendrá una aserción. Para asegurarse de que esto no suceda, realice la siguiente llamada antes de llamar: `SetScaleToFitSize`

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

## <a name="cscrollviewsetscrollsizes"></a><a name="setscrollsizes"></a>CScrollView::SetScrollSizes

Llame `SetScrollSizes` cuando la vista está a punto de actualizarse.

```cpp
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parámetros

*nMapMode*<br/>
El modo de asignación que se establecerá para esta vista. Los valores posibles son:

|Modo de asignación|Unidad lógica|El eje Y positivo se extiende...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 píxel|Hacia abajo|
|MM_HIMETRIC|0,01 mm|Hacia arriba|
|MM_TWIPS|1/1440 en|Hacia arriba|
|MM_HIENGLISH|0.001 en|Hacia arriba|
|MM_LOMETRIC|0,1 mm|Hacia arriba|
|MM_LOENGLISH|0.01 en|Hacia arriba|

Todos estos modos están definidos por Windows. MM_ANISOTROPIC MM_ISOTROPIC Para `CScrollView`. La biblioteca de `SetScaleToFitSize` clases proporciona la función miembro para escalar la vista al tamaño de la ventana. La columna tres de la tabla anterior describe la orientación de las coordenadas.

*sizeTotal*<br/>
El tamaño total de la vista de desplazamiento. El `cx` miembro contiene la extensión horizontal. El `cy` miembro contiene la extensión vertical. Los tamaños están en unidades lógicas. Ambos `cx` `cy` y debe ser mayor o igual que 0.

*sizePage*<br/>
Las cantidades horizontales y verticales para desplazarse en cada dirección en respuesta a un clic del ratón en un eje de la barra de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

*sizeLine*<br/>
Las cantidades horizontales y verticales para desplazarse en cada dirección en respuesta a un clic del ratón en una flecha de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

### <a name="remarks"></a>Observaciones

Llámelo en la `OnUpdate` invalidación de la función miembro para ajustar las características de desplazamiento cuando, por ejemplo, el documento se muestra inicialmente o cuando cambia de tamaño.

Normalmente obtendrá información de tamaño del documento asociado de la vista `GetMyDocSize`llamando a una función miembro de documento, tal vez denominada , que proporcione con la clase de documento derivada. El código siguiente muestra este enfoque:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Como alternativa, es posible que a veces necesite establecer un tamaño fijo, como en el código siguiente:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Debe establecer el modo de asignación en cualquiera de los modos de asignación de Windows, excepto MM_ISOTROPIC o MM_ANISOTROPIC. Si desea utilizar un modo de asignación `SetScaleToFitSize` sin `SetScrollSizes`restricciones, llame a la función miembro en lugar de .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[Clase CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)
