---
title: Clase CLinkCtrl
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
ms.openlocfilehash: 37d9e624c40f0d6aa7f3d3fa1ed3d97ffa478ee7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505701"
---
# <a name="clinkctrl-class"></a>Clase CLinkCtrl

Proporciona la funcionalidad del control SysLink común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Construye un objeto `CLinkCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CLinkCtrl::Create](#create)|Crea un control de vínculo y lo adjunta a un `CLinkCtrl` objeto.|
|[CLinkCtrl::CreateEx](#createex)|Crea un control de vínculo con estilos extendidos y lo adjunta a `CLinkCtrl` un objeto.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Recupera el alto ideal del control de vínculo.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Calcula el alto preferido del texto del vínculo para el control de vínculo actual, dependiendo del ancho especificado del vínculo.|
|[CLinkCtrl::GetItem](#getitem)|Recupera los Estados y los atributos de un elemento de control de vínculo.|
|[CLinkCtrl::GetItemID](#getitemid)|Recupera el identificador de un elemento de control de vínculo.|
|[CLinkCtrl::GetItemState](#getitemstate)|Recupera el estado del elemento de control de vínculo.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Recupera la dirección URL representada por el elemento de control de vínculo.|
|[CLinkCtrl::HitTest](#hittest)|Determina si el usuario hizo clic en el vínculo especificado.|
|[CLinkCtrl::SetItem](#setitem)|Establece los Estados y los atributos de un elemento de control de vínculo.|
|[CLinkCtrl::SetItemID](#setitemid)|Establece el identificador de un elemento de control de vínculo.|
|[CLinkCtrl::SetItemState](#setitemstate)|Establece el estado del elemento de control de vínculo.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Establece la dirección URL representada por el elemento de control de vínculo.|

## <a name="remarks"></a>Comentarios

Un "control de vínculo" proporciona una manera cómoda de insertar vínculos de hipertexto en una ventana. El control real es una ventana que representa el texto marcado e inicia las aplicaciones adecuadas cuando el usuario hace clic en un vínculo incrustado. Se admiten varios vínculos dentro de un control y se puede tener acceso a ellos mediante un índice basado en cero.

Este control (y, por `CLinkCtrl` lo tanto, la clase) solo está disponible para programas que se ejecutan en Windows XP y versiones posteriores.

Para obtener más información, vea [SysLink (control](/windows/win32/Controls/syslink-overview) ) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl

Construye un objeto `CLinkCtrl`.

```
CLinkCtrl();
```

##  <a name="create"></a>  CLinkCtrl::Create

Crea un control de vínculo y lo adjunta a un `CLinkCtrl` objeto.

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
Puntero a una cadena terminada en cero que contiene el texto marcado que se va a mostrar. Para obtener más información, vea la sección "marcado y acceso a vínculos" en el tema [información general sobre los controles SysLink](/windows/win32/Controls/syslink-overview).

*dwStyle*<br/>
Especifica el estilo del control de vínculo. Aplique cualquier combinación de estilos de control. Vea [estilos de control comunes](/windows/win32/Controls/common-control-styles) en `Windows SDK` para obtener más información.

*rect*<br/>
Especifica el tamaño y la posición del control de vínculo. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Especifica la ventana primaria del control de vínculo. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de vínculo.

### <a name="return-value"></a>Valor devuelto

TRUE si la inicialización se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Un `CLinkCtrl` objeto se crea en dos pasos. En primer lugar, llame al constructor y `Create`, a continuación, llame `CLinkCtrl` a, que crea el control de vínculo y lo adjunta al objeto. Si desea utilizar estilos extendidos de Windows con el control, llame a [CLinkCtrl:: CreateEx](#createex) en lugar `Create`de a.

La segunda forma del `Create` método está en desuso. Use el primer formulario que especifique el parámetro *lpszLinkMarkup* .

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se definen dos `m_Link1` variables `m_Link2`, denominadas y, que se utilizan para tener acceso a dos controles de vínculo.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se crea un control de vínculo basado en la ubicación de otro control de vínculo. El cargador de recursos crea el primer control de vínculo cuando se inicia la aplicación. Cuando la aplicación entra en el método OnInitDialog, se crea el segundo control de vínculo en relación con la posición del primer control de vínculo. A continuación, cambiará el tamaño del segundo control de vínculo para ajustarse al texto que muestra.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>  CLinkCtrl::CreateEx

Crea un control de vínculo con estilos extendidos y lo adjunta a `CLinkCtrl` un objeto.

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
Puntero a una cadena terminada en cero que contiene el texto marcado que se va a mostrar. Para obtener más información, vea la sección "marcado y acceso a vínculos" en el tema [información general sobre los controles SysLink](/windows/win32/Controls/syslink-overview).

*dwExStyle*<br/>
Especifica el estilo extendido del control de vínculo. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de vínculo. Aplique cualquier combinación de estilos de control. Para obtener más información, vea [estilos de control comunes](/windows/win32/Controls/common-control-styles) en el Windows SDK.

*rect*<br/>
Especifica el tamaño y la posición del control de vínculo. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Especifica la ventana primaria del control de vínculo. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de vínculo.

### <a name="return-value"></a>Valor devuelto

TRUE si la inicialización se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [Create](#create) para aplicar constantes de estilo extendidas de Windows.

La segunda forma del `CreateEx` método está en desuso. Use el primer formulario que especifique el parámetro *lpszLinkMarkup* .

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

Recupera el alto ideal del control de vínculo.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Valor devuelto

Alto ideal del control, en píxeles.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight), tal y como se describe en el Windows SDK.

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

Calcula el alto preferido del texto del vínculo para el control de vínculo actual, dependiendo del ancho especificado del vínculo.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*cxMaxWidth*|de Ancho máximo del vínculo, en píxeles.|
|enuncia \* *pSize*|Puntero a una estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) de Windows. Cuando este método devuelve, el miembro *CY* de la `SIZE` estructura contiene el alto de texto del vínculo ideal para el ancho del texto del vínculo especificado por *cxMaxWidth*. El miembro *CX* de la estructura contiene el ancho del texto del vínculo que realmente se necesita.|

### <a name="return-value"></a>Valor devuelto

Alto preferido del texto del vínculo, en píxeles. El valor devuelto es el mismo que el valor del miembro *CY* de la `SIZE` estructura.

### <a name="remarks"></a>Comentarios

Para obtener un ejemplo del `GetIdealSize` método, vea el ejemplo de [CLinkCtrl:: Create](#create).

Este método envía el mensaje [LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize) , que se describe en el Windows SDK.

##  <a name="getitem"></a>  CLinkCtrl::GetItem

Recupera los Estados y los atributos de un elemento de control de vínculo.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero a [una estructura de](/windows/win32/api/commctrl/ns-commctrl-litem) la que se va a recibir información del elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem), tal y como se describe en el Windows SDK.

##  <a name="getitemid"></a>  CLinkCtrl::GetItemID

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

*iLink*<br/>
Índice de un elemento de control de vínculo.

*strID*<br/>
Objeto [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el identificador del elemento especificado.

*szID*<br/>
Una cadena terminada en null que contiene el identificador del elemento especificado.

*cchID*<br/>
Tamaño en caracteres del búfer de *szID* .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

> [!NOTE]
>  Esta función también devuelve FALSE si el búfer de *szID o progresa* es menor que MAX_LINKID_TEXT.

### <a name="remarks"></a>Comentarios

Recupera el identificador de un elemento de control de vínculo específico. Para obtener más información, vea el mensaje de Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) en el Windows SDK.

##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState

Recupera el estado del elemento de control de vínculo.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parámetros

*iLink*<br/>
Índice de un elemento de control de vínculo.

*pnState*<br/>
Valor del elemento de estado especificado.

*stateMask*<br/>
Combinación de marcas que describen el elemento de estado que se va a obtener. Para obtener una lista de valores, vea la descripción del `state` miembro en la [estructura de](/windows/win32/api/commctrl/ns-commctrl-litem) la. Los elementos permitidos son idénticos a los `state`permitidos en.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Recupera el valor del elemento de estado especificado de un elemento de control de vínculo específico. Para obtener más información, vea el mensaje de Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) en el Windows SDK.

##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl

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

*iLink*<br/>
Índice de un elemento de control de vínculo.

*strUrl*<br/>
Objeto [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) que contiene la dirección URL representada por el elemento especificado.

*szUrl*<br/>
Una cadena terminada en null que contiene la dirección URL representada por el elemento especificado.

*cchUrl*<br/>
Tamaño en caracteres del búfer de *szURL* .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

> [!NOTE]
>  Esta función también devuelve FALSE si el búfer de *szUrl o strUrl* es menor que MAX_LINKID_TEXT.

### <a name="remarks"></a>Comentarios

Recupera la dirección URL representada por el elemento de control de vínculo especificado. Para obtener más información, vea el mensaje de Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) en el Windows SDK.

##  <a name="hittest"></a>  CLinkCtrl::HitTest

Determina si el usuario hizo clic en el vínculo especificado.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parámetros

*phti*<br/>
Puntero a una `LHITTESTINFO` estructura que contiene información sobre el vínculo en el que el usuario hizo clic.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_HITTEST](/windows/win32/Controls/lm-hittest), tal y como se describe en el Windows SDK.

##  <a name="setitem"></a>  CLinkCtrl::SetItem

Establece los Estados y los atributos de un elemento de control de vínculo.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero a [una estructura de](/windows/win32/api/commctrl/ns-commctrl-litem) un valor que contiene la información que se va a establecer.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem), tal y como se describe en el Windows SDK.

##  <a name="setitemid"></a>  CLinkCtrl::SetItemID

Recupera el identificador de un elemento de control de vínculo.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parámetros

*iLink*<br/>
Índice de un elemento de control de vínculo.

*szID*<br/>
Una cadena terminada en null que contiene el identificador del elemento especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Establece el identificador de un elemento de control de vínculo específico. Para obtener más información, vea el mensaje de Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) en el Windows SDK.

##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState

Recupera el estado del elemento de control de vínculo.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parámetros

*iLink*<br/>
Índice de un elemento de control de vínculo.

*pnState*<br/>
Valor del elemento de estado especificado que se va a establecer.

*stateMask*<br/>
Combinación de marcas que describen el elemento de estado que se va a establecer. Para obtener una lista de valores, vea la descripción del `state` miembro en la [estructura de](/windows/win32/api/commctrl/ns-commctrl-litem) la. Los elementos permitidos son idénticos a los `state`permitidos en.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Establece el valor del elemento de estado especificado de un elemento de control de vínculo específico. Para obtener más información, vea el mensaje de Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) en el Windows SDK.

##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl

Establece la dirección URL representada por el elemento de control de vínculo.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parámetros

*iLink*<br/>
Índice de un elemento de control de vínculo.

*szUrl*<br/>
Una cadena terminada en null que contiene la dirección URL representada por el elemento especificado.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Comentarios

Establece la dirección URL representada por el elemento de control de vínculo especificado. Para obtener más información, vea el mensaje de Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)
