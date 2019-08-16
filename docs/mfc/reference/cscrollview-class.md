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
ms.openlocfilehash: b89daaae4bb578d328e1468cc29470825e19c670
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502589"
---
# <a name="cscrollview-class"></a>CScrollView (clase)

[CView](../../mfc/reference/cview-class.md) con capacidades de desplazamiento.

## <a name="syntax"></a>Sintaxis

```
class CScrollView : public CView
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CScrollView::CScrollView](#cscrollview)|Construye un objeto `CScrollView`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CScrollView::CheckScrollBars](#checkscrollbars)|Indica si la vista de desplazamiento tiene barras de desplazamiento horizontal y vertical.|
|[CScrollView::FillOutsideRect](#filloutsiderect)|Rellena el área de una vista fuera del área de desplazamiento.|
|[CScrollView::GetDeviceScrollPosition](#getdevicescrollposition)|Obtiene la posición de desplazamiento actual en unidades de dispositivo.|
|[CScrollView::GetDeviceScrollSizes](#getdevicescrollsizes)|Obtiene el modo de asignación actual, el tamaño total y los tamaños de línea y página de la vista desplazable. Los tamaños están en unidades de dispositivo.|
|[CScrollView::GetScrollPosition](#getscrollposition)|Obtiene la posición de desplazamiento actual en unidades lógicas.|
|[CScrollView::GetTotalSize](#gettotalsize)|Obtiene el tamaño total de la vista de desplazamiento en unidades lógicas.|
|[CScrollView::ResizeParentToFit](#resizeparenttofit)|Hace que el tamaño de la vista dicte el tamaño de su marco.|
|[CScrollView::ScrollToPosition](#scrolltoposition)|Desplaza la vista a un punto determinado, especificado en unidades lógicas.|
|[CScrollView::SetScaleToFitSize](#setscaletofitsize)|Coloca la vista de desplazamiento en el modo de ajuste horizontal.|
|[CScrollView::SetScrollSizes](#setscrollsizes)|Establece el modo de asignación de la vista de desplazamiento, el tamaño total y las cantidades de desplazamiento horizontal y vertical.|

## <a name="remarks"></a>Comentarios

Puede controlar el desplazamiento estándar en cualquier clase derivada de `CView` invalidando las funciones miembro [OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) asignadas a mensajes. Pero `CScrollView` agrega las siguientes características a sus `CView` capacidades:

- Administra los tamaños de ventana y de ventanilla y los modos de asignación.

- Se desplaza automáticamente en respuesta a los mensajes de la barra de desplazamiento.

- Se desplaza automáticamente en respuesta a los mensajes del teclado, un mouse sin desplazamiento o la rueda de IntelliMouse.

Para desplazarse automáticamente en respuesta a los mensajes del teclado, agregue un mensaje WM_KEYDOWN y pruebe VK_DOWN, VK_PREV y llame a [SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos).

Puede controlar el desplazamiento de la rueda del mouse por su cuenta invalidando las funciones miembro [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel) y [OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel) asignadas por el mensaje. Como son para `CScrollView`, estas funciones miembro admiten el comportamiento recomendado para [WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel), el mensaje de rotación de la rueda.

Para aprovechar el desplazamiento automático, derive la clase de vista de `CScrollView` en lugar `CView`de. Cuando se crea la vista por primera vez, si desea calcular el tamaño de la vista desplazable en función del tamaño del documento, llame a `SetScrollSizes` la función miembro desde la invalidación de [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) o [CView:: actualiza](../../mfc/reference/cview-class.md#onupdate). (Debe escribir su propio código para consultar el tamaño del documento. Para obtener un ejemplo, vea el [ejemplo Scribble](../../overview/visual-cpp-samples.md)).

La llamada a la `SetScrollSizes` función miembro establece el modo de asignación de la vista, las dimensiones totales de la vista de desplazamiento y los valores que se van a desplazar horizontal y verticalmente. Todos los tamaños se encuentran en unidades lógicas. El tamaño lógico de la vista normalmente se calcula a partir de los datos almacenados en el documento, pero en algunos casos es posible que desee especificar un tamaño fijo. Para obtener ejemplos de ambos enfoques, vea [CScrollView:: SetScrollSizes](#setscrollsizes).

Especifique las cantidades para desplazarse horizontal y verticalmente en unidades lógicas. De forma predeterminada, si el usuario hace clic en el eje de una barra de desplazamiento fuera `CScrollView` del cuadro de desplazamiento, desplaza una "página". Si el usuario hace clic en una flecha de desplazamiento en cualquiera de los extremos de `CScrollView` una barra de desplazamiento, desplaza una "línea". De forma predeterminada, una página es 1/10 del tamaño total de la vista; una línea es 1/10 del tamaño de página. Reemplace estos valores predeterminados pasando los tamaños personalizados `SetScrollSizes` en la función miembro. Por ejemplo, puede establecer el tamaño horizontal en una fracción del ancho del tamaño total y el tamaño vertical en el alto de una línea en la fuente actual.

En lugar de desplazarse `CScrollView` , puede escalar automáticamente la vista al tamaño de la ventana actual. En este modo, la vista no tiene barras de desplazamiento y la vista lógica se estira o se reduce para ajustarse exactamente al área cliente de la ventana. Para usar esta capacidad de ajuste de escala, llame a [CScrollView:: SetScaleToFitSize](#setscaletofitsize). (Llame a `SetScaleToFitSize` o `SetScrollSizes`, pero no a ambos).

Antes de `OnDraw` que se llame a la función miembro de la clase `CScrollView` de vista derivada, ajusta automáticamente el origen `CPaintDC` de la ventanilla para el objeto de contexto `OnDraw`del dispositivo al que pasa.

Para ajustar el origen de la ventanilla para la ventana desplazable, `CScrollView` invalida [CView:: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc). Este ajuste es automático para el `CPaintDC` contexto de dispositivo `CScrollView` que se `OnDraw`pasa a, pero debe `CScrollView::OnPrepareDC` llamar a sí mismo para los demás contextos de dispositivo que use `CClientDC`, como un. Puede reemplazar `CScrollView::OnPrepareDC` para establecer el lápiz, el color de fondo y otros atributos de dibujo, pero llamar a la clase base para realizar el escalado.

Las barras de desplazamiento pueden aparecer en tres lugares relativos a una vista, como se muestra en los siguientes casos:

- Las barras de desplazamiento de estilo de ventana estándar se pueden establecer para la vista mediante los[estilos de Windows](../../mfc/reference/styles-used-by-mfc.md#window-styles)WS_HSCROLL y WS_VSCROLL.

- Los controles de barra de desplazamiento también se pueden agregar al marco que contiene la vista, en cuyo caso el marco reenvía los mensajes WM_HSCROLL y WM_VSCROLL desde la ventana de marco a la vista activa.

- El marco de trabajo también reenvía los `CSplitterWnd` mensajes de desplazamiento desde un control divisor al panel de división activo (una vista). Cuando se coloca en [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) con barras de desplazamiento compartidas, un `CScrollView` objeto usará los compartidos en lugar de crear los suyos propios.

Para obtener más información sobre `CScrollView`el uso de, vea [arquitectura de documento/vista](../../mfc/document-view-architecture.md) y [clases de vistas derivadas disponibles en MFC](../../mfc/derived-view-classes-available-in-mfc.md).

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

Debe llamar a `SetScrollSizes` o `SetScaleToFitSize` antes de que se pueda usar la vista de desplazamiento.

##  <a name="filloutsiderect"></a>  CScrollView::FillOutsideRect

Llame `FillOutsideRect` a para rellenar el área de la vista que aparece fuera del área de desplazamiento.

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Contexto de dispositivo en el que se va a realizar el rellenado.

*pBrush*<br/>
Pincel con el que se va a rellenar el área.

### <a name="remarks"></a>Comentarios

Utilice `FillOutsideRect` en la función de controlador `OnEraseBkgnd` de la vista de desplazamiento para evitar la repintado excesiva del fondo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>  CScrollView::GetDeviceScrollPosition

Llame `GetDeviceScrollPosition` a cuando necesite las posiciones horizontal y vertical actuales de los cuadros de desplazamiento en las barras de desplazamiento.

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Las posiciones horizontal y vertical (en unidades de dispositivo) de los cuadros de desplazamiento `CPoint` como un objeto.

### <a name="remarks"></a>Comentarios

Este par de coordenadas corresponde a la ubicación del documento a la que se ha desplazado la esquina superior izquierda de la vista. Esto resulta útil para desplazar las posiciones de los dispositivos del mouse a las posiciones de los dispositivos de la vista de desplazamiento.

`GetDeviceScrollPosition`devuelve valores en unidades de dispositivo. Si desea unidades lógicas, utilice `GetScrollPosition` en su lugar.

##  <a name="getdevicescrollsizes"></a>  CScrollView::GetDeviceScrollSizes

`GetDeviceScrollSizes`Obtiene el modo de asignación actual, el tamaño total y los tamaños de línea y página de la vista desplazable.

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>Parámetros

*nMapMode*<br/>
Devuelve el modo de asignación actual para esta vista. Para obtener una lista de los valores posibles `SetScrollSizes`, vea.

*sizeTotal*<br/>
Devuelve el tamaño total actual de la vista de desplazamiento en unidades de dispositivo.

*sizePage*<br/>
Devuelve las cantidades horizontales y verticales actuales que se van a desplazar en cada dirección en respuesta a un clic del mouse en el eje de la barra de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

*sizeLine*<br/>
Devuelve las cantidades horizontales y verticales actuales que se van a desplazar en cada dirección en respuesta a un clic del mouse en una flecha de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

### <a name="remarks"></a>Comentarios

Los tamaños están en unidades de dispositivo. Rara vez se llama a esta función miembro.

##  <a name="getscrollposition"></a>  CScrollView::GetScrollPosition

Llame `GetScrollPosition` a cuando necesite las posiciones horizontal y vertical actuales de los cuadros de desplazamiento en las barras de desplazamiento.

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>Valor devuelto

Las posiciones horizontal y vertical (en unidades lógicas) de los cuadros de desplazamiento `CPoint` como un objeto.

### <a name="remarks"></a>Comentarios

Este par de coordenadas corresponde a la ubicación del documento a la que se ha desplazado la esquina superior izquierda de la vista.

`GetScrollPosition`devuelve valores en unidades lógicas. Si desea unidades de dispositivo, use `GetDeviceScrollPosition` en su lugar.

##  <a name="gettotalsize"></a>  CScrollView::GetTotalSize

Llame `GetTotalSize` a para recuperar los tamaños horizontal y vertical actuales de la vista de desplazamiento.

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño total de la vista de desplazamiento en unidades lógicas. El tamaño horizontal está en el `cx` miembro `CSize` del valor devuelto. El tamaño vertical está en el `cy` miembro.

##  <a name="resizeparenttofit"></a>  CScrollView::ResizeParentToFit

Llame `ResizeParentToFit` a para que el tamaño de la vista dicte el tamaño de la ventana de marco.

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>Parámetros

*bShrinkOnly*<br/>
Tipo de cambio de tamaño que se va a realizar. El valor predeterminado, TRUE, reduce la ventana de marco si es necesario. Las barras de desplazamiento seguirán apareciendo para vistas grandes o pequeñas ventanas de marco. Un valor FALSE hace que la vista siempre cambie el tamaño de la ventana de marco exactamente. Esto puede ser algo peligroso, ya que la ventana de marco podría llegar a ser demasiado grande para caber en la ventana de marco de la interfaz de múltiples documentos (MDI) o en la pantalla.

### <a name="remarks"></a>Comentarios

Solo se recomienda para las vistas en ventanas de marco secundarias MDI. Use `ResizeParentToFit` en la `OnInitialUpdate` función de controlador de la `CScrollView` clase derivada. Para obtener un ejemplo de esta función miembro, vea [CScrollView:: SetScrollSizes](#setscrollsizes).

`ResizeParentToFit`supone que se ha establecido el tamaño de la ventana de vista. Si no se ha establecido el tamaño de la ventana `ResizeParentToFit` de vista cuando se llama a, obtendrá una aserción. Para asegurarse de que esto no suceda, realice la siguiente llamada antes de `ResizeParentToFit`llamar a:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>  CScrollView::ScrollToPosition

Llame `ScrollToPosition` a para desplazarse a un punto determinado en la vista.

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Punto al que se va a desplazar, en unidades lógicas. El `x` miembro debe ser un valor positivo (mayor o igual que 0, hasta el tamaño total de la vista). Lo mismo se aplica `y` al miembro cuando el modo de asignación es MM_TEXT. El `y` miembro es negativo en modos de asignación distintos de MM_TEXT.

### <a name="remarks"></a>Comentarios

La vista se desplazará para que este punto se encuentre en la esquina superior izquierda de la ventana. No se debe llamar a esta función miembro si la vista se escala para ajustarse.

##  <a name="setscaletofitsize"></a>  CScrollView::SetScaleToFitSize

Llame `SetScaleToFitSize` a si desea escalar automáticamente el tamaño de la ventanilla al tamaño de la ventana actual.

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>Parámetros

*sizeTotal*<br/>
Los tamaños horizontal y vertical a los que se va a escalar la vista. El tamaño de la vista de desplazamiento se mide en unidades lógicas. El tamaño horizontal está incluido en el `cx` miembro. El tamaño vertical está incluido en el `cy` miembro. `cx` Y`cy` deben ser mayores o iguales que 0.

### <a name="remarks"></a>Comentarios

Con las barras de desplazamiento, solo una parte de la vista lógica puede estar visible en cualquier momento. Sin embargo, con la capacidad de ajuste de escala, la vista no tiene barras de desplazamiento y la vista lógica se estira o se reduce para ajustarse exactamente al área cliente de la ventana. Cuando se cambia el tamaño de la ventana, la vista dibuja sus datos en una nueva escala en función del tamaño de la ventana.

Normalmente se realizará la llamada a `SetScaleToFitSize` en la invalidación de la función `OnInitialUpdate` miembro de la vista. Si no desea el escalado automático, llame a `SetScrollSizes` la función miembro en su lugar.

`SetScaleToFitSize`se puede usar para implementar una operación de "zoom para ajustar". Use `SetScrollSizes` para reinicializar el desplazamiento.

`SetScaleToFitSize`supone que se ha establecido el tamaño de la ventana de vista. Si no se ha establecido el tamaño de la ventana `SetScaleToFitSize` de vista cuando se llama a, obtendrá una aserción. Para asegurarse de que esto no suceda, realice la siguiente llamada antes de `SetScaleToFitSize`llamar a:

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>  CScrollView::SetScrollSizes

Llame `SetScrollSizes` a cuando la vista esté a punto de actualizarse.

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>Parámetros

*nMapMode*<br/>
Modo de asignación que se va a establecer para esta vista. Entre los posibles valores se incluyen:

|Modo de asignación|Unidad lógica|El eje y positivo extiende...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1 píxel|Arriba|
|MM_HIMETRIC|0,01 mm|Mirando|
|MM_TWIPS|1/1440 en|Mirando|
|MM_HIENGLISH|0,001 en|Mirando|
|MM_LOMETRIC|0,1 mm|Mirando|
|MM_LOENGLISH|0,01 en|Mirando|

Todos estos modos están definidos por Windows. No se utilizan dos modos de `CScrollView`asignación estándar, MM_ISOTROPIC y MM_ANISOTROPIC. La biblioteca de clases proporciona `SetScaleToFitSize` la función miembro para escalar la vista al tamaño de la ventana. En la columna tres de la tabla anterior se describe la orientación de coordenadas.

*sizeTotal*<br/>
Tamaño total de la vista de desplazamiento. El `cx` miembro contiene la extensión horizontal. El `cy` miembro contiene la extensión vertical. Los tamaños están en unidades lógicas. `cx` Y`cy` deben ser mayores o iguales que 0.

*sizePage*<br/>
Las cantidades horizontal y vertical que se van a desplazar en cada dirección en respuesta a un clic del mouse en un eje de la barra de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

*sizeLine*<br/>
Las cantidades horizontal y vertical que se van a desplazar en cada dirección en respuesta a un clic del mouse en una flecha de desplazamiento. El `cx` miembro contiene la cantidad horizontal. El `cy` miembro contiene la cantidad vertical.

### <a name="remarks"></a>Comentarios

Llámelo en la invalidación de `OnUpdate` la función miembro para ajustar las características de desplazamiento cuando, por ejemplo, el documento se muestre inicialmente o cuando cambie de tamaño.

Normalmente obtendrá información de tamaño del documento asociado a la vista mediante una llamada a una función miembro del documento, `GetMyDocSize`tal vez que se le haya llamado, que proporcione con la clase de documento derivada. En el código siguiente se muestra este enfoque:

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

Como alternativa, en ocasiones es posible que necesite establecer un tamaño fijo, como en el código siguiente:

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

Debe establecer el modo de asignación en cualquiera de los modos de asignación de Windows, excepto MM_ISOTROPIC o MM_ANISOTROPIC. Si desea utilizar un modo de asignación sin restricciones, llame a la `SetScaleToFitSize` función miembro en lugar de `SetScrollSizes`a.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>Vea también

[DIBLOOK de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd (clase)](../../mfc/reference/csplitterwnd-class.md)
