---
title: Clase CSliderCtrl
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
ms.openlocfilehash: 24e1cb18f979d1144f15cf6ffedc6cace5f5361e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318211"
---
# <a name="csliderctrl-class"></a>Clase CSliderCtrl

Proporciona la funcionalidad del control deslizante común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Construye un objeto `CSliderCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|Borra la selección actual en un control deslizante.|
|[CSliderCtrl::ClearTics](#cleartics)|Elimina las marcas de graduación actuales de un control deslizante.|
|[CSliderCtrl::Crear](#create)|Crea un control deslizante y `CSliderCtrl` lo asocia a un objeto.|
|[CSliderCtrl::CreateEx](#createex)|Crea un control deslizante con los estilos extendidos `CSliderCtrl` de Windows especificados y lo asocia a un objeto.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Recupera el identificador de una ventana de compañero de control deslizante en una ubicación determinada.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Recupera el tamaño del canal del control deslizante.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Recupera el tamaño de línea de un control deslizante.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Recupera el número de marcas de graduación en un control deslizante.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Recupera el tamaño de página de un control deslizante.|
|[CSliderCtrl::GetPos](#getpos)|Recupera la posición actual del control deslizante.|
|[CSliderCtrl::GetRange](#getrange)|Recupera las posiciones mínima y máxima de un control deslizante.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Recupera la posición máxima de un control deslizante.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Recupera la posición mínima de un control deslizante.|
|[CSliderCtrl::GetSelection](#getselection)|Recupera el rango de la selección actual.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Recupera la longitud del control deslizante en el control de barra de seguimiento actual.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Recupera el tamaño del pulgar del control deslizante.|
|[CSliderCtrl::GetTic](#gettic)|Recupera la posición de la marca de graduación especificada.|
|[CSliderCtrl::GetTicArray](#getticarray)|Recupera la matriz de posiciones de marcas de graduación para un control deslizante.|
|[CSliderCtrl::GetTicPos](#getticpos)|Recupera la posición de la marca de graduación especificada, en coordenadas de cliente.|
|[CSliderCtrl::GetToolTips](#gettooltips)|Recupera el identificador del control de información sobre herramientas asignado al control deslizante, si existe.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Asigna una ventana como la ventana de compañero para un control deslizante.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Establece el tamaño de línea de un control deslizante.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Establece el tamaño de página de un control deslizante.|
|[CSliderCtrl::SetPos](#setpos)|Establece la posición actual del control deslizante.|
|[CSliderCtrl::SetRange](#setrange)|Establece las posiciones mínima y máxima de un control deslizante.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Establece la posición máxima de un control deslizante.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Establece la posición mínima de un control deslizante.|
|[CSliderCtrl::SetSelection](#setselection)|Establece el rango de la selección actual.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Establece la longitud del control deslizante en el control de barra de seguimiento actual.|
|[CSliderCtrl::SetTic](#settic)|Establece la posición de la marca de graduación especificada.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Establece la frecuencia de las marcas de graduación por incremento de control deslizante.|
|[CSliderCtrl::SetTipSide](#settipside)|Coloca un control de información sobre herramientas utilizado por un control de barra de seguimiento.|
|[CSliderCtrl::SetToolTips](#settooltips)|Asigna un control de información sobre herramientas a un control deslizante.|

## <a name="remarks"></a>Observaciones

Un "control deslizante" (también conocido como barra de seguimiento) es una ventana que contiene un control deslizante y marcas de graduación opcionales. Cuando el usuario mueve el control deslizante, utilizando el mouse o las teclas de dirección, el control envía mensajes de notificación para indicar el cambio.

Los controles deslizantes son útiles cuando desea que el usuario seleccione un valor discreto o un conjunto de valores consecutivos en un intervalo. Por ejemplo, puede utilizar un control deslizante para permitir al usuario establecer la velocidad de repetición del teclado moviendo el control deslizante a una marca de graduación determinada.

Este control (y, por lo tanto, la `CSliderCtrl` clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

El control deslizante se mueve en incrementos que especifique al crearlo. Por ejemplo, si especifica que el control deslizante debe tener un rango de cinco, el control deslizante solo puede ocupar seis posiciones: una posición en el lado izquierdo del control deslizante y una posición para cada incremento en el intervalo. Normalmente, cada una de estas posiciones se identifica mediante una marca de graduación.

Crear un control deslizante mediante `Create` el constructor `CSliderCtrl`y la función miembro de . Una vez que haya creado un control `CSliderCtrl` deslizante, puede usar funciones miembro para cambiar muchas de sus propiedades. Los cambios que puede realizar incluyen la configuración de las posiciones mínima y máxima para el control deslizante, el dibujo de marcas de graduación, el establecimiento de un rango de selección y la reposición del control deslizante.

Para obtener más `CSliderCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y [uso de CSliderCtrl](../../mfc/using-csliderctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSliderCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="csliderctrlclearsel"></a><a name="clearsel"></a>CSliderCtrl::ClearSel

Borra la selección actual en un control deslizante.

```
void ClearSel(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*bRedraw*<br/>
Vuelva a dibujar la bandera. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar después de borrar la selección; de lo contrario, el control deslizante no se vuelve a dibujar.

## <a name="csliderctrlcleartics"></a><a name="cleartics"></a>CSliderCtrl::ClearTics

Elimina las marcas de graduación actuales de un control deslizante.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*bRedraw*<br/>
Vuelva a dibujar la bandera. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar después de borrar las marcas de graduación; de lo contrario, el control deslizante no se vuelve a dibujar.

## <a name="csliderctrlcreate"></a><a name="create"></a>CSliderCtrl::Crear

Crea un control deslizante y `CSliderCtrl` lo asocia a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control deslizante. Aplique cualquier combinación de estilos de [control deslizante,](/windows/win32/Controls/trackbar-control-styles)que se describen en el Windows SDK, al control.

*Rect*<br/>
Especifica el tamaño y la posición del control deslizante. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control `CDialog`deslizante, normalmente un archivo . No debe ser NULL.

*nID*<br/>
Especifica el identificador del control deslizante.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Se construye `CSliderCtrl` un en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CSliderCtrl` llame a , que crea el control deslizante y lo adjunta al objeto.

Dependiendo de los valores establecidos para *dwStyle*, el control deslizante puede tener una orientación vertical u horizontal. Puede tener marcas de graduación a ambos lados, ambos lados o ninguno de los dos. También se puede utilizar para especificar un rango de valores consecutivos.

Para aplicar estilos de ventana extendidos al `Create`control deslizante, llame a [CreateEx](#createex) en lugar de .

## <a name="csliderctrlcreateex"></a><a name="createex"></a>CSliderCtrl::CreateEx

Crea un control (una ventana secundaria) `CSliderCtrl` y lo asocia con el objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control deslizante. Aplique cualquier combinación de estilos de [control deslizante,](/windows/win32/Controls/trackbar-control-styles)que se describen en el Windows SDK, al control.

*Rect*<br/>
Una referencia a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa en lugar de [Crear](#create) para aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

## <a name="csliderctrlcsliderctrl"></a><a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl

Construye un objeto `CSliderCtrl`.

```
CSliderCtrl();
```

## <a name="csliderctrlgetbuddy"></a><a name="getbuddy"></a>CSliderCtrl::GetBuddy

Recupera el identificador de una ventana de compañero de control deslizante en una ubicación determinada.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*fLocation*<br/>
Valor booleano que indica cuál de los dos identificadores de ventana de compañero se va a recuperar. Puede ser uno de los siguientes valores:

- TRUE Recupera el identificador del compañero a la izquierda del control deslizante. Si el control deslizante utiliza el estilo TBS_VERT, el mensaje recuperará al amigo encima del control deslizante.

- FALSE Recupera el identificador del compañero a la derecha del control deslizante. Si el control deslizante utiliza el estilo TBS_VERT, el mensaje recuperará al amigo debajo del control deslizante.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana de compañero en la ubicación especificada por *fLocation*, o NULL si no existe ninguna ventana de amigo en esa ubicación.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_GETBUDDY](/windows/win32/Controls/tbm-getbuddy), como se describe en el Windows SDK. Para obtener una descripción de los estilos de control deslizante, consulte [Estilos](/windows/win32/Controls/trackbar-control-styles) de control de barra de seguimiento en el Windows SDK.

## <a name="csliderctrlgetchannelrect"></a><a name="getchannelrect"></a>CSliderCtrl::GetChannelRect

Recupera el tamaño y la posición del rectángulo delimitador para el canal de un control deslizante.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Puntero a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el tamaño y la posición del rectángulo delimitador del canal cuando se devuelve la función.

### <a name="remarks"></a>Observaciones

El canal es el área sobre la que se mueve el control deslizante y que contiene el resaltado cuando se selecciona un rango.

## <a name="csliderctrlgetlinesize"></a><a name="getlinesize"></a>CSliderCtrl::GetLineSize

Recupera el tamaño de la línea de un control deslizante.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de una línea para el control deslizante.

### <a name="remarks"></a>Observaciones

El tamaño de línea afecta a la cantidad que se mueve el control deslizante para las notificaciones TB_LINEUP y TB_LINEDOWN. La configuración predeterminada para el tamaño de línea es 1.

## <a name="csliderctrlgetnumtics"></a><a name="getnumtics"></a>CSliderCtrl::GetNumTics

Recupera el número de marcas de graduación en un control deslizante.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Valor devuelto

El número de marcas de graduación en el control deslizante.

## <a name="csliderctrlgetpagesize"></a><a name="getpagesize"></a>CSliderCtrl::GetPageSize

Recupera el tamaño de la página para un control deslizante.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de una página para el control deslizante.

### <a name="remarks"></a>Observaciones

El tamaño de página afecta a la cantidad que se mueve el control deslizante para las notificaciones TB_PAGEUP y TB_PAGEDOWN.

## <a name="csliderctrlgetpos"></a><a name="getpos"></a>CSliderCtrl::GetPos

Recupera la posición actual del control deslizante en un control deslizante.

```
int GetPos() const;
```

### <a name="return-value"></a>Valor devuelto

Posición actual.

## <a name="csliderctrlgetrange"></a><a name="getrange"></a>CSliderCtrl::GetRange

Recupera las posiciones máxima y mínima del control deslizante en un control deslizante.

```
void GetRange(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Referencia a un entero que recibe la posición mínima.

*nMax*<br/>
Referencia a un entero que recibe la posición máxima.

### <a name="remarks"></a>Observaciones

Esta función copia los valores en los enteros a los que hacen referencia *nMin* y *nMax*.

## <a name="csliderctrlgetrangemax"></a><a name="getrangemax"></a>CSliderCtrl::GetRangeMax

Recupera la posición máxima del control deslizante en un control deslizante.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valor devuelto

La posición máxima del control.

## <a name="csliderctrlgetrangemin"></a><a name="getrangemin"></a>CSliderCtrl::GetRangeMin

Recupera la posición mínima del control deslizante en un control deslizante.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valor devuelto

La posición mínima del control.

## <a name="csliderctrlgetselection"></a><a name="getselection"></a>CSliderCtrl::GetSelection

Recupera las posiciones inicial y final de la selección actual en un control deslizante.

```
void GetSelection(
    int& nMin,
    int& nMax) const;
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Referencia a un entero que recibe la posición inicial de la selección actual.

*nMax*<br/>
Referencia a un entero que recibe la posición final de la selección actual.

## <a name="csliderctrlgetthumblength"></a><a name="getthumblength"></a>CSliderCtrl::GetThumbLength

Recupera la longitud del control deslizante en el control de barra de seguimiento actual.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud del control deslizante, en píxeles.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje TBM_GETTHUMBLENGTH,](/windows/win32/Controls/tbm-getthumblength) que se describe en el Windows SDK.

## <a name="csliderctrlgetthumbrect"></a><a name="getthumbrect"></a>CSliderCtrl::GetThumbRect

Recupera el tamaño y la posición del rectángulo delimitador para el control deslizante (thumb) en un control deslizante.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Puntero a `CRect` un objeto que contiene el rectángulo delimitador del control deslizante cuando se devuelve la función.

## <a name="csliderctrlgettic"></a><a name="gettic"></a>CSliderCtrl::GetTic

Recupera la posición de una marca de graduación en un control deslizante.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parámetros

*Ntic*<br/>
El índice de base cero que identifica una marca de graduación.

### <a name="return-value"></a>Valor devuelto

La posición de la marca de graduación especificada o - 1 si *nTic* no especifica un índice válido.

## <a name="csliderctrlgetticarray"></a><a name="getticarray"></a>CSliderCtrl::GetTicArray

Recupera la dirección de la matriz que contiene las posiciones de las marcas de graduación para un control deslizante.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección de la matriz que contiene las posiciones de las marcas de graduación para el control deslizante.

## <a name="csliderctrlgetticpos"></a><a name="getticpos"></a>CSliderCtrl::GetTicPos

Recupera la posición física actual de una marca de graduación en un control deslizante.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parámetros

*Ntic*<br/>
El índice de base cero que identifica una marca de graduación.

### <a name="return-value"></a>Valor devuelto

La posición física, en coordenadas de cliente, de la marca de graduación especificada o - 1 si *nTic* no especifica un índice válido.

## <a name="csliderctrlgettooltips"></a><a name="gettooltips"></a>CSliderCtrl::GetToolTips

Recupera el identificador del control de información sobre herramientas asignado al control deslizante, si existe.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto, o NULL si la información sobre herramientas no está en uso. Si el control deslizante no usa el estilo TBS_TOOLTIPS, el valor devuelto es NULL.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje Win32 TBM_GETTOOLTIPS](/windows/win32/Controls/tbm-gettooltips), como se describe en el Windows SDK. Tenga en cuenta que `CToolTipCtrl` esta función miembro devuelve un objeto en lugar de un identificador a un control.

