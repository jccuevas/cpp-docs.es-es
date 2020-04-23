---
title: Clase CNetDirecciónCtrl
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: c6f391966ef6657363e8f23e5666a57a935b08e1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752778"
---
# <a name="cnetaddressctrl-class"></a>Clase CNetDirecciónCtrl

La clase `CNetAddressCtrl` representa el control de dirección de red, que puede utilizar para especificar y validar el formato de direcciones IPv4, IPv6 y DNS con nombre.

## <a name="syntax"></a>Sintaxis

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Construye un objeto `CNetAddressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CNetAddressCtrl::Crear](#create)|Crea un control de dirección de red con `CNetAddressCtrl` estilos especificados y lo asocia al objeto actual.|
|[CNetAddressCtrl::CreateEx](#createex)|Crea un control de dirección de red con estilos extendidos especificados y lo asocia al objeto actual. `CNetAddressCtrl`|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Muestra una sugerencia de globo de error cuando el usuario introduce una dirección de red no admitida en el control de dirección de red actual.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Recupera una representación validada y analizada de la dirección de red asociada con el control de dirección de red actual.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Recupera el tipo de dirección de red que puede admitir el control de dirección de red actual.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Establece el tipo de dirección de red que puede admitir el control de dirección de red actual.|

## <a name="remarks"></a>Observaciones

El control de dirección de red comprueba que el formato de la dirección que introduce el usuario es correcto. El control no se conecta realmente a la dirección de red. El [CNetAddressCtrl::SetAllowType](#setallowtype) método especifica uno o varios tipos de dirección que el [CNetAddressCtrl::GetAddress](#getaddress) método puede analizar y comprobar. Una dirección puede tener la forma de un iPv4, IPv6 o una dirección con nombre para un servidor, red, host o destino de mensaje de difusión. Si el formato de la dirección es incorrecto, puede usar el método [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) para mostrar un cuadro de mensaje de información que apunta gráficamente al cuadro de texto del control de dirección de red y muestra un mensaje de error predefinido.

La `CNetAddressCtrl` clase se deriva de la [clase CEdit.](../../mfc/reference/cedit-class.md) Por lo tanto, el control de dirección de red proporciona acceso a todos los mensajes de control de edición de Windows.

En la figura siguiente se muestra un cuadro de diálogo que contiene un control de dirección de red. El cuadro de texto (1) del control de dirección de red contiene una dirección de red no válida. Se muestra el mensaje de información (2) si la dirección de red no es válida.

![Cuadro de diálogo con un control de dirección de red y un recuadro informativo.](../../mfc/reference/media/cnetaddctrl.png "Cuadro de diálogo con un control de dirección de red y un recuadro informativo.")

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente es una parte de un cuadro de diálogo que valida una dirección de red. Los controladores de eventos para tres botones de opción especifican que la dirección de red puede ser uno de los tres tipos de dirección. El usuario escribe una dirección en el cuadro de texto del control de red y, a continuación, presiona un botón para validar la dirección. Si la dirección es válida, se muestra un mensaje de éxito; de lo contrario, se muestra el mensaje de error de información predefinida.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Ejemplo

El ejemplo de código siguiente del archivo de encabezado de cuadro de diálogo define las variables [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) y [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) que requiere el [método CNetAddressCtrl::GetAddress.](#getaddress)

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

Esta clase se admite en Windows Vista y versiones posteriores.

Los requisitos adicionales para esta clase se describen en [Requisitos de compilación para controles comunes](../../mfc/build-requirements-for-windows-vista-common-controls.md)de Windows Vista .

## <a name="cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a>CNetAddressCtrl::CNetAddressCtrl

Construye un objeto `CNetAddressCtrl`.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Observaciones

Utilice el método [CNetAddressCtrl::Create](#create) o [CNetAddressCtrl::CreateEx](#createex) para crear `CNetAddressCtrl` un control de red y adjuntarlo al objeto.

## <a name="cnetaddressctrlcreate"></a><a name="create"></a>CNetAddressCtrl::Crear

Crea un control de dirección de red con `CNetAddressCtrl` estilos especificados y lo asocia al objeto actual.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwStyle*|[en] Una combinación bit a bit de estilos que se aplicarán al control. Para obtener más información, consulte [Editar estilos](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[en] Una referencia a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene la posición y el tamaño del control.|
|*pParentWnd*|[en] Un puntero no nulo a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control.|
|*nID*|[en] El identificador del control.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

## <a name="cnetaddressctrlcreateex"></a><a name="createex"></a>CNetAddressCtrl::CreateEx

Crea un control de dirección de red con estilos extendidos especificados y lo asocia al objeto actual. `CNetAddressCtrl`

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwExStyle*|[en] Una combinación bit a bit (OR) de estilos extendidos que se aplicarán al control. Para obtener más información, vea el parámetro *dwExStyle* de la función [CreateWindowEx.](/windows/win32/api/winuser/nf-winuser-createwindowexw)|
|*dwStyle*|[en] Una combinación bit a bit (OR) de estilos que se aplicarán al control. Para obtener más información, consulte [Editar estilos](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*Rect*|[en] Una referencia a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene la posición y el tamaño del control.|
|*pParentWnd*|[en] Un puntero no nulo a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control.|
|*nID*|[en] El identificador del control.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

## <a name="cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a>CNetAddressCtrl::DisplayErrorTip

Muestra un mensaje de error en la sugerencia de globo asociada al control de dirección de red actual.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Valor devuelto

El `S_OK` valor si este método es correcto; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

Utilice el método [CNetAddressCtrl::SetAllowType](#setallowtype) para especificar los tipos de direcciones que puede admitir el control de direcciones de red actual. Utilice el método [CNetAddressCtrl::GetAddress](#getaddress) para validar y analizar la dirección de red que escribe el usuario. Utilice el [método CNetAddressCtrl::DisplayErrorTip](#displayerrortip) para mostrar una información sobre el mensaje de error si el método [CNetAddressCtrl::GetAddress](#getaddress) no se realiza correctamente.

Este mensaje invoca la macro [NetAddr_DisplayErrorTip,](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) que se describe en el Windows SDK. Esa macro `NCM_DISPLAYERRORTIP` envía el mensaje.

## <a name="cnetaddressctrlgetaddress"></a><a name="getaddress"></a>CNetAddressCtrl::GetAddress

Recupera una representación validada y analizada de la dirección de red asociada al control de dirección de red actual.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parámetros

*pAddress*<br/>
[adentro, fuera] Puntero a una estructura [NC_ADDRESS.](/windows/win32/api/shellapi/ns-shellapi-nc_address)  Establezca el *pAddrInfo* miembro de esta estructura en la dirección de un [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) estructura antes de llamar a la GetAddress método.

### <a name="return-value"></a>Valor devuelto

El valor S_OK si este método se realiza correctamente; de lo contrario, un código de error COM. Para obtener más información acerca de los posibles códigos de error, consulte la sección Valor devuelto de la [macro NetAddr_GetAddress.](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress)

### <a name="remarks"></a>Observaciones

Si este método se realiza correctamente, la estructura [de NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) contiene información adicional sobre la dirección de red.

Utilice el método [CNetAddressCtrl::SetAllowType](#setallowtype) para especificar los tipos de direcciones que puede admitir el control de direcciones de red actual. Utilice el método [CNetAddressCtrl::GetAddress](#getaddress) para validar y analizar la dirección de red que escribe el usuario. Utilice el [método CNetAddressCtrl::DisplayErrorTip](#displayerrortip) para mostrar una información sobre el mensaje de error si el método [CNetAddressCtrl::GetAddress](#getaddress) no se realiza correctamente.

Este método invoca la [macro de NetAddr_GetAddress,](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) que se describe en el Windows SDK. Esa macro envía el mensaje de NCM_GETADDRESS.

## <a name="cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a>CNetAddressCtrl::GetAllowType

Recupera el tipo de dirección de red que puede admitir el control de dirección de red actual.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Valor devuelto

Una combinación bit a bit (OR) de indicadores que especifica los tipos de direcciones que puede admitir el control de direcciones de red. Para obtener más información, consulte [NET_STRING](/windows/win32/shell/net-string).

### <a name="remarks"></a>Observaciones

Este mensaje invoca la macro [NetAddr_GetAllowType,](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) que se describe en el Windows SDK. Esa macro envía el mensaje NCM_GETALLOWTYPE.

## <a name="cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a>CNetAddressCtrl::SetAllowType

Establece el tipo de dirección de red que puede admitir el control de dirección de red actual.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*dwAddrMask*|[en] Una combinación bit a bit (OR) de indicadores que especifica los tipos de direcciones que puede admitir el control de direcciones de red. Para obtener más información, consulte [NET_STRING](/windows/win32/shell/net-string).|

### <a name="return-value"></a>Valor devuelto

S_OK si este método es correcto; de lo contrario, un código de error COM.

### <a name="remarks"></a>Observaciones

Utilice el método [CNetAddressCtrl::SetAllowType](#setallowtype) para especificar los tipos de direcciones que puede admitir el control de direcciones de red actual. Utilice el método [CNetAddressCtrl::GetAddress](#getaddress) para validar y analizar la dirección de red que escribe el usuario. Utilice el [método CNetAddressCtrl::DisplayErrorTip](#displayerrortip) para mostrar una información sobre el mensaje de error si el método [CNetAddressCtrl::GetAddress](#getaddress) no se realiza correctamente.

Este mensaje invoca la [macro NetAddr_SetAllowType,](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) que se describe en el Windows SDK. Esa macro envía el mensaje NCM_SETALLOWTYPE.

## <a name="see-also"></a>Vea también

[Clase CNetAddressCtrl](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)
