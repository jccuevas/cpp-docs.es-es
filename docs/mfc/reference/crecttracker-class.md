---
title: CRectTracker (clase)
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: c3600bc5a945c24e91269bc280b4b8e99c54d4c8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750455"
---
# <a name="crecttracker-class"></a>CRectTracker (clase)

Permite que un elemento se muestre, mueva y redimensione de diferentes maneras.

## <a name="syntax"></a>Sintaxis

```
class CRectTracker
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|Construye un objeto `CRectTracker`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|Se llama cuando se cambia el tamaño del rectángulo.|
|[CRectTracker::Draw](#draw)|Representa el rectángulo.|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Se llama al dibujar `CRectTracker` el borde de un objeto.|
|[CRectTracker::GetHandleMask](#gethandlemask)|Se llama para obtener `CRectTracker` la máscara de los identificadores de cambio de tamaño de un elemento.|
|[CRectTracker::GetTrueRect](#gettruerect)|Devuelve el ancho y el alto del rectángulo, incluidos los identificadores de cambio de tamaño.|
|[CRectTracker::HitTest](#hittest)|Devuelve la posición actual del `CRectTracker` cursor relacionada con el objeto.|
|[CRectTracker::NormalizeHit](#normalizehit)|Normaliza un código de prueba de posicionación.|
|[CRectTracker::OnChangedRect](#onchangedrect)|Se llama cuando el rectángulo se ha redimensionado o movido.|
|[CRectTracker::SetCursor](#setcursor)|Establece el cursor, dependiendo de su posición sobre el rectángulo.|
|[CRectTracker::Track](#track)|Permite al usuario manipular el rectángulo.|
|[CRectTracker::TrackRubberBand](#trackrubberband)|Permite al usuario "banda de goma" la selección.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Determina el tamaño de los identificadores de cambio de tamaño.|
|[CRectTracker::m_nStyle](#m_nstyle)|Estilo(s) actual(es) del rastreador.|
|[CRectTracker::m_rect](#m_rect)|Posición actual (en píxeles) del rectángulo.|
|[CRectTracker::m_sizeMin](#m_sizemin)|Determina el ancho y el alto mínimos del rectángulo.|

## <a name="remarks"></a>Observaciones

`CRectTracker`no tiene una clase base.

Aunque `CRectTracker` la clase está diseñada para permitir al usuario interactuar con elementos OLE mediante una interfaz gráfica, su uso no está restringido a las aplicaciones habilitadas para OLE. Se puede utilizar en cualquier lugar como tal interfaz de usuario es necesaria.

`CRectTracker`los bordes pueden ser líneas sólidas o punteadas. Al elemento se le puede dar un borde sombreado o superponerse con un patrón sombreado para indicar diferentes estados del elemento. Puede colocar ocho identificadores de cambio de tamaño en el borde exterior o interior del elemento. (Para obtener una explicación de los identificadores de cambio de tamaño, vea [GetHandleMask](#gethandlemask).) Por último, a `CRectTracker` le permite cambiar la orientación de un elemento durante el cambio de tamaño.

Para `CRectTracker`utilizar , `CRectTracker` construya un objeto y especifique qué estados de visualización se inicializan. A continuación, puede usar esta interfaz para proporcionar al usuario comentarios visuales sobre el estado actual del elemento OLE asociado al `CRectTracker` objeto.

Para obtener más `CRectTracker`información sobre el uso de , consulte el artículo [Rastreadores](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CRectTracker`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="crecttrackeradjustrect"></a><a name="adjustrect"></a>CRectTracker::AdjustRect

Llamado por el marco de trabajo cuando se cambia el tamaño del rectángulo de seguimiento mediante un identificador de cambio de tamaño.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*nHandle*<br/>
Indice de manejador utilizado.

*lpRect*<br/>
Puntero al tamaño actual del rectángulo. (El tamaño de un rectángulo se da por su altura y anchura.)

### <a name="remarks"></a>Observaciones

El comportamiento predeterminado de esta función permite que `Track` `TrackRubberBand` la orientación del rectángulo cambie solo cuando y se llame con inversión permitida.