Para obtener una descripción de los estilos de control deslizante, consulte [Estilos](/windows/win32/Controls/trackbar-control-styles) de control de barra de seguimiento en el Windows SDK.

## <a name="csliderctrlsetbuddy"></a><a name="setbuddy"></a>CSliderCtrl::SetBuddy

Asigna una ventana como la ventana de compañero para un control deslizante.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWndBuddy*<br/>
Puntero a `CWnd` un objeto que se establecerá como amigo del control deslizante.

*fLocation*<br/>
Valor que especifica la ubicación en la que se mostrará la ventana de compañero. Este valor puede ser uno de los siguientes:

- TRUE El amigo aparecerá a la izquierda de la barra de seguimiento si el control de la barra de seguimiento utiliza el estilo TBS_HORZ. Si la barra de seguimiento utiliza el estilo TBS_VERT, el compañero aparece encima del control de la barra de seguimiento.

- FALSE El amigo aparecerá a la derecha de la barra de seguimiento si el control de la barra de seguimiento utiliza el estilo TBS_HORZ. Si la barra de seguimiento utiliza el estilo TBS_VERT, el compañero aparece debajo del control de la barra de seguimiento.

### <a name="return-value"></a>Valor devuelto

Puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que se asignó previamente al control deslizante en esa ubicación.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [TBM_SETBUDDY](/windows/win32/Controls/tbm-setbuddy)de mensaje de Win32 , como se describe en el Windows SDK. Tenga en cuenta que esta `CWnd` función miembro utiliza punteros a objetos, en lugar de identificadores de ventana para su valor devuelto y parámetro.

