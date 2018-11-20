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
ms.openlocfilehash: c82b06903f0705a79a15b263b1dbdfc6aee4c8ca
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176515"
---
# <a name="crecttracker-class"></a>CRectTracker (clase)

Permite que un elemento para mostrar, mover y cambiar el tamaño de distintas maneras.

## <a name="syntax"></a>Sintaxis

```
class CRectTracker
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CRectTracker::CRectTracker](#crecttracker)|Construye un objeto `CRectTracker`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|Se llama cuando se cambia el tamaño del rectángulo.|
|[CRectTracker::Draw](#draw)|Representa el rectángulo.|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|Llamado cuando se dibuja el borde de un `CRectTracker` objeto.|
|[CRectTracker::GetHandleMask](#gethandlemask)|Se llama para obtener la máscara de un `CRectTracker` controladores de tamaño del elemento.|
|[CRectTracker::GetTrueRect](#gettruerect)|Devuelve el ancho y alto del rectángulo, incluidos los controladores de tamaño.|
|[CRectTracker:: HitTest](#hittest)|Devuelve la posición actual del cursor relacionados con la `CRectTracker` objeto.|
|[CRectTracker::NormalizeHit](#normalizehit)|Normaliza un código de prueba de posicionamiento.|
|[CRectTracker::OnChangedRect](#onchangedrect)|Se llama cuando se cambia el tamaño o mover el rectángulo.|
|[CRectTracker:: SetCursor](#setcursor)|Establece el cursor, dependiendo de su posición en el rectángulo.|
|[CRectTracker::Track](#track)|Permite al usuario manipular el rectángulo.|
|[CRectTracker:: TrackRubberBand](#trackrubberband)|Permite al usuario "goma" de la selección.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|Determina el tamaño de los controladores de tamaño.|
|[CRectTracker::m_nStyle](#m_nstyle)|Style(s) actual de la herramienta de seguimiento.|
|[CRectTracker::m_rect](#m_rect)|Posición actual (en píxeles) del rectángulo.|
|[CRectTracker::m_sizeMin](#m_sizemin)|Determina el alto y ancho mínimos del rectángulo.|

## <a name="remarks"></a>Comentarios

`CRectTracker` no tiene una clase base.

Aunque la `CRectTracker` clase está diseñada para permitir al usuario interactuar con elementos OLE mediante una interfaz gráfica, su uso no está restringido a aplicaciones habilitadas para OLE. Se puede usar en cualquier lugar que se requiere una interfaz de usuario de este tipo.

`CRectTracker` los bordes pueden ser sólidos o líneas de puntos. El elemento puede ser con un borde sombreado o superpuesto con un patrón de sombreado para indicar distintos Estados del elemento. Puede colocar ocho controladores de tamaño en el exterior o en el interior borde del elemento. (Para obtener una explicación de los controladores de tamaño, vea [GetHandleMask](#gethandlemask).) Por último, un `CRectTracker` le permite cambiar la orientación de un elemento durante el cambio de tamaño.

Para usar `CRectTracker`, construir un `CRectTracker` de objetos y especificar qué estados de visualización se inicializan. A continuación, puede usar esta interfaz para proporcionar al usuario información visual sobre el estado actual del elemento OLE asociado con el `CRectTracker` objeto.

Para obtener más información sobre el uso de `CRectTracker`, consulte el artículo [rastreadores](../../mfc/trackers.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CRectTracker`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

##  <a name="adjustrect"></a>  CRectTracker::AdjustRect

Lo llama el marco de trabajo cuando se cambia el tamaño del rectángulo de seguimiento mediante el uso de un controlador de tamaño.

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*nHandle*<br/>
Índice del controlador que se utiliza.

*lpRect*<br/>
Puntero al tamaño actual del rectángulo. (El tamaño de un rectángulo viene dado por su alto y ancho).

### <a name="remarks"></a>Comentarios

El comportamiento predeterminado de esta función permite la orientación del rectángulo cambiar solo cuando `Track` y `TrackRubberBand` se llaman con invertir permitido.

Reemplace esta función para controlar el ajuste del rectángulo de seguimiento durante una operación de arrastre. Un método consiste en ajustar las coordenadas especificadas por *lpRect* antes de devolver.

Las características especiales que no son directamente compatibles con `CRectTracker`, como complemento a la cuadrícula o keep--relación de aspecto, puede implementarse mediante la invalidación de esta función.

##  <a name="crecttracker"></a>  CRectTracker::CRectTracker

Crea e inicializa un `CRectTracker` objeto.

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
Especifica el estilo de la `CRectTracker` objeto. Se admiten los siguientes estilos:

- `CRectTracker::solidLine` Utilice una línea sólida para el borde del rectángulo.

- `CRectTracker::dottedLine` Usar una línea de puntos del borde del rectángulo.

- `CRectTracker::hatchedBorder` Use un patrón de sombreado para el borde del rectángulo.

- `CRectTracker::resizeInside` Controladores que se encuentra dentro del rectángulo de tamaño.

- `CRectTracker::resizeOutside` Controladores que se encuentra fuera del rectángulo de tamaño.

