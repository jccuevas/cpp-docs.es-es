---
title: CLinkCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: aa1f630b448c60a0eeb6a905ed6eef6f84a2ff8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372256"
---
# <a name="clinkctrl-class"></a>CLinkCtrl (clase)

Proporciona la funcionalidad del control SysLink común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Construye un objeto `CLinkCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CLinkCtrl::Crear](#create)|Crea un control de vínculo `CLinkCtrl` y lo adjunta a un objeto.|
|[CLinkCtrl::CreateEx](#createex)|Crea un control de vínculo con estilos extendidos y lo asocia a un `CLinkCtrl` objeto.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Recupera la altura ideal del control de vínculo.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Calcula el alto preferido del texto del vínculo para el control de vínculo actual, en función del ancho especificado del vínculo.|
|[CLinkCtrl::GetItem](#getitem)|Recupera los estados y atributos de un elemento de control de vínculo.|
|[CLinkCtrl::GetItemID](#getitemid)|Recupera el identificador de un elemento de control de vínculo.|
|[CLinkCtrl::GetItemState](#getitemstate)|Recupera el estado del elemento de control de vínculo.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Recupera la dirección URL representada por el elemento de control de vínculo.|
|[CLinkCtrl::HitTest](#hittest)|Determina si el usuario ha haciendo clic en el vínculo especificado.|
|[CLinkCtrl::SetItem](#setitem)|Establece los estados y atributos de un elemento de control de vínculo.|
|[CLinkCtrl::SetItemID](#setitemid)|Establece el identificador de un elemento de control de vínculo.|
|[CLinkCtrl::SetItemState](#setitemstate)|Establece el estado del elemento de control de vínculo.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Establece la dirección URL representada por el elemento de control de vínculo.|

## <a name="remarks"></a>Observaciones

Un "control de vínculos" proporciona una manera conveniente de incrustar vínculos de hipertexto en una ventana. El control real es una ventana que representa el texto marcado e inicia las aplicaciones adecuadas cuando el usuario hace clic en un vínculo incrustado. Se admiten varios vínculos dentro de un control y se puede acceder a él mediante un índice de base cero.

Este control (y, por lo tanto, la `CLinkCtrl` clase) solo está disponible para programas que se ejecutan en Windows XP y versiones posteriores.

Para obtener más información, consulte [SysLink Control](/windows/win32/Controls/syslink-overview) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a>CLinkCtrl::CLinkCtrl

Construye un objeto `CLinkCtrl`.

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a>CLinkCtrl::Crear

Crea un control de vínculo `CLinkCtrl` y lo adjunta a un objeto.

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*lpszLinkMarkup*<br/>
Puntero a una cadena terminada en cero que contiene el texto marcado para mostrar. Para obtener más información, vea la sección "Acceso de marcado y vínculo" en el tema [Información general de SysLink Controls](/windows/win32/Controls/syslink-overview).

*dwStyle*<br/>
Especifica el estilo del control de vínculo. Aplique cualquier combinación de estilos de control. Consulte [Estilos](/windows/win32/Controls/common-control-styles) de `Windows SDK` control comunes en el para obtener más información.

*Rect*<br/>
Especifica el tamaño y la posición del control de vínculo. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/windows/win32/api/windef/ns-windef-rect) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control de vínculo. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de vínculo.

### <a name="return-value"></a>Valor devuelto

TRUESi la inicialización se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Construir un `CLinkCtrl` objeto en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CLinkCtrl` llame a , que crea el control de vínculo y lo adjunta al objeto. Si desea utilizar estilos de ventanas extendidas con el control, llame a [CLinkCtrl::CreateEx](#createex) en lugar de `Create`.

La segunda forma `Create` del método está en desuso. Utilice el primer formulario que especifica el parámetro *lpszLinkMarkup.*

### <a name="example"></a>Ejemplo

En el ejemplo de código `m_Link1` siguiente `m_Link2`se definen dos variables, denominadas y , que se usan para tener acceso a dos controles de vínculo.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se crea un control de vínculo basado en la ubicación de otro control de vínculo. El cargador de recursos crea el primer control de vínculo cuando se inicia la aplicación. Cuando la aplicación entra en el OnInitDialog método, se crea el segundo control de vínculo en relación con la posición del primer control de vínculo. A continuación, cambie el tamaño del segundo control de vínculo para que se ajuste al texto que muestra.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a>CLinkCtrl::CreateEx

Crea un control de vínculo con estilos extendidos y lo asocia a un `CLinkCtrl` objeto.

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>Parámetros

*lpszLinkMarkup*<br/>
Puntero a una cadena terminada en cero que contiene el texto marcado para mostrar. Para obtener más información, vea la sección "Acceso de marcado y vínculo" en el tema [Información general de SysLink Controls](/windows/win32/Controls/syslink-overview).

*dwExStyle*<br/>
Especifica el estilo extendido del control de vínculo. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de vínculo. Aplique cualquier combinación de estilos de control. Para obtener más información, consulte [Estilos](/windows/win32/Controls/common-control-styles) de control comunes en el Windows SDK.

*Rect*<br/>
Especifica el tamaño y la posición del control de vínculo. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/windows/win32/api/windef/ns-windef-rect) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control de vínculo. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de vínculo.