Para obtener una descripción de los estilos de control deslizante, consulte [Estilos](/windows/win32/Controls/trackbar-control-styles) de control de barra de seguimiento en el Windows SDK.

## <a name="csliderctrlsetlinesize"></a><a name="setlinesize"></a>CSliderCtrl::SetLineSize

Establece el tamaño de la línea para un control deslizante.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nTamaño*<br/>
El nuevo tamaño de línea del control deslizante.

### <a name="return-value"></a>Valor devuelto

El tamaño de línea anterior.

### <a name="remarks"></a>Observaciones

El tamaño de línea afecta a la cantidad que se mueve el control deslizante para las notificaciones TB_LINEUP y TB_LINEDOWN.

## <a name="csliderctrlsetpagesize"></a><a name="setpagesize"></a>CSliderCtrl::SetPageSize

Establece el tamaño de la página para un control deslizante.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nTamaño*<br/>
El nuevo tamaño de página del control deslizante.

### <a name="return-value"></a>Valor devuelto

El tamaño de página anterior.

### <a name="remarks"></a>Observaciones

El tamaño de página afecta a la cantidad que se mueve el control deslizante para las notificaciones TB_PAGEUP y TB_PAGEDOWN.

## <a name="csliderctrlsetpos"></a><a name="setpos"></a>CSliderCtrl::SetPos

