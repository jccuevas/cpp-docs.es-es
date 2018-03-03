---
title: Clase CLinkCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1e6834190d7693e60f80285b04a04c484313d3c2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="clinkctrl-class"></a>Clase CLinkCtrl
Proporciona la funcionalidad del control SysLink común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CLinkCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Construye un objeto `CLinkCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CLinkCtrl::Create](#create)|Crea un control de vínculo y lo adjunta a un `CLinkCtrl` objeto.|  
|[CLinkCtrl::CreateEx](#createex)|Crea un control de vínculo con estilos extendidos y lo adjunta a un `CLinkCtrl` objeto.|  
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Recupera el alto ideal de control de vínculo.|  
|[CLinkCtrl::GetIdealSize](#getidealsize)|Calcula el alto preferido del texto del vínculo para el control de vínculo actual, según el ancho especificado del vínculo.|  
|[CLinkCtrl::GetItem](#getitem)|Recupera los Estados y los atributos de un elemento de control de vínculo.|  
|[CLinkCtrl::GetItemID](#getitemid)|Recupera el identificador de un elemento de control de vínculo.|  
|[CLinkCtrl::GetItemState](#getitemstate)|Recupera el estado del elemento de control de vínculo.|  
|[CLinkCtrl::GetItemUrl](#getitemurl)|Recupera la dirección URL representada por el elemento de control de vínculo.|  
|[CLinkCtrl::HitTest](#hittest)|Determina si el usuario hace clic en el vínculo especificado.|  
|[CLinkCtrl::SetItem](#setitem)|Establece los Estados y los atributos de un elemento de control de vínculo.|  
|[CLinkCtrl::SetItemID](#setitemid)|Establece el identificador de un elemento de control de vínculo.|  
|[CLinkCtrl::SetItemState](#setitemstate)|Establece el estado del elemento de control de vínculo.|  
|[CLinkCtrl::SetItemUrl](#setitemurl)|Establece la dirección URL representada por el elemento de control de vínculo.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control link" proporciona una manera cómoda de incrustar vínculos de hipertexto en una ventana. Del control real que es una ventana que representa el texto de marcado telefónico e inicia aplicaciones adecuadas cuando el usuario hace clic en un vínculo incrustado. Varios vínculos se admiten dentro de un control y pueden tener acceso a un índice de base cero.  
  
 Este control (y, por tanto, la `CLinkCtrl` clase) solo está disponible para programas que se ejecutan en Windows XP y versiones posteriores.  
  
 Para obtener más información, consulte [SysLink Control](http://msdn.microsoft.com/library/windows/desktop/bb760706) del SDK de Windows.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CLinkCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="clinkctrl"></a>CLinkCtrl::CLinkCtrl  
 Construye un objeto `CLinkCtrl`.  
  
```  
CLinkCtrl();
```  
  
##  <a name="create"></a>CLinkCtrl::Create  
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
 `lpszLinkMarkup`  
 Puntero a una cadena terminada en cero que contiene los elementos marcados el texto para mostrar. Para obtener más información, vea la sección "Marcado y vínculo de acceso" en el tema [información general de los controles SysLink](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 `dwStyle`  
 Especifica el estilo del control de vínculo. Aplicar cualquier combinación de estilos de control. Vea [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) en la `Windows SDK` para obtener más información.  
  
 `rect`  
 Especifica el tamaño y la posición del control de vínculo. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](../../mfc/reference/rect-structure1.md) estructura.  
  
 `pParentWnd`  
 Especifica la ventana primaria del control de vínculo. No debe ser `NULL`.  
  
 `nID`  
 Especifica el identificador. del control de vínculo  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si la inicialización se realizó correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CLinkCtrl` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de vínculo y lo adjunta a la `CLinkCtrl` objeto. Si desea utilizar los estilos extendidos de windows con el control, llame a [CLinkCtrl::CreateEx](#createex) en lugar de `Create`.  
  
 La segunda forma de la `Create` método está en desuso. Usar la primera forma que especifica el `lpszLinkMarkup` parámetro.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define dos variables, denominadas `m_Link1` y `m_Link2`, que se usan para tener acceso a dos controles de vínculo.  
  
 [!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se crea un control de vínculo en función de la ubicación de otro control de vínculo. El cargador de recursos crea el primer control de vínculo cuando se inicia la aplicación. Cuando la aplicación entra en el método OnInitDialog, crear el segundo control de vínculo con respecto a la posición del primer control de vínculo. A continuación, cambiar el tamaño del segundo control de vínculo para ajustarse al texto que muestra.  
  
 [!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]  
  
##  <a name="createex"></a>CLinkCtrl::CreateEx  
 Crea un control de vínculo con estilos extendidos y lo adjunta a un `CLinkCtrl` objeto.  
  
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
 `lpszLinkMarkup`  
 Puntero a una cadena terminada en cero que contiene los elementos marcados el texto para mostrar. Para obtener más información, vea la sección "Marcado y vínculo de acceso" en el tema [información general de los controles SysLink](http://msdn.microsoft.com/library/windows/desktop/bb760706).  
  
 `dwExStyle`  
 Especifica el estilo extendido del control de vínculo. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) del SDK de Windows.  
  
 `dwStyle`  
 Especifica el estilo del control de vínculo. Aplicar cualquier combinación de estilos de control. Para obtener más información, consulte [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) del SDK de Windows.  
  
 `rect`  
 Especifica el tamaño y la posición del control de vínculo. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](../../mfc/reference/rect-structure1.md) estructura.  
  
 `pParentWnd`  
 Especifica la ventana primaria del control de vínculo. No debe ser `NULL`.  
  
 `nID`  
 Especifica el identificador. del control de vínculo  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si la inicialización se realizó correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Use `CreateEx` en lugar de [crear](#create) aplicar las constantes de estilo extendidos de Windows.  
  
 La segunda forma de la `CreateEx` método está en desuso. Usar la primera forma que especifica el `lpszLinkMarkup` parámetro.  
  
##  <a name="getidealheight"></a>CLinkCtrl::GetIdealHeight  
 Recupera el alto ideal de control de vínculo.  
  
```  
int GetIdealHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto ideal de control, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_GETIDEALHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb760716), tal y como se describe en el SDK de Windows.  
  
##  <a name="getidealsize"></a>CLinkCtrl::GetIdealSize  
 Calcula el alto preferido del texto del vínculo para el control de vínculo actual, según el ancho especificado del vínculo.  
  
```  
int GetIdealSize(
    int cxMaxWidth,   
    SIZE* pSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `cxMaxWidth`|El ancho máximo del vínculo, en píxeles.|  
|[out] *`pSize`|Un puntero a una ventana de [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura. Cuando este método finaliza, el `cy` miembro de la `SIZE` estructura contiene el alto del texto de vínculo ideal para el ancho del texto de vínculo especificado por `cxMaxWidth`. El `cx` miembro de la estructura contiene el ancho del texto de vínculo que necesita realmente.|  
  
### <a name="return-value"></a>Valor devuelto  
 El alto preferido del texto del vínculo, en píxeles. El valor devuelto es el mismo que el valor de la `cy` miembro de la `SIZE` estructura.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de la `GetIdealSize` método, vea el ejemplo de [CLinkCtrl::Create](#create).  
  
 Este método envía el [LM_GETIDEALSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760718) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="getitem"></a>CLinkCtrl::GetItem  
 Recupera los Estados y los atributos de un elemento de control de vínculo.  
  
```  
BOOL GetItem(PLITEM pItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Un puntero a un [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) estructura para recibir información del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720), tal y como se describe en el SDK de Windows.  
  
##  <a name="getitemid"></a>CLinkCtrl::GetItemID  
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
 `iLink`  
 El índice de un elemento de control de vínculo.  
  
 *strID*  
 A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el identificador del elemento especificado.  
  
 *NID*  
 Una cadena terminada en null que contiene el identificador del elemento especificado.  
  
 *cchID*  
 El tamaño en caracteres de la *NID* búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
> [!NOTE]
>  Esta función también devuelve **FALSE** si el búfer de *NID o strID* es menor que **MAX_LINKID_TEXT**.  
  
### <a name="remarks"></a>Comentarios  
 Recupera el identificador de un elemento de control de vínculo específico. Para obtener más información, vea el mensaje de Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) en el SDK de Windows.  
  
##  <a name="getitemstate"></a>CLinkCtrl::GetItemState  
 Recupera el estado del elemento de control de vínculo.  
  
```  
BOOL GetItemState(
    int iLink,  
    UINT* pnState,  
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `iLink`  
 El índice de un elemento de control de vínculo.  
  
 `pnState`  
 El valor del elemento de estado especificado.  
  
 `stateMask`  
 Combinación de marcas que describen qué elemento de estado para obtener. Para obtener una lista de valores, vea la descripción de la **estado** miembro en el [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) estructura. Elementos permitidos son idénticos a aquellos que se permiten en **estado**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Recupera el valor del elemento de estado especificado de un elemento de control de vínculo específico. Para obtener más información, vea el mensaje de Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) en el SDK de Windows.  
  
##  <a name="getitemurl"></a>CLinkCtrl::GetItemUrl  
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
 `iLink`  
 El índice de un elemento de control de vínculo.  
  
 `strUrl`  
 A [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene la dirección URL representada por el elemento especificado  
  
 `szUrl`  
 Una cadena terminada en null que contiene la dirección URL representada por el elemento especificado  
  
 *cchUrl*  
 El tamaño en caracteres de la *szURL* búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
> [!NOTE]
>  Esta función también devuelve **FALSE** si el búfer de *szUrl o strUrl* es menor que **MAX_LINKID_TEXT**.  
  
### <a name="remarks"></a>Comentarios  
 Recupera la dirección URL representada por el elemento de control de vínculo especificado. Para obtener más información, vea el mensaje de Win32 [LM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760720) en el SDK de Windows.  
  
##  <a name="hittest"></a>CLinkCtrl::HitTest  
 Determina si el usuario hace clic en el vínculo especificado.  
  
```  
BOOL HitTest(PLHITTESTINFO phti) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *phti*  
 Puntero a un **LHITTESTINFO** estructura que contiene toda la información sobre el vínculo el usuario hizo clic.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb760722), tal y como se describe en el SDK de Windows.  
  
##  <a name="setitem"></a>CLinkCtrl::SetItem  
 Establece los Estados y los atributos de un elemento de control de vínculo.  
  
```  
BOOL SetItem(PLITEM pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Un puntero a un [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) estructura que contiene la información para establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724), tal y como se describe en el SDK de Windows.  
  
##  <a name="setitemid"></a>CLinkCtrl::SetItemID  
 Recupera el identificador de un elemento de control de vínculo.  
  
```  
BOOL SetItemID(
    int iLink,  
    LPCWSTR szID);
```  
  
### <a name="parameters"></a>Parámetros  
 `iLink`  
 El índice de un elemento de control de vínculo.  
  
 *NID*  
 Una cadena terminada en null que contiene el identificador del elemento especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Establece el identificador de un elemento de control de vínculo específico. Para obtener más información, vea el mensaje de Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) en el SDK de Windows.  
  
##  <a name="setitemstate"></a>CLinkCtrl::SetItemState  
 Recupera el estado del elemento de control de vínculo.  
  
```  
BOOL SetItemState(
    int iLink,  
    UINT state,  
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```  
  
### <a name="parameters"></a>Parámetros  
 `iLink`  
 El índice de un elemento de control de vínculo.  
  
 `pnState`  
 El valor del elemento de estado especificado que se va a establecer.  
  
 `stateMask`  
 Combinación de marcas que describen el elemento de estado que se va a establecer. Para obtener una lista de valores, vea la descripción de la **estado** miembro en el [LITEM](http://msdn.microsoft.com/library/windows/desktop/bb760710) estructura. Elementos permitidos son idénticos a aquellos que se permiten en **estado**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Establece el valor del elemento de estado especificado de un elemento de control de vínculo específico. Para obtener más información, vea el mensaje de Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) en el SDK de Windows.  
  
##  <a name="setitemurl"></a>CLinkCtrl::SetItemUrl  
 Establece la dirección URL representada por el elemento de control de vínculo.  
  
```  
BOOL SetItemUrl(
    int iLink,  
    LPCWSTR szUrl);
```  
  
### <a name="parameters"></a>Parámetros  
 `iLink`  
 El índice de un elemento de control de vínculo.  
  
 `szUrl`  
 Una cadena terminada en null que contiene la dirección URL representada por el elemento especificado  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Establece la dirección URL representada por el elemento de control de vínculo especificado. Para obtener más información, vea el mensaje de Win32 [LM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb760724) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)
