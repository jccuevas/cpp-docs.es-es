---
title: CSliderCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
ms.openlocfilehash: 8fffdfc002b25fdcd72dcbbf53e7e6c321f55296
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502516"
---
# <a name="csliderctrl-class"></a>CSliderCtrl (clase)

Proporciona la funcionalidad del control deslizante común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Construye un objeto `CSliderCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|Borra la selección actual en un control deslizante.|
|[CSliderCtrl::ClearTics](#cleartics)|Quita las marcas de graduación actuales de un control deslizante.|
|[CSliderCtrl::Create](#create)|Crea un control deslizante y lo adjunta a un `CSliderCtrl` objeto.|
|[CSliderCtrl::CreateEx](#createex)|Crea un control deslizante con los estilos extendidos de Windows especificados y lo `CSliderCtrl` adjunta a un objeto.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Recupera el identificador de una ventana relacionada con el control deslizante en una ubicación determinada.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Recupera el tamaño del canal del control deslizante.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Recupera el tamaño de línea de un control deslizante.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Recupera el número de marcas de graduación de un control deslizante.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Recupera el tamaño de página de un control deslizante.|
|[CSliderCtrl::GetPos](#getpos)|Recupera la posición actual del control deslizante.|
|[CSliderCtrl::GetRange](#getrange)|Recupera las posiciones mínima y máxima de un control deslizante.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Recupera la posición máxima de un control deslizante.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Recupera la posición mínima de un control deslizante.|
|[CSliderCtrl::GetSelection](#getselection)|Recupera el intervalo de la selección actual.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Recupera la longitud del control deslizante en el control de barra de desplazamiento actual.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Recupera el tamaño de la miniatura del control deslizante.|
|[CSliderCtrl::GetTic](#gettic)|Recupera la posición de la marca de graduación especificada.|
|[CSliderCtrl::GetTicArray](#getticarray)|Recupera la matriz de posiciones de la marca de graduación para un control deslizante.|
|[CSliderCtrl::GetTicPos](#getticpos)|Recupera la posición de la marca de graduación especificada, en coordenadas de cliente.|
|[CSliderCtrl::GetToolTips](#gettooltips)|Recupera el identificador del control de información sobre herramientas asignado al control deslizante, si existe.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Asigna una ventana como ventana relacionada para un control deslizante.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Establece el tamaño de línea de un control deslizante.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Establece el tamaño de página de un control deslizante.|
|[CSliderCtrl::SetPos](#setpos)|Establece la posición actual del control deslizante.|
|[CSliderCtrl::SetRange](#setrange)|Establece las posiciones mínima y máxima de un control deslizante.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Establece la posición máxima de un control deslizante.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Establece la posición mínima de un control deslizante.|
|[CSliderCtrl::SetSelection](#setselection)|Establece el intervalo de la selección actual.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Establece la longitud del control deslizante en el control de barra de desplazamiento actual.|
|[CSliderCtrl::SetTic](#settic)|Establece la posición de la marca de graduación especificada.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Establece la frecuencia de las marcas de graduación por incremento del control deslizante.|
|[CSliderCtrl::SetTipSide](#settipside)|Coloca un control ToolTip utilizado por un control TrackBar.|
|[CSliderCtrl::SetToolTips](#settooltips)|Asigna un control de información sobre herramientas a un control deslizante.|

## <a name="remarks"></a>Comentarios

Un "control deslizante" (también conocido como barra de desplazamiento) es una ventana que contiene un control deslizante y unas marcas de graduación opcionales. Cuando el usuario mueve el control deslizante, con el mouse o con las teclas de dirección, el control envía mensajes de notificación para indicar el cambio.

Los controles deslizantes son útiles cuando se desea que el usuario seleccione un valor discreto o un conjunto de valores consecutivos en un intervalo. Por ejemplo, puede usar un control deslizante para permitir al usuario establecer la frecuencia de repetición del teclado moviendo el control deslizante a una marca de graduación determinada.

Este control (y, por `CSliderCtrl` lo tanto, la clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3,51 y versiones posteriores.

El control deslizante se mueve en incrementos que se especifican al crearlo. Por ejemplo, si especifica que el control deslizante debe tener un intervalo de cinco, el control deslizante solo puede ocupar seis posiciones: una posición en el lado izquierdo del control deslizante y una posición para cada incremento del intervalo. Normalmente, cada una de estas posiciones se identifica mediante una marca de graduación.

Puede crear un control deslizante mediante el constructor y `Create` la función miembro `CSliderCtrl`de. Una vez que haya creado un control deslizante, puede utilizar las funciones `CSliderCtrl` miembro de para cambiar muchas de sus propiedades. Entre los cambios que puede realizar se incluyen establecer las posiciones mínima y máxima para el control deslizante, dibujar marcas de graduación, establecer un intervalo de selección y cambiar la posición del control deslizante.

Para obtener más información sobre `CSliderCtrl`el uso de, vea [controles](../../mfc/controls-mfc.md) y [usar CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="clearsel"></a>  CSliderCtrl::ClearSel

Borra la selección actual en un control deslizante.

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*bRedraw*<br/>
Volver a dibujar el marcador. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar una vez desactivada la selección. en caso contrario, el control deslizante no se vuelve a dibujar.

##  <a name="cleartics"></a>  CSliderCtrl::ClearTics

Quita las marcas de graduación actuales de un control deslizante.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*bRedraw*<br/>
Volver a dibujar el marcador. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar una vez que se han borrado las marcas de graduación; en caso contrario, el control deslizante no se vuelve a dibujar.

##  <a name="create"></a>  CSliderCtrl::Create

Crea un control deslizante y lo adjunta a un `CSliderCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control deslizante. Aplique cualquier combinación de [estilos de control deslizante](/windows/win32/Controls/trackbar-control-styles), descrita en el Windows SDK, al control.