Reemplace esta función para controlar el ajuste del rectángulo de seguimiento durante una operación de arrastre. Un método consiste en ajustar las coordenadas especificadas por *lpRect* antes de devolver.

Las características especiales que `CRectTracker`no son compatibles directamente con , como snap-to-grid o keep-aspect-ratio, se pueden implementar reemplazando esta función.

## <a name="crecttrackercrecttracker"></a><a name="crecttracker"></a>CRectTracker::CRectTracker

Crea e inicializa un objeto `CRectTracker`.

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*lpSrcRect*<br/>
Las coordenadas del objeto rectángulo.

*nStyle*<br/>
Especifica el estilo `CRectTracker` del objeto. Se admiten los estilos siguientes:

- `CRectTracker::solidLine`Utilice una línea sólida para el borde del rectángulo.

- `CRectTracker::dottedLine`Utilice una línea punteada para el borde del rectángulo.

- `CRectTracker::hatchedBorder`Utilice un patrón sombreado para el borde del rectángulo.

- `CRectTracker::resizeInside`Cambie el tamaño de los controladores situados dentro del rectángulo.

- `CRectTracker::resizeOutside`Cambie el tamaño de los controladores situados fuera del rectángulo.

- `CRectTracker::hatchInside`El patrón sombreado cubre todo el rectángulo.

### <a name="remarks"></a>Observaciones

El constructor predeterminado `CRectTracker` inicializa el objeto con los valores de *lpSrcRect* e inicializa otros tamaños en los valores predeterminados del sistema. Si el objeto se crea `m_rect` sin parámetros, los miembros de datos y `m_nStyle` los no se inicializan.

## <a name="crecttrackerdraw"></a><a name="draw"></a>CRectTracker::Draw

Llame a esta función para dibujar las líneas externas y la región interna del rectángulo.

```cpp
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto del dispositivo en el que se desea dibujar.

### <a name="remarks"></a>Observaciones

El estilo del rastreador determina cómo se realiza el dibujo. Consulte el `CRectTracker` constructor para obtener más información sobre los estilos disponibles.

## <a name="crecttrackerdrawtrackerrect"></a><a name="drawtrackerrect"></a>CRectTracker::DrawTrackerRect

Llamado por el marco de trabajo siempre que `Track` `TrackRubberBand` la posición del rastreador ha cambiado mientras está dentro de la función miembro o.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Puntero a `RECT` la que contiene el rectángulo que se desea dibujar.

*pWndClipTo*<br/>
Puntero a la ventana para utilizar en el recorte del rectángulo.

*pDC*<br/>
Puntero al contexto del dispositivo en el que se desea dibujar.

*pWnd*<br/>
Puntero a la ventana en la que se producirá el dibujo.

### <a name="remarks"></a>Observaciones

La implementación predeterminada `CDC::DrawFocusRect`realiza una llamada a , que dibuja un rectángulo de puntos.

Invalide esta función para proporcionar diferentes comentarios durante la operación de seguimiento.

## <a name="crecttrackergethandlemask"></a><a name="gethandlemask"></a>CRectTracker::GetHandleMask

El marco de trabajo llama a esta función miembro para recuperar la máscara para los identificadores de cambio de tamaño de un rectángulo.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Valor devuelto

La máscara `CRectTracker` de los identificadores de cambio de tamaño de un elemento.

### <a name="remarks"></a>Observaciones

Los identificadores de cambio de tamaño aparecen en los lados y esquinas del rectángulo y permiten al usuario controlar la forma y el tamaño del rectángulo.

Un rectángulo tiene 8 identificadores de cambio de tamaño numerados 0-7. Cada identificador de cambio de tamaño está representado por un bit en la máscara; el valor de ese bit es 2 *n*, donde *n* es el número de identificador de cambio de tamaño. Los bits 0-3 corresponden a los manejadores de cambio de tamaño de esquina, comenzando en la parte superior izquierda moviéndose en el sentido de las agujas del reloj. Los bits 4-7 corresponden a los manejadores de cambio de tamaño laterales comenzando en la parte superior en el sentido de las agujas del reloj. En la ilustración siguiente se muestran los identificadores de cambio de tamaño de un rectángulo y sus correspondientes números y valores de identificador de cambio de tamaño:

![Cambiar el tamaño de los números de los manejadore](../../mfc/reference/media/vc35dp1.gif "Números del controlador de cambio de tamaño")

La implementación `GetHandleMask` predeterminada de devuelve la máscara de los bits para que aparezcan los identificadores de cambio de tamaño. Si el bit único está activado, se dibujará el controlador de cambio de tamaño correspondiente.

Invalide esta función miembro para ocultar o mostrar los identificadores de cambio de tamaño indicados.

## <a name="crecttrackergettruerect"></a><a name="gettruerect"></a>CRectTracker::GetTrueRect

Llame a esta función para recuperar las coordenadas del rectángulo.

```cpp
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Parámetros

