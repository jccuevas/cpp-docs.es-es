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
ms.openlocfilehash: 3fcdddd27437f57ba800a602873d9bb3ae26e82f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283610"
---
# <a name="csliderctrl-class"></a>CSliderCtrl (clase)

Proporciona la funcionalidad del control deslizante común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CSliderCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Construye un objeto `CSliderCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSliderCtrl::ClearSel](#clearsel)|Borra la selección actual en un control deslizante.|
|[CSliderCtrl::ClearTics](#cleartics)|Quita las marcas de graduación actual de un control deslizante.|
|[CSliderCtrl::Create](#create)|Crea un control deslizante y lo adjunta a un `CSliderCtrl` objeto.|
|[CSliderCtrl::CreateEx](#createex)|Crea un control deslizante con los estilos extendidos de Windows especificados y lo adjunta a un `CSliderCtrl` objeto.|
|[CSliderCtrl::GetBuddy](#getbuddy)|Recupera el identificador de ventana deslizante control relacionada en una ubicación determinada.|
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Recupera el tamaño del canal del control deslizante.|
|[CSliderCtrl::GetLineSize](#getlinesize)|Recupera el tamaño de la línea de un control deslizante.|
|[CSliderCtrl::GetNumTics](#getnumtics)|Recupera el número de marcas de graduación en un control deslizante.|
|[CSliderCtrl::GetPageSize](#getpagesize)|Recupera el tamaño de página de un control deslizante.|
|[CSliderCtrl::GetPos](#getpos)|Recupera la posición actual del control deslizante.|
|[CSliderCtrl::GetRange](#getrange)|Recupera las posiciones mínimas y máxima para un control deslizante.|
|[CSliderCtrl::GetRangeMax](#getrangemax)|Recupera la posición máxima de un control deslizante.|
|[CSliderCtrl::GetRangeMin](#getrangemin)|Recupera la posición mínima para un control deslizante.|
|[CSliderCtrl::GetSelection](#getselection)|Recupera el intervalo de la selección actual.|
|[CSliderCtrl::GetThumbLength](#getthumblength)|Recupera la longitud del control deslizante en el control de barra de seguimiento actual.|
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Recupera el tamaño de thumb del control deslizante.|
|[CSliderCtrl::GetTic](#gettic)|Recupera la posición de la marca de graduación especificado.|
|[CSliderCtrl::GetTicArray](#getticarray)|Recupera la matriz de posiciones de marca de graduación para un control deslizante.|
|[CSliderCtrl::GetTicPos](#getticpos)|Recupera la posición de la marca de graduación especificado, en coordenadas de cliente.|
|[CSliderCtrl::GetToolTips](#gettooltips)|Recupera el identificador del control de información sobre herramientas asignado para el control deslizante, si existe.|
|[CSliderCtrl::SetBuddy](#setbuddy)|Asigna una ventana como la ventana relacionada para un control deslizante.|
|[CSliderCtrl::SetLineSize](#setlinesize)|Establece el tamaño de la línea de un control deslizante.|
|[CSliderCtrl::SetPageSize](#setpagesize)|Establece el tamaño de página de un control deslizante.|
|[CSliderCtrl::SetPos](#setpos)|Establece la posición actual del control deslizante.|
|[CSliderCtrl::SetRange](#setrange)|Establece las posiciones mínimas y máxima para un control deslizante.|
|[CSliderCtrl::SetRangeMax](#setrangemax)|Establece la posición máxima de un control deslizante.|
|[CSliderCtrl::SetRangeMin](#setrangemin)|Establece la posición mínima para un control deslizante.|
|[CSliderCtrl::SetSelection](#setselection)|Establece la duración de la selección actual.|
|[CSliderCtrl::SetThumbLength](#setthumblength)|Establece la longitud del control deslizante en el control de barra de seguimiento actual.|
|[CSliderCtrl::SetTic](#settic)|Establece la posición de la marca de graduación especificado.|
|[CSliderCtrl::SetTicFreq](#setticfreq)|Establece la frecuencia de graduación marcas por cada incremento del control deslizante.|
|[CSliderCtrl::SetTipSide](#settipside)|Las posiciones de un control de información sobre herramientas usa un control de barra de seguimiento.|
|[CSliderCtrl::SetToolTips](#settooltips)|Asigna un control de información sobre herramientas a un control deslizante.|

## <a name="remarks"></a>Comentarios

Un "control deslizante" (también conocido como una barra de seguimiento) es una ventana que contiene un control deslizante y las marcas de graduación opcionales. Cuando el usuario mueve el control deslizante, con el mouse o las teclas de dirección, el control envía mensajes de notificación para indicar el cambio.

Controles deslizantes son útiles cuando desee que el usuario seleccione un valor discreto o un conjunto de valores consecutivos en un intervalo. Por ejemplo, podría usar un control deslizante para permitir al usuario establecer la velocidad de repetición del teclado moviendo el control deslizante hasta una marca de graduación determinado.

Este control (y, por tanto, la `CSliderCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