### <a name="return-value"></a>Valor devuelto

TRUESi la inicialización se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Utilícelo `CreateEx` en lugar de [Crear](#create) para aplicar constantes de estilo de Windows extendidas.

La segunda forma `CreateEx` del método está en desuso. Utilice el primer formulario que especifica el parámetro *lpszLinkMarkup.*

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a>CLinkCtrl::GetIdealHeight

Recupera la altura ideal del control de vínculo.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Valor devuelto

La altura ideal del control, en píxeles.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight), como se describe en el Windows SDK.

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a>CLinkCtrl::GetIdealSize

Calcula el alto preferido del texto del vínculo para el control de vínculo actual, en función del ancho especificado del vínculo.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*cxMaxWidth*|[en] El ancho máximo del vínculo, en píxeles.|
|[fuera] \* *pSize*|Puntero a una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) de Windows. Cuando se devuelve este método, `SIZE` el miembro *cy* de la estructura contiene el alto de texto de vínculo ideal para el ancho de texto de vínculo especificado por *cxMaxWidth*. El miembro *cx* de la estructura contiene el ancho de texto del vínculo que realmente se necesita.|

### <a name="return-value"></a>Valor devuelto

La altura preferida del texto del vínculo, en píxeles. El valor devuelto es el mismo que el `SIZE` valor del miembro *cy* de la estructura.

### <a name="remarks"></a>Observaciones