*lpTrueRect*<br/>
Puntero a `RECT` la estructura que contendrá `CRectTracker` las coordenadas del dispositivo del objeto.

### <a name="remarks"></a>Observaciones

Las dimensiones del rectángulo incluyen la altura y la anchura de los identificadores de cambio de tamaño situados en el borde exterior. Al volver, *lpTrueRect* siempre es un rectángulo normalizado en las coordenadas del dispositivo.

## <a name="crecttrackerhittest"></a><a name="hittest"></a>CRectTracker::HitTest

Llame a esta función para averiguar si el usuario ha capturado un identificador de cambio de tamaño.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
El punto, en las coordenadas del dispositivo, para probar.

### <a name="return-value"></a>Valor devuelto

El valor devuelto se basa `CRectTracker::TrackerHit` en el tipo enumerado y puede tener uno de los siguientes valores:

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight`1

- `CRectTracker::hitBottomRight`2

- `CRectTracker::hitBottomLeft`3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight`5

- `CRectTracker::hitBottom`6

- `CRectTracker::hitLeft`7

- `CRectTracker::hitMiddle`8

## <a name="crecttrackerm_nhandlesize"></a><a name="m_nhandlesize"></a>CRectTracker::m_nHandleSize

El tamaño, en píxeles, de los `CRectTracker` identificadores de cambio de tamaño.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Observaciones

Inicializado con el valor predeterminado del sistema.

## <a name="crecttrackerm_rect"></a><a name="m_rect"></a>CRectTracker::m_rect

La posición actual del rectángulo en las coordenadas de cliente (píxeles).

```
CRect m_rect;
```

## <a name="crecttrackerm_sizemin"></a><a name="m_sizemin"></a>CRectTracker::m_sizeMin

El tamaño mínimo del rectángulo.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Observaciones

Ambos valores `cx` predeterminados y `cy`, se calculan a partir del valor predeterminado del sistema para el ancho del borde. Este miembro de datos `AdjustRect` solo lo utiliza la función miembro.

## <a name="crecttrackerm_nstyle"></a><a name="m_nstyle"></a>CRectTracker::m_nStyle

Estilo actual del rectángulo.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Observaciones