*rect*<br/>
Especifica el tamaño y la posición del control deslizante. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Especifica la ventana primaria del control deslizante, normalmente `CDialog`una. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control deslizante.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

En dos pasos `CSliderCtrl` se crea un. En primer lugar, llame al constructor y, `Create`a continuación, llame a, que crea el control deslizante `CSliderCtrl` y lo adjunta al objeto.

Dependiendo de los valores establecidos para *dwStyle*, el control deslizante puede tener una orientación vertical u horizontal. Puede tener marcas de graduación en cualquier lado, en ambos lados o en ninguna de ellas. También se puede usar para especificar un intervalo de valores consecutivos.

Para aplicar estilos de ventana extendidos al control deslizante, llame a [CreateEx](#createex) en lugar de a `Create`.

##  <a name="createex"></a>  CSliderCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia al `CSliderCtrl` objeto.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control deslizante. Aplique cualquier combinación de [estilos de control deslizante](/windows/win32/Controls/trackbar-control-styles), descrita en el Windows SDK, al control.

*rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar los estilos extendidos de Windows, que especifica el **WS_EX_** de estilo extendido de Windows.

##  <a name="csliderctrl"></a>  CSliderCtrl::CSliderCtrl

Construye un objeto `CSliderCtrl`.

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>  CSliderCtrl::GetBuddy

Recupera el identificador de una ventana relacionada con el control deslizante en una ubicación determinada.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*fLocation*<br/>
Valor booleano que indica cuál de los dos identificadores de ventana de Buddy se deben recuperar. Puede presentar uno de los siguientes valores:

- TRUE recupera el identificador del Buddy situado a la izquierda del control deslizante. Si el control deslizante usa el estilo TBS_VERT, el mensaje recuperará el colega situado encima del control deslizante.

- FALSE recupera el identificador del Buddy situado a la derecha del control deslizante. Si el control deslizante usa el estilo TBS_VERT, el mensaje recuperará el amigo debajo del control deslizante.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana relacionada en la ubicación especificada por *FLOCATION*, o null si no existe ninguna ventana relacionada en esa ubicación.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy), tal y como se describe en el Windows SDK. Para obtener una descripción de los estilos de control deslizante, vea [estilos de control TrackBar](/windows/win32/Controls/trackbar-control-styles) en el Windows SDK.