El control deslizante se mueve en incrementos que se especifican al crearlo. Por ejemplo, si especifica que el control deslizante debe tener un intervalo de cinco, el control deslizante solo puede ocupar seis posiciones: una posición en el lado izquierdo del control deslizante y una posición para cada incremento en el intervalo. Normalmente, cada una de estas posiciones se identifica mediante una marca de graduación.

Crear un control deslizante mediante el constructor y el `Create` función miembro de `CSliderCtrl`. Una vez haya creado un control deslizante, puede usar las funciones miembro de `CSliderCtrl` cambiar muchas de sus propiedades. Los cambios que puede realizar incluyen establecer las posiciones mínimas y máxima para el control deslizante, dibujar marcas de graduación, establecer un intervalo de selección y volver a colocar el control deslizante.

Para obtener más información sobre el uso de `CSliderCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CSliderCtrl](../../mfc/using-csliderctrl.md).

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
Volver a dibujar la marca. Si este parámetro es TRUE, se vuelve a dibujar el control deslizante después de borra la selección; en caso contrario, el control deslizante no vuelve a dibujarse.

##  <a name="cleartics"></a>  CSliderCtrl::ClearTics

Quita las marcas de graduación actual de un control deslizante.

```
void ClearTics(BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*bRedraw*<br/>
Volver a dibujar la marca. Si este parámetro es TRUE, se vuelve a dibujar el control deslizante después de que se borran las marcas de graduación; en caso contrario, el control deslizante no vuelve a dibujarse.

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
Especifica el estilo del control deslizante. Aplicar cualquier combinación de [estilos de control deslizante](/windows/desktop/Controls/trackbar-control-styles), que se describen en el SDK de Windows para el control.

*rect*<br/>
Especifica el tamaño y la posición del control deslizante. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.

*pParentWnd*<br/>
Especifica la ventana del elemento primario del control deslizante, normalmente un `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el Id. del control deslizante

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Construir un `CSliderCtrl` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control deslizante y lo adjunta a la `CSliderCtrl` objeto.

Dependiendo de los valores establecidos para *dwStyle*, el control deslizante puede tener una orientación vertical u horizontal. Puede tener marcas de graduación en cualquier lado, ambos o ninguno. También puede usarse para especificar un intervalo de valores consecutivos.

Para aplicar estilos de ventana extendidos para el control deslizante, llame al [CreateEx](#createex) en lugar de `Create`.

##  <a name="createex"></a>  CSliderCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia a la `CSliderCtrl` objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.

*dwStyle*<br/>
Especifica el estilo del control deslizante. Aplicar cualquier combinación de [estilos de control deslizante](/windows/desktop/Controls/trackbar-control-styles), que se describen en el SDK de Windows para el control.

*rect*<br/>
Una referencia a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Un puntero a la ventana que es primario del control.

*nID*<br/>
Identificador de ventana secundaria. del control

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.

##  <a name="csliderctrl"></a>  CSliderCtrl::CSliderCtrl

Construye un objeto `CSliderCtrl`.

```
CSliderCtrl();
```

##  <a name="getbuddy"></a>  CSliderCtrl::GetBuddy

Recupera el identificador de ventana deslizante control relacionada en una ubicación determinada.

```
CWnd* GetBuddy(BOOL fLocation = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*fLocation*<br/>
Un valor booleano que indica cuál de los dos identificadores de ventana relacionada para recuperar. Puede presentar uno de los siguientes valores:

- TRUE, recupera el identificador para el amigo a la izquierda del control deslizante. Si el control deslizante usa el estilo TBS_VERT, el mensaje recuperará al amigo encima del control deslizante.

- FALSE recupera el identificador para el amigo a la derecha del control deslizante. Si el control deslizante usa el estilo TBS_VERT, el mensaje recuperará al amigo debajo del control deslizante.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana relacionada en la ubicación especificada por *fLocation*, o NULL si no existe ninguna ventana relacionada en esa ubicación.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_GETBUDDY](/windows/desktop/Controls/tbm-getbuddy), tal y como se describe en el SDK de Windows. Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](/windows/desktop/Controls/trackbar-control-styles) en el SDK de Windows.