Para obtener un `GetIdealSize` ejemplo del método, vea el ejemplo de [CLinkCtrl::Create](#create).

Este método envía el [mensaje LM_GETIDEALSIZE,](/windows/win32/Controls/lm-getidealsize) que se describe en el Windows SDK.

## <a name="clinkctrlgetitem"></a><a name="getitem"></a>CLinkCtrl::GetItem

Recupera los estados y atributos de un elemento de control de vínculo.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero a una estructura [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) para recibir información de elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [LM_GETITEM](/windows/win32/Controls/lm-getitem)de mensaje de Win32 , como se describe en el Windows SDK.

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a>CLinkCtrl::GetItemID

Recupera el identificador de un elemento de control de vínculo.

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>Parámetros

*Ilink*<br/>
El índice de un elemento de control de vínculo.

*strID*<br/>
Un [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el identificador del elemento especificado.

*szID*<br/>
Cadena terminada en null que contiene el identificador del elemento especificado.

*cchID*<br/>
El tamaño en caracteres del búfer *szID.*

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

> [!NOTE]
> Esta función también devuelve FALSE si el búfer de *szID o strID* es menor que MAX_LINKID_TEXT.

### <a name="remarks"></a>Observaciones

Recupera el identificador de un elemento de control de vínculo específico. Para obtener más información, consulte el [LM_GETITEM](/windows/win32/Controls/lm-getitem) de mensajes de Win32 en el Windows SDK.

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a>CLinkCtrl::GetItemState

Recupera el estado del elemento de control de vínculo.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parámetros

*Ilink*<br/>
El índice de un elemento de control de vínculo.

*pnState*<br/>
El valor del elemento de estado especificado.

*stateMask*<br/>
Combinación de indicadores que describen qué elemento de estado se va a obtener. Para obtener una lista de valores, vea la descripción del `state` miembro en el [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) estructura. Los elementos permitidos son `state`idénticos a los permitidos en .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Recupera el valor del elemento de estado especificado de un elemento de control de vínculo específico. Para obtener más información, consulte el [LM_GETITEM](/windows/win32/Controls/lm-getitem) de mensajes de Win32 en el Windows SDK.

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a>CLinkCtrl::GetItemUrl

Recupera la dirección URL representada por el elemento de control de vínculo.

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>Parámetros

*Ilink*<br/>
El índice de un elemento de control de vínculo.

*strUrl*<br/>
Un [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene la dirección URL representada por el elemento especificado

*szUrl*<br/>
Cadena terminada en null que contiene la dirección URL representada por el elemento especificado

*cchUrl*<br/>
El tamaño en caracteres del búfer *szURL.*

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

> [!NOTE]
> Esta función también devuelve FALSE si el búfer de *szUrl o strUrl* es menor que MAX_LINKID_TEXT.

### <a name="remarks"></a>Observaciones

Recupera la dirección URL representada por el elemento de control de vínculo especificado. Para obtener más información, consulte el [LM_GETITEM](/windows/win32/Controls/lm-getitem) de mensajes de Win32 en el Windows SDK.

## <a name="clinkctrlhittest"></a><a name="hittest"></a>CLinkCtrl::HitTest

Determina si el usuario ha haciendo clic en el vínculo especificado.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parámetros

*phti*<br/>
Puntero a `LHITTESTINFO` una estructura que contenga información sobre el vínculo en el que ha en cajado el usuario.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [LM_HITTEST](/windows/win32/Controls/lm-hittest)de mensaje de Win32 , como se describe en el Windows SDK.

## <a name="clinkctrlsetitem"></a><a name="setitem"></a>CLinkCtrl::SetItem

Establece los estados y atributos de un elemento de control de vínculo.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero a una estructura [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) que contiene la información que se va a establecer.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem), como se describe en el Windows SDK.

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a>CLinkCtrl::SetItemID

Recupera el identificador de un elemento de control de vínculo.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parámetros

*Ilink*<br/>
El índice de un elemento de control de vínculo.

*szID*<br/>
Cadena terminada en null que contiene el identificador del elemento especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Establece el identificador de un elemento de control de vínculo específico. Para obtener más información, consulte el [mensaje win32 LM_SETITEM](/windows/win32/Controls/lm-setitem) en el Windows SDK.

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a>CLinkCtrl::SetItemState

Recupera el estado del elemento de control de vínculo.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parámetros

*Ilink*<br/>
El índice de un elemento de control de vínculo.

*pnState*<br/>
El valor del elemento de estado especificado que se va a establecer.

*stateMask*<br/>
Combinación de indicadores que describen el elemento de estado que se va a establecer. Para obtener una lista de valores, vea la descripción del `state` miembro en el [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) estructura. Los elementos permitidos son `state`idénticos a los permitidos en .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Establece el valor del elemento de estado especificado de un elemento de control de vínculo específico. Para obtener más información, consulte el [mensaje win32 LM_SETITEM](/windows/win32/Controls/lm-setitem) en el Windows SDK.

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a>CLinkCtrl::SetItemUrl

Establece la dirección URL representada por el elemento de control de vínculo.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parámetros

*Ilink*<br/>
El índice de un elemento de control de vínculo.

*szUrl*<br/>
Cadena terminada en null que contiene la dirección URL representada por el elemento especificado

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Establece la dirección URL representada por el elemento de control de vínculo especificado. Para obtener más información, consulte el [mensaje win32 LM_SETITEM](/windows/win32/Controls/lm-setitem) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)