##  <a name="getchannelrect"></a>  CSliderCtrl::GetChannelRect

Recupera el tamaño y la posición del rectángulo delimitador del canal de un control deslizante.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Un puntero a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que contiene el tamaño y la posición del rectángulo delimitador del canal cuando la función devuelve.

### <a name="remarks"></a>Comentarios

El canal es el área sobre la que se mueve el control deslizante y que contiene el resaltado cuando se selecciona un intervalo.

##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize

Recupera el tamaño de la línea para un control deslizante.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño de una línea para el control deslizante.

### <a name="remarks"></a>Comentarios

El tamaño de línea afecta a la cantidad de movimiento del control deslizante para las notificaciones TB_LINEUP y TB_LINEDOWN. La configuración predeterminada para el tamaño de línea es 1.

##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics

Recupera el número de marcas de graduación de un control deslizante.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Valor devuelto

El número de marcas de graduación en el control deslizante.

##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize

Recupera el tamaño de la página para un control deslizante.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño de una página para el control deslizante.

### <a name="remarks"></a>Comentarios

El tamaño de página afecta a la cantidad de movimiento del control deslizante para las notificaciones TB_PAGEUP y TB_PAGEDOWN.

##  <a name="getpos"></a>  CSliderCtrl::GetPos

Recupera la posición actual del control deslizante en un control deslizante.

```
int GetPos() const;
```

### <a name="return-value"></a>Valor devuelto

Posición actual.

##  <a name="getrange"></a>  CSliderCtrl::GetRange

Recupera las posiciones máxima y mínima del control deslizante en un control deslizante.

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Referencia a un entero que recibe la posición mínima.

*Nmáx.*<br/>
Referencia a un entero que recibe la posición máxima.

### <a name="remarks"></a>Comentarios

Esta función copia los valores en los enteros a los que hace referencia *nmín.* y *nmáx.* .

##  <a name="getrangemax"></a>  CSliderCtrl::GetRangeMax

Recupera la posición máxima del control deslizante en un control deslizante.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valor devuelto

Posición máxima del control.

##  <a name="getrangemin"></a>  CSliderCtrl::GetRangeMin

Recupera la posición mínima del control deslizante en un control deslizante.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valor devuelto

Posición mínima del control.

##  <a name="getselection"></a>  CSliderCtrl::GetSelection

Recupera las posiciones inicial y final de la selección actual en un control deslizante.

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Referencia a un entero que recibe la posición inicial de la selección actual.

*Nmáx.*<br/>
Referencia a un entero que recibe la posición final de la selección actual.

##  <a name="getthumblength"></a>  CSliderCtrl::GetThumbLength

Recupera la longitud del control deslizante en el control de barra de desplazamiento actual.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud del control deslizante, en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [TBM_GETTHUMBLENGTH](/windows/win32/Controls/tbm-getthumblength) , que se describe en el Windows SDK.

##  <a name="getthumbrect"></a>  CSliderCtrl::GetThumbRect

Recupera el tamaño y la posición del rectángulo delimitador para el control deslizante (Thumb) en un control deslizante.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Un puntero a un `CRect` objeto que contiene el rectángulo delimitador del control deslizante cuando la función devuelve.

##  <a name="gettic"></a>  CSliderCtrl::GetTic

Recupera la posición de una marca de paso en un control deslizante.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parámetros

*nTic*<br/>
Índice de base cero que identifica una marca de graduación.

### <a name="return-value"></a>Valor devuelto

Posición de la marca de graduación especificada o-1 si *nTic* no especifica un índice válido.

##  <a name="getticarray"></a>  CSliderCtrl::GetTicArray

Recupera la dirección de la matriz que contiene las posiciones de las marcas de graduación de un control deslizante.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Valor devuelto

Dirección de la matriz que contiene las posiciones de las marcas de graduación del control deslizante.