##  <a name="getchannelrect"></a>  CSliderCtrl::GetChannelRect

Recupera el tamaño y posición del rectángulo delimitador para el canal de un control deslizante.

```
void GetChannelRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Un puntero a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el tamaño y posición del canal del rectángulo delimitador que devuelve la función.

### <a name="remarks"></a>Comentarios

El canal es el área sobre la que se mueve el control deslizante y que contiene la parte resaltada cuando se selecciona un intervalo.

##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize

Recupera el tamaño de la línea para un control deslizante.

```
int GetLineSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de una línea para el control deslizante.

### <a name="remarks"></a>Comentarios

El tamaño de línea afecta a cómo mucho el control deslizante se mueve para las notificaciones TB_LINEUP y TB_LINEDOWN. La configuración predeterminada para el tamaño de la línea es 1.

##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics

Recupera el número de marcas de graduación en un control deslizante.

```
UINT GetNumTics() const;
```

### <a name="return-value"></a>Valor devuelto

El número de marcas de graduación en el control deslizante.

##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize

Recupera el tamaño de la página de un control deslizante.

```
int GetPageSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de una página para el control deslizante.

### <a name="remarks"></a>Comentarios

El tamaño de página afecta a cómo mucho el control deslizante se mueve para las notificaciones TB_PAGEUP y TB_PAGEDOWN.

##  <a name="getpos"></a>  CSliderCtrl::GetPos

Recupera la posición actual del control deslizante en un control deslizante.

```
int GetPos() const;
```

### <a name="return-value"></a>Valor devuelto

Posición actual.

##  <a name="getrange"></a>  CSliderCtrl::GetRange

Recupera las posiciones mínimas y máxima para el control deslizante en un control deslizante.

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

### <a name="remarks"></a>Comentarios

Esta función copia los valores en los enteros que se hace referencia a *nmín* y *Nmáx*.

##  <a name="getrangemax"></a>  CSliderCtrl::GetRangeMax

Recupera la posición máxima para el control deslizante en un control deslizante.

```
int GetRangeMax() const;
```

### <a name="return-value"></a>Valor devuelto

La posición del control máximo.

##  <a name="getrangemin"></a>  CSliderCtrl::GetRangeMin

Recupera la posición mínima para el control deslizante en un control deslizante.

```
int GetRangeMin() const;
```

### <a name="return-value"></a>Valor devuelto

La posición del control mínimo.

##  <a name="getselection"></a>  CSliderCtrl::GetSelection

Recupera las posiciones inicial y finales de la selección actual en un control deslizante.

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

##  <a name="getthumblength"></a>  CSliderCtrl::GetThumbLength

Recupera la longitud del control deslizante en el control de barra de seguimiento actual.

```
int GetThumbLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud del control deslizante, en píxeles.

### <a name="remarks"></a>Comentarios

Este método envía el [TBM_GETTHUMBLENGTH](/windows/desktop/Controls/tbm-getthumblength) mensaje, que se describe en el SDK de Windows.

##  <a name="getthumbrect"></a>  CSliderCtrl::GetThumbRect

Recupera el tamaño y posición del rectángulo delimitador para el control deslizante en un control deslizante.

```
void GetThumbRect(LPRECT lprc) const;
```

### <a name="parameters"></a>Parámetros

*lprc*<br/>
Un puntero a un `CRect` objeto que contiene el rectángulo delimitador para el control deslizante cuando se devuelve la función.

##  <a name="gettic"></a>  CSliderCtrl::GetTic

Recupera la posición de una marca de graduación en un control deslizante.

```
int GetTic(int nTic) const;
```

### <a name="parameters"></a>Parámetros

*nTic*<br/>
Índice de base cero que identifica una marca de graduación.

### <a name="return-value"></a>Valor devuelto

La posición de la marca de graduación especificado o - 1 si *nTic* no especifica un índice válido.

##  <a name="getticarray"></a>  CSliderCtrl::GetTicArray

Recupera la dirección de la matriz que contiene las posiciones de las marcas de graduación para un control deslizante.

```
DWORD* GetTicArray() const;
```

### <a name="return-value"></a>Valor devuelto

La dirección de la matriz que contiene las posiciones de marca de graduación para el control deslizante.