Consulte [CRectTracker::CRectTracker](#crecttracker) para obtener una lista de los estilos posibles.

## <a name="crecttrackernormalizehit"></a><a name="normalizehit"></a>CRectTracker::NormalizeHit

Llame a esta función para convertir un identificador potencialmente invertido.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Parámetros

*nHandle*<br/>
Control seleccionado por el usuario.

### <a name="return-value"></a>Valor devuelto

El índice del identificador normalizado.

### <a name="remarks"></a>Observaciones

Cuando `CRectTracker::Track` `CRectTracker::TrackRubberBand` se llama o se llama con la inversión permitida, es posible que el rectángulo se invierta en el eje X, el eje Y o ambos. Cuando esto `HitTest` sucede, devolverá los identificadores que también se invierten con respecto al rectángulo. Esto es inapropiado para dibujar comentarios del cursor porque la retroalimentación depende de la posición de la pantalla del rectángulo, no de la parte de la estructura de datos del rectángulo que se modificará.

## <a name="crecttrackeronchangedrect"></a><a name="onchangedrect"></a>CRectTracker::OnChangedRect

Llamado por el marco de trabajo cada `Track`vez que el rectángulo de seguimiento ha cambiado durante una llamada a .

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Parámetros

*rectOld*<br/>
Contiene las coordenadas antiguas `CRectTracker` del dispositivo del objeto.

### <a name="remarks"></a>Observaciones

En el momento en que se `DrawTrackerRect` llama a esta función, se han eliminado todos los comentarios extraídos con. La implementación predeterminada de esta función no hace nada.

Reemplace esta función cuando desee realizar cualquier acción después de cambiar el tamaño del rectángulo.

## <a name="crecttrackersetcursor"></a><a name="setcursor"></a>CRectTracker::SetCursor

Llame a esta función para cambiar `CRectTracker` la forma del cursor mientras está sobre la región del objeto.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta a la ventana que contiene actualmente el cursor.

*nHitTest*<br/>
Resultados de la prueba de posicionación anterior, del mensaje WM_SETCURSOR.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el hit anterior estaba sobre el rectángulo del rastreador; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta función desde dentro de la función de la ventana que controla el mensaje de WM_SETCURSOR (normalmente `OnSetCursor`).

## <a name="crecttrackertrack"></a><a name="track"></a>CRectTracker::Track

Llame a esta función para mostrar la interfaz de usuario para cambiar el tamaño del rectángulo.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
El objeto de ventana que contiene el rectángulo.

*Punto*<br/>
Coordenadas del dispositivo de la posición actual del ratón en relación con el área de cliente.

*bAllowInvert*<br/>
Si es TRUE, el rectángulo se puede invertir a lo largo del eje X o del eje Y; de lo contrario FALSO.

*pWndClipTo*<br/>
La ventana a la que se recortarán las operaciones de dibujo. Si NULL, *pWnd* se utiliza como rectángulo delimitador.

### <a name="return-value"></a>Valor devuelto

Si se presiona la tecla ESC, se detiene el proceso de seguimiento, el rectángulo almacenado en el rastreador no se modifica y se devuelve 0. Si se confirma el cambio, moviendo el ratón y soltando el botón izquierdo del ratón, la nueva posición y/o tamaño se registra en el rectángulo del rastreador y se devuelve distinto de cero.

### <a name="remarks"></a>Observaciones

Normalmente se llama desde dentro de la `WM_LBUTTONDOWN` función `OnLButtonDown`de la aplicación que controla el mensaje (normalmente ).

Esta función capturará el ratón hasta que el usuario suelte el botón izquierdo del ratón, presione la tecla ESC o presione el botón derecho del ratón. A medida que el usuario mueve el `DrawTrackerRect` cursor `OnChangedRect`del mouse, los comentarios se actualizan llamando y .

Si *bAllowInvert* es TRUE, el rectángulo de seguimiento se puede invertir en el eje X o en el eje Y.

## <a name="crecttrackertrackrubberband"></a><a name="trackrubberband"></a>CRectTracker::TrackRubberBand

Llame a esta función para realizar la selección de bandas de goma.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
El objeto de ventana que contiene el rectángulo.

*Punto*<br/>
Coordenadas del dispositivo de la posición actual del ratón en relación con el área de cliente.

*bAllowInvert*<br/>
Si es TRUE, el rectángulo se puede invertir a lo largo del eje X o del eje Y; de lo contrario FALSO.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el ratón se ha movido y el rectángulo no está vacío; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Normalmente se llama desde dentro de la función de `OnLButtonDown`la aplicación que controla el mensaje de WM_LBUTTONDOWN (normalmente).

Esta función capturará el ratón hasta que el usuario suelte el botón izquierdo del ratón, presione la tecla ESC o presione el botón derecho del ratón. A medida que el usuario mueve el `DrawTrackerRect` cursor `OnChangedRect`del mouse, los comentarios se actualizan llamando y .

El seguimiento se realiza con una selección de tipo banda de goma del mango inferior derecho. Si se permite invertir, el rectángulo se puede dimensionar arrastrando hacia arriba y hacia la izquierda o hacia abajo y hacia la derecha.

## <a name="see-also"></a>Vea también

[EJEMPLO TRACKER de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase COleResizeBar](../../mfc/reference/coleresizebar-class.md)<br/>
[Clase CRect](../../atl-mfc-shared/reference/crect-class.md)