- `CRectTracker::hatchInside` Generan patrón abarca todo el rectángulo.

### <a name="remarks"></a>Comentarios

El constructor predeterminado inicializa el `CRectTracker` objeto con los valores de *lpSrcRect* e inicializa otros tamaños de los valores predeterminados del sistema. Si el objeto se crea sin parámetros, el `m_rect` y `m_nStyle` los miembros de datos están sin inicializados.

##  <a name="draw"></a>  CRectTracker::Draw

Llame a esta función para dibujar el rectángulo exteriores líneas y región interna.

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto de dispositivo en el que se va a dibujar.

### <a name="remarks"></a>Comentarios

El estilo de la herramienta de seguimiento determina cómo se realiza el dibujo. Vea el constructor para `CRectTracker` para obtener más información sobre los estilos disponibles.

##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect

Lo llama el marco de trabajo cada vez que ha cambiado la posición de la herramienta de seguimiento mientras dentro de la `Track` o `TrackRubberBand` función miembro.

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Puntero a la `RECT` que contiene el rectángulo que se va a dibujar.

*pWndClipTo*<br/>
Puntero a la ventana que se usará en el rectángulo de recorte.

*pDC*<br/>
Puntero al contexto de dispositivo en el que se va a dibujar.

*conquistado*<br/>
Puntero a la ventana en la que se producirá el dibujo.

### <a name="remarks"></a>Comentarios

La implementación predeterminada realiza una llamada a `CDC::DrawFocusRect`, que dibuja un rectángulo de puntos.

Reemplace esta función para proporcionar comentarios diferente durante la operación de seguimiento.

##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask

El marco de trabajo llama a esta función miembro para recuperar la máscara para controladores de tamaño de un rectángulo.

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>Valor devuelto

La máscara de un `CRectTracker` controladores de tamaño del elemento.

### <a name="remarks"></a>Comentarios

Los controladores de tamaño aparecen en los lados y las esquinas del rectángulo y permiten al usuario controlar la forma y tamaño del rectángulo.

Un rectángulo tiene 8 controladores de tamaño con el número 0-7. Cada controlador de tamaño se representa mediante un poco en la máscara; el valor de ese bit es 2 ^ *n*, donde *n* es el número de identificador de cambio de tamaño. Bits 0-3 se corresponden con los controladores de tamaño de la esquina, comenzando en la parte superior izquierda de mover hacia la derecha. Desde la parte superior agujas del reloj de controladores de tamaño de bits se corresponden con el lado del 4 al 7. Controla el cambio de tamaño de un rectángulo y sus correspondientes cambiar el tamaño de los números de identificador y los valores, se muestra en la siguiente ilustración:

![Cambiar el tamaño de los números de asas](../../mfc/reference/media/vc35dp1.gif "números de asas de cambio de tamaño")

La implementación predeterminada de `GetHandleMask` devuelve la máscara de bits para que aparezcan los manipuladores de cambio de tamaño. Si el bit único está activado, se dibujará el controlador de tamaño correspondiente.

Reemplace esta función miembro para ocultar o mostrar que controladores de tamaño indicado.

##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect

Llame a esta función para recuperar las coordenadas del rectángulo.

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>Parámetros

*lpTrueRect*<br/>
Puntero a la `RECT` coordina la estructura que contiene el dispositivo de la `CRectTracker` objeto.

### <a name="remarks"></a>Comentarios

Las dimensiones del rectángulo incluyen el alto y ancho de los controladores de tamaño situado en el borde exterior. Al volver, *lpTrueRect* siempre es un rectángulo normalizado en coordenadas de dispositivo.

##  <a name="hittest"></a>  CRectTracker:: HitTest

Llame a esta función para averiguar si el usuario ha tomado un controlador de tamaño.

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>Parámetros

*punto*<br/>
El punto en coordenadas de dispositivo, para probar.

### <a name="return-value"></a>Valor devuelto

El valor devuelto se basa en el tipo enumerado `CRectTracker::TrackerHit` y puede tener uno de los siguientes valores:

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight` 1

- `CRectTracker::hitBottomRight` 2

- `CRectTracker::hitBottomLeft` 3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight` 5

- `CRectTracker::hitBottom` 6

- `CRectTracker::hitLeft` 7

- `CRectTracker::hitMiddle` 8

##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize

El tamaño, en píxeles, de la `CRectTracker` controladores de tamaño.

```
int m_nHandleSize;
```

### <a name="remarks"></a>Comentarios

Se inicializa con el valor predeterminado del sistema.

##  <a name="m_rect"></a>  CRectTracker::m_rect

La posición actual del rectángulo en coordenadas de cliente (píxeles).

```
CRect m_rect;
```

##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin

El tamaño mínimo del rectángulo.

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Comentarios

Ambos valores predeterminados, `cx` y `cy`, se calculan a partir del valor del sistema predeterminado para el ancho del borde. Este miembro de datos se usa únicamente por la `AdjustRect` función miembro.

##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle

Estilo actual del rectángulo.

```
UINT m_nStyle;
```