##  <a name="getticpos"></a>  CSliderCtrl::GetTicPos

Recupera la posición física actual de una marca de graduación en un control deslizante.

```
int GetTicPos(int nTic) const;
```

### <a name="parameters"></a>Parámetros

*nTic*<br/>
Índice de base cero que identifica una marca de graduación.

### <a name="return-value"></a>Valor devuelto

La posición física, en coordenadas de cliente, de la marca de graduación especificado o - 1 si *nTic* no especifica un índice válido.

##  <a name="gettooltips"></a>  CSliderCtrl::GetToolTips

Recupera el identificador del control de información sobre herramientas asignado para el control deslizante, si existe.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) de objeto, o NULL si la información sobre herramientas no está en uso. Si el control deslizante no usa el estilo TBS_TOOLTIPS, el valor devuelto es NULL.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_GETTOOLTIPS](/windows/desktop/Controls/tbm-gettooltips), tal y como se describe en el SDK de Windows. Tenga en cuenta que esta función miembro devuelve un `CToolTipCtrl` objeto en lugar de un identificador para un control.

Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](/windows/desktop/Controls/trackbar-control-styles) en el SDK de Windows.

##  <a name="setbuddy"></a>  CSliderCtrl::SetBuddy

Asigna una ventana como la ventana relacionada para un control deslizante.

```
CWnd* SetBuddy(
    CWnd* pWndBuddy,
    BOOL fLocation = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWndBuddy*<br/>
Un puntero a un `CWnd` objeto que se establecerá como amigo del control deslizante.

*fLocation*<br/>
Valor que especifica la ubicación en la que se va a mostrar la ventana relacionada. Este valor puede ser uno de los siguientes:

- TRUE el amigo aparecerán a la izquierda de la barra de seguimiento si el control de barra de seguimiento utiliza el estilo de estilos TBS_HORZ. Si la barra de seguimiento usa el estilo TBS_VERT, el amigo aparece encima del control trackbar.

- FALSE el amigo aparecerán a la derecha de la barra de seguimiento si el control de barra de seguimiento utiliza el estilo de estilos TBS_HORZ. Si la barra de seguimiento usa el estilo TBS_VERT, el amigo aparece debajo del control trackbar.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que se asignó previamente para el control deslizante en esa ubicación.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_SETBUDDY](/windows/desktop/Controls/tbm-setbuddy), tal y como se describe en el SDK de Windows. Tenga en cuenta que esta función miembro utiliza punteros a `CWnd` objetos, en lugar de identificadores de ventana para su valor devuelto y el parámetro.

Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](/windows/desktop/Controls/trackbar-control-styles) en el SDK de Windows.

##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize

Establece el tamaño de la línea para un control deslizante.

```
int SetLineSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nSize*<br/>
El nuevo tamaño de línea del control deslizante.

### <a name="return-value"></a>Valor devuelto

El tamaño de la línea anterior.

### <a name="remarks"></a>Comentarios

El tamaño de línea afecta a cómo mucho el control deslizante se mueve para las notificaciones TB_LINEUP y TB_LINEDOWN.

##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize

Establece el tamaño de la página de un control deslizante.

```
int SetPageSize(int nSize);
```

### <a name="parameters"></a>Parámetros

*nSize*<br/>
El nuevo tamaño de página del control deslizante.

### <a name="return-value"></a>Valor devuelto

El tamaño de página anterior.

### <a name="remarks"></a>Comentarios

El tamaño de página afecta a cómo mucho el control deslizante se mueve para las notificaciones TB_PAGEUP y TB_PAGEDOWN.

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
Posición mínima para el control deslizante.

*nMax*<br/>
Posición máxima para el control deslizante.

*bRedraw*<br/>
La marca de renegociación. Si este parámetro es TRUE, se vuelve a dibujar el control deslizante después de establece el intervalo; en caso contrario, el control deslizante no vuelve a dibujarse.

##  <a name="setrangemax"></a>  CSliderCtrl::SetRangeMax

Establece la duración máxima para el control deslizante en un control deslizante.

```
void SetRangeMax(
    int nMax,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*nMax*<br/>
Posición máxima para el control deslizante.

*bRedraw*<br/>
La marca de renegociación. Si este parámetro es TRUE, se vuelve a dibujar el control deslizante después de establece el intervalo; en caso contrario, el control deslizante no vuelve a dibujarse.

##  <a name="setrangemin"></a>  CSliderCtrl::SetRangeMin

Establece el intervalo mínimo para el control deslizante en un control deslizante.

```
void SetRangeMin(
    int nMin,
    BOOL bRedraw = FALSE);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Posición mínima para el control deslizante.