##  <a name="getticpos"></a>  CSliderCtrl::GetTicPos

Recupera la posición física actual de una marca de paso en un control deslizante.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parámetros

*nTic*<br/>
Índice de base cero que identifica una marca de graduación.

### <a name="return-value"></a>Valor devuelto

Posición física, en coordenadas de cliente, de la marca de graduación especificada o-1 si *nTic* no especifica un índice válido.

##  <a name="gettooltips"></a>  CSliderCtrl::GetToolTips

Recupera el identificador del control de información sobre herramientas asignado al control deslizante, si existe.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) o null si la información sobre herramientas no está en uso. Si el control deslizante no usa el estilo TBS_TOOLTIPS, el valor devuelto es NULL.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips), tal y como se describe en el Windows SDK. Tenga en cuenta que esta función miembro `CToolTipCtrl` devuelve un objeto en lugar de un identificador de un control.

Para obtener una descripción de los estilos de control deslizante, vea [estilos de control TrackBar](/windows/win32/Controls/trackbar-control-styles) en el Windows SDK.

##  <a name="setbuddy"></a>  CSliderCtrl::SetBuddy

Asigna una ventana como ventana relacionada para un control deslizante.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWndBuddy*<br/>
Un puntero a un `CWnd` objeto que se establecerá como el Buddy del control deslizante.

*fLocation*<br/>
Valor que especifica la ubicación en la que se va a mostrar la ventana relacionada. Este valor puede ser uno de los siguientes:

- TRUE el amigo aparecerá a la izquierda del control TrackBar si el control TrackBar usa el estilo TBS_HORZ. Si la barra de mandos usa el estilo TBS_VERT, el amigo aparece sobre el control TrackBar.

- FALSE el Buddy aparecerá a la derecha del control TrackBar si el control TrackBar usa el estilo TBS_HORZ. Si la barra de mandos usa el estilo TBS_VERT, el amigo aparece debajo del control TrackBar.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que se asignó previamente al control deslizante en esa ubicación.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy), tal y como se describe en el Windows SDK. Tenga en cuenta que esta función miembro utiliza punteros a `CWnd` objetos, en lugar de identificadores de ventana para el valor devuelto y el parámetro.

Para obtener una descripción de los estilos de control deslizante, vea [estilos de control TrackBar](/windows/win32/Controls/trackbar-control-styles) en el Windows SDK.

##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize

Establece el tamaño de la línea para un control deslizante.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nSize*<br/>
Nuevo tamaño de línea del control deslizante.

### <a name="return-value"></a>Valor devuelto

Tamaño de línea anterior.

### <a name="remarks"></a>Comentarios

El tamaño de línea afecta a la cantidad de movimiento del control deslizante para las notificaciones TB_LINEUP y TB_LINEDOWN.

##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize

Establece el tamaño de la página para un control deslizante.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nSize*<br/>
Nuevo tamaño de página del control deslizante.

### <a name="return-value"></a>Valor devuelto

Tamaño de página anterior.

### <a name="remarks"></a>Comentarios

El tamaño de página afecta a la cantidad de movimiento del control deslizante para las notificaciones TB_PAGEUP y TB_PAGEDOWN.

##  <a name="setpos"></a>  CSliderCtrl::SetPos

Establece la posición actual del control deslizante en un control deslizante.