### <a name="remarks"></a>Comentarios

Consulte [CRectTracker::CRectTracker](#crecttracker) para obtener una lista de posibles estilos.

##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit

Llame a esta función para convertir un identificador potencialmente invertido.

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>Parámetros

*nHandle*<br/>
Identificador seleccionado por el usuario.

### <a name="return-value"></a>Valor devuelto

El índice del identificador normalizado.

### <a name="remarks"></a>Comentarios

Cuando `CRectTracker::Track` o `CRectTracker::TrackRubberBand` se llama con invertir permitido, es posible que el rectángulo que se va a invertir en el eje x, el eje y o ambos. Cuando esto sucede, `HitTest` devolverá los identificadores que también están invertidos con respecto al rectángulo. Esto es apropiado para dibujo comentarios del cursor porque depende de los comentarios en la posición de pantalla del rectángulo, no la parte de la estructura de datos del rectángulo que se va a modificar.

##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect

Lo llama el marco de trabajo siempre que el rectángulo rastreador ha cambiado durante una llamada a `Track`.

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>Parámetros

*rectOld*<br/>
Contiene las coordenadas de dispositivo antiguo de la `CRectTracker` objeto.

### <a name="remarks"></a>Comentarios

En el momento en los que se llama a esta función, todos los comentarios que se dibuja con `DrawTrackerRect` se ha quitado. La implementación predeterminada de esta función no hace nada.

Reemplace esta función cuando desea realizar acciones después de que ha cambiado el tamaño del rectángulo.

##  <a name="setcursor"></a>  CRectTracker:: SetCursor

Llame a esta función para cambiar la forma del cursor mientras está sobre el `CRectTracker` región del objeto.

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
Apunta a la ventana que contiene actualmente el cursor.

*nHitTest*<br/>
Resultados de la prueba de posicionamiento anterior, desde el mensaje WM_SETCURSOR.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el posicionamiento anterior era el rectángulo tracker; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función desde dentro de la función de la ventana que controla el mensaje WM_SETCURSOR (normalmente `OnSetCursor`).

##  <a name="track"></a>  CRectTracker::Track

Llame a esta función para mostrar la interfaz de usuario para cambiar el tamaño del rectángulo.

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
El objeto de ventana que contiene el rectángulo.

*punto*<br/>
Coordenadas de dispositivo de la posición actual del mouse relativa al área de cliente.

*bAllowInvert*<br/>
Si es TRUE, se puede invertir el rectángulo a lo largo del eje x o del eje y; en caso contrario, FALSE.

*pWndClipTo*<br/>
La ventana que las operaciones de dibujo se ajustarán a. Si es NULL, *conquistado* se utiliza como el rectángulo de recorte.

### <a name="return-value"></a>Valor devuelto

Si se presiona la tecla ESC, se detiene el proceso de seguimiento, el rectángulo que se almacenan en la herramienta de seguimiento no se modifica y se devuelve 0. Si el cambio se confirma, al mover el mouse y suelte el botón primario del mouse, la nueva posición o el tamaño se registra en el rectángulo de la herramienta de seguimiento y se devuelve es distinto de cero.

### <a name="remarks"></a>Comentarios

Normalmente, esto se llama desde dentro de la función de la aplicación que controla la `WM_LBUTTONDOWN` mensaje (normalmente `OnLButtonDown`).

Esta función capturará el mouse hasta que el usuario suelta el botón primario del mouse, presiona la tecla ESC o presiona el botón secundario del mouse. Cuando el usuario mueve el cursor del mouse, los comentarios se actualizan mediante una llamada a `DrawTrackerRect` y `OnChangedRect`.

Si *bAllowInvert* es TRUE, el rectángulo de seguimiento se puede invertir en el eje x o del eje y.

##  <a name="trackrubberband"></a>  CRectTracker:: TrackRubberBand

Llame a esta función para realizar la selección de banda de goma.

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
El objeto de ventana que contiene el rectángulo.

*punto*<br/>
Coordenadas de dispositivo de la posición actual del mouse relativa al área de cliente.

*bAllowInvert*<br/>
Si es TRUE, se puede invertir el rectángulo a lo largo del eje x o del eje y; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha movido el mouse y el rectángulo no está vacío; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Normalmente, se llama desde dentro de la función de la aplicación que controla el mensaje WM_LBUTTONDOWN (normalmente `OnLButtonDown`).

Esta función capturará el mouse hasta que el usuario suelta el botón primario del mouse, presiona la tecla ESC o presiona el botón secundario del mouse. Cuando el usuario mueve el cursor del mouse, los comentarios se actualizan mediante una llamada a `DrawTrackerRect` y `OnChangedRect`.

Seguimiento se realiza con una selección de tipo de banda de goma en el controlador inferior derecha. Si se permite si invierte, el rectángulo puede ajustarse arrastrando ya sea de y a la izquierda o hacia abajo y la derecha.

## <a name="see-also"></a>Vea también

[Ejemplo MFC TRACKER](../../visual-cpp-samples.md)<br/>
[Ejemplo de MFC DRAWCLI](../../visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar (clase)](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)