*bRedraw*<br/>
La marca de renegociación. Si este parámetro es TRUE, se vuelve a dibujar el control deslizante después de establece el intervalo; en caso contrario, el control deslizante no vuelve a dibujarse.

##  <a name="setselection"></a>  CSliderCtrl::SetSelection

Establece las posiciones inicial y finales para la selección actual en un control deslizante.

```
void SetSelection(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>Parámetros

*nMin*<br/>
Posición inicial para el control deslizante.

*nMax*<br/>
Posición final para el control deslizante.

##  <a name="setthumblength"></a>  CSliderCtrl::SetThumbLength

Establece la longitud del control deslizante en el control de barra de seguimiento actual.

```
void SetThumbLength(int nLength);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*nLength*|[in] Longitud del control deslizante, en píxeles.|

### <a name="remarks"></a>Comentarios

Este método requiere que el control de barra de seguimiento se establezca en [TBS_FIXEDLENGTH](/windows/desktop/Controls/trackbar-control-styles) estilo.

Este método envía el [TBM_SETTHUMBLENGTH](/windows/desktop/Controls/tbm-setthumblength) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_sliderCtrl`, que se usa para tener acceso al control de barra de seguimiento actual. El ejemplo también define una variable, `thumbLength`, que se usa para almacenar la longitud predeterminada del componente de control de posición del control trackbar. Estas variables se usan en el ejemplo siguiente.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente establece el componente de control de posición del control trackbar a dos veces su duración predeterminada.

[!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]

##  <a name="settic"></a>  CSliderCtrl::SetTic

Establece la posición de una marca de graduación en un control deslizante.

```
BOOL SetTic(int nTic);
```

### <a name="parameters"></a>Parámetros

*nTic*<br/>
Posición de la marca de graduación. Este parámetro debe especificar un valor positivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se establece la marca de graduación; en caso contrario, es 0.

##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq

Establece la frecuencia con que marca las marcas se muestran en un control deslizante.

```
void SetTicFreq(int nFreq);
```

### <a name="parameters"></a>Parámetros

*nFreq*<br/>
Frecuencia de las marcas de graduación.

### <a name="remarks"></a>Comentarios

Por ejemplo, si la frecuencia se establece en 2, se muestra una marca de graduación para cada incremento de otro en el intervalo del control deslizante. El valor predeterminado para la frecuencia es 1 (es decir, cada incremento en el intervalo está asociado con una marca de graduación).

Debe crear el control con el estilo TBS_AUTOTICKS para usar esta función. Para obtener más información, consulte [CSliderCtrl::Create](#create).

##  <a name="settipside"></a>  CSliderCtrl::SetTipSide

Las posiciones de un control de información sobre herramientas usa un control de barra de seguimiento.

```
int SetTipSide(int nLocation);
```

### <a name="parameters"></a>Parámetros

*nLocation*<br/>
Valor que representa la ubicación en la que se va a mostrar el control de información sobre herramientas. Para obtener una lista de valores posibles, vea el mensaje de Win32 [TBM_SETTIPSIDE](/windows/desktop/Controls/tbm-settipside), tal y como se describe en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Un valor que representa la ubicación anterior del control tooltip. El valor devuelto es igual a uno de los valores posibles para *Nubicación*.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 TBM_SETTIPSIDE, como se describe en el SDK de Windows. Los controles deslizantes que usan el estilo TBS_TOOLTIPS mostrarán información sobre herramientas. Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](/windows/desktop/Controls/trackbar-control-styles) en el SDK de Windows.

##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips

Asigna un control de información sobre herramientas a un control deslizante.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parámetros

*pWndTip*<br/>
Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto que contiene la información sobre herramientas para usar con el control deslizante.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_SETTOOLTIPS](/windows/desktop/Controls/tbm-settooltips), tal y como se describe en el SDK de Windows. Cuando se crea un control deslizante con el estilo TBS_TOOLTIPS, crea un control de información sobre herramientas predeterminada que aparece junto al control deslizante, que muestra la posición actual del control deslizante. Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](/windows/desktop/Controls/trackbar-control-styles) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[MFC Sample CMNCTRL2](../../visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CProgressCtrl (clase)](../../mfc/reference/cprogressctrl-class.md)