Establece la posición actual del control deslizante en un control deslizante.

```
void SetPos(int nPos);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Especifica la nueva posición del control deslizante.

## <a name="csliderctrlsetrange"></a><a name="setrange"></a>CSliderCtrl::SetRange

Establece el rango (posiciones mínima y máxima) para el control deslizante en un control deslizante.

```
void SetRange(
    int nMin,
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Posición mínima para el control deslizante.

*nMax*<br/>
Posición máxima para el control deslizante.

*bRedraw*<br/>
La bandera de redibujo. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar después de establecer el intervalo; de lo contrario, el control deslizante no se vuelve a dibujar.

## <a name="csliderctrlsetrangemax"></a><a name="setrangemax"></a>CSliderCtrl::SetRangeMax

Establece el rango máximo para el control deslizante en un control deslizante.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*nMax*<br/>
Posición máxima para el control deslizante.

*bRedraw*<br/>
La bandera de redibujo. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar después de establecer el intervalo; de lo contrario, el control deslizante no se vuelve a dibujar.

## <a name="csliderctrlsetrangemin"></a><a name="setrangemin"></a>CSliderCtrl::SetRangeMin

Establece el rango mínimo para el control deslizante en un control deslizante.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Posición mínima para el control deslizante.

*bRedraw*<br/>
La bandera de redibujo. Si este parámetro es TRUE, el control deslizante se vuelve a dibujar después de establecer el intervalo; de lo contrario, el control deslizante no se vuelve a dibujar.

## <a name="csliderctrlsetselection"></a><a name="setselection"></a>CSliderCtrl::SetSelection

Establece las posiciones inicial y final de la selección actual en un control deslizante.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Posición inicial del control deslizante.

*nMax*<br/>
Posición final del control deslizante.

## <a name="csliderctrlsetthumblength"></a><a name="setthumblength"></a>CSliderCtrl::SetThumbLength

Establece la longitud del control deslizante en el control de barra de seguimiento actual.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*nLongitud*|[en] Longitud del control deslizante, en píxeles.|

### <a name="remarks"></a>Observaciones

Este método requiere que el control de barra de seguimiento se establezca en [TBS_FIXEDLENGTH](/windows/win32/Controls/trackbar-control-styles) estilo.

Este método envía el [mensaje TBM_SETTHUMBLENGTH,](/windows/win32/Controls/tbm-setthumblength) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_sliderCtrl`código siguiente se define la variable, , que se utiliza para tener acceso al control de barra de seguimiento actual. En el ejemplo también `thumbLength`se define una variable, , que se utiliza para almacenar la longitud predeterminada del componente de pulgar del control de barra de seguimiento. Estas variables se utilizan en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el componente thumb del control de barra de seguimiento en el doble de su longitud predeterminada.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

## <a name="csliderctrlsettic"></a><a name="settic"></a>CSliderCtrl::SetTic

Establece la posición de una marca de graduación en un control deslizante.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parámetros

*Ntic*<br/>
Posición de la marca de graduación. Este parámetro debe especificar un valor positivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se establece la marca de graduación; de lo contrario 0.

## <a name="csliderctrlsetticfreq"></a><a name="setticfreq"></a>CSliderCtrl::SetTicFreq

Establece la frecuencia con la que se muestran las marcas de graduación en un control deslizante.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parámetros

*nFreq*<br/>
Frecuencia de las marcas de graduación.

### <a name="remarks"></a>Observaciones

Por ejemplo, si la frecuencia se establece en 2, se muestra una marca de graduación para cada otro incremento en el rango del control deslizante. El valor predeterminado para la frecuencia es 1 (es decir, cada incremento en el rango está asociado con una marca de graduación).

Debe crear el control con el estilo TBS_AUTOTICKS para utilizar esta función. Para obtener más información, vea [CSliderCtrl::Create](#create).

## <a name="csliderctrlsettipside"></a><a name="settipside"></a>CSliderCtrl::SetTipSide

Coloca un control de información sobre herramientas utilizado por un control de barra de seguimiento.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parámetros

*nUbicación*<br/>
Valor que representa la ubicación en la que se mostrará el control de información sobre herramientas. Para obtener una lista de valores posibles, vea el mensaje Win32 [TBM_SETTIPSIDE](/windows/win32/Controls/tbm-settipside), como se describe en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Valor que representa la ubicación anterior del control de información sobre herramientas. El valor devuelto es igual a uno de los valores posibles para *nLocation*.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 TBM_SETTIPSIDE, como se describe en el Windows SDK. Los controles deslizantes que utilizan el estilo TBS_TOOLTIPS muestran información sobre herramientas. Para obtener una descripción de los estilos de control deslizante, consulte [Estilos](/windows/win32/Controls/trackbar-control-styles) de control de barra de seguimiento en el Windows SDK.

## <a name="csliderctrlsettooltips"></a><a name="settooltips"></a>CSliderCtrl::SetToolTips

Asigna un control de información sobre herramientas a un control deslizante.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parámetros

*pWndTip*<br/>
Puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto que contiene la información sobre herramientas que se va a utilizar con el control deslizante.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_SETTOOLTIPS](/windows/win32/Controls/tbm-settooltips), como se describe en el Windows SDK. Cuando se crea un control deslizante con el estilo TBS_TOOLTIPS, crea un control de información sobre herramientas predeterminado que aparece junto al control deslizante, mostrando la posición actual del control deslizante. Para obtener una descripción de los estilos de control deslizante, consulte [Estilos](/windows/win32/Controls/trackbar-control-styles) de control de barra de seguimiento en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Ejemplo cmNCTRL2 de MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl (clase)](../../mfc/reference/cprogressctrl-class.md)