```
void SetPos(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica la nueva posición del control deslizante.

##  <a name="setrange"></a>  CSliderCtrl::SetRange

Establece el intervalo (posiciones mínima y máxima) para el control deslizante en un control deslizante.

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Posición mínima del control deslizante.

*Nmáx.*<br/>
Posición máxima del control deslizante.

*bRedraw*<br/>
Marca de volver a dibujar. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar una vez establecido el intervalo; en caso contrario, el control deslizante no se vuelve a dibujar.

##  <a name="setrangemax"></a>  CSliderCtrl::SetRangeMax

Establece el intervalo máximo para el control deslizante en un control deslizante.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*Nmáx.*<br/>
Posición máxima del control deslizante.

*bRedraw*<br/>
Marca de volver a dibujar. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar una vez establecido el intervalo; en caso contrario, el control deslizante no se vuelve a dibujar.

##  <a name="setrangemin"></a>  CSliderCtrl::SetRangeMin

Establece el intervalo mínimo para el control deslizante en un control deslizante.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Posición mínima del control deslizante.

*bRedraw*<br/>
Marca de volver a dibujar. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar una vez establecido el intervalo; en caso contrario, el control deslizante no se vuelve a dibujar.

##  <a name="setselection"></a>  CSliderCtrl::SetSelection

Establece las posiciones inicial y final de la selección actual en un control deslizante.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Posición inicial del control deslizante.

*Nmáx.*<br/>
Posición final del control deslizante.

##  <a name="setthumblength"></a>  CSliderCtrl::SetThumbLength

Establece la longitud del control deslizante en el control de barra de desplazamiento actual.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*nLength*|de Longitud del control deslizante, en píxeles.|

### <a name="remarks"></a>Comentarios

Este método requiere que el control TrackBar se establezca en el estilo [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) .

Este método envía el mensaje [TBM_SETTHUMBLENGTH](/windows/win32/Controls/tbm-setthumblength) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_sliderCtrl`la variable,, que se utiliza para tener acceso al control TrackBar actual. En el ejemplo también se define una `thumbLength`variable,, que se utiliza para almacenar la longitud predeterminada del componente Thumb del control TrackBar. Estas variables se usan en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el componente Thumb del control TrackBar en el doble de su longitud predeterminada.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>  CSliderCtrl::SetTic

Establece la posición de una marca de paso en un control deslizante.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parámetros

*nTic*<br/>
Posición de la marca de graduación. Este parámetro debe especificar un valor positivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se establece la marca de graduación; de lo contrario, es 0.

##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq

Establece la frecuencia con la que se muestran las marcas de graduación en un control deslizante.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parámetros

*nFreq*<br/>
Frecuencia de las marcas de graduación.

### <a name="remarks"></a>Comentarios

Por ejemplo, si la frecuencia se establece en 2, se muestra una marca de graduación para cada otro incremento en el intervalo del control deslizante. La configuración predeterminada de la frecuencia es 1 (es decir, cada incremento del intervalo está asociado a una marca de graduación).

Debe crear el control con el estilo TBS_AUTOTICKS para usar esta función. Para obtener más información, vea [CSliderCtrl:: Create](#create).

##  <a name="settipside"></a>  CSliderCtrl::SetTipSide

Coloca un control ToolTip utilizado por un control TrackBar.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parámetros

*nLocation*<br/>
Valor que representa la ubicación en la que se va a mostrar el control ToolTip. Para obtener una lista de los valores posibles, vea el mensaje de Win32 [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside), como se describe en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Valor que representa la ubicación anterior del control ToolTip. El valor devuelto es igual a uno de los valores posibles de *nubicación*.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 TBM_SETTIPSIDE, tal y como se describe en el Windows SDK. Los controles deslizantes que utilizan el estilo TBS_TOOLTIPS muestran información sobre herramientas. Para obtener una descripción de los estilos de control deslizante, vea [estilos de control TrackBar](/windows/win32/Controls/trackbar-control-styles) en el Windows SDK.

##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips

Asigna un control de información sobre herramientas a un control deslizante.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parámetros

*pWndTip*<br/>
Un puntero a un objeto [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) que contiene la información sobre herramientas que se va a utilizar con el control deslizante.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips), tal y como se describe en el Windows SDK. Cuando se crea un control deslizante con el estilo TBS_TOOLTIPS, se crea un control ToolTip predeterminado que aparece junto al control deslizante, que muestra la posición actual del control deslizante. Para obtener una descripción de los estilos de control deslizante, vea [estilos de control TrackBar](/windows/win32/Controls/trackbar-control-styles) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl (clase)](../../mfc/reference/cprogressctrl-class.md)
