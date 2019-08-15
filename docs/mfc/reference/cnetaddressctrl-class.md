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
ms.openlocfilehash: 5e485c22bcc4bf35f61226d84345102052689f89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504532"
---
# <a name="cnetaddressctrl-class"></a>Clase CNetDirecciónCtrl

La clase `CNetAddressCtrl` representa el control de dirección de red, que puede utilizar para especificar y validar el formato de direcciones IPv4, IPv6 y DNS con nombre.

## <a name="syntax"></a>Sintaxis

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Construye un objeto `CNetAddressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CNetAddressCtrl::Create](#create)|Crea un control de dirección de red con los estilos especificados y lo adjunta `CNetAddressCtrl` al objeto actual.|
|[CNetAddressCtrl::CreateEx](#createex)|Crea un control de dirección de red con los estilos extendidos especificados y lo `CNetAddressCtrl` adjunta al objeto actual.|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Muestra un globo de sugerencias de error cuando el usuario escribe una dirección de red no compatible en el control de dirección de red actual.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Recupera una representación validada y analizada de la dirección de red asociada al control de dirección de red actual.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Recupera el tipo de dirección de red que el control de dirección de red actual puede admitir.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Establece el tipo de dirección de red que puede admitir el control de dirección de red actual.|

## <a name="remarks"></a>Comentarios

El control de dirección de red comprueba que el formato de la dirección que escribe el usuario es correcto. El control no se conecta realmente a la dirección de red. El método [CNetAddressCtrl:: SetAllowType](#setallowtype) especifica uno o más tipos de direcciones que el método [CNetAddressCtrl:: GetAddress](#getaddress) puede analizar y comprobar. Una dirección puede tener la forma de IPv4, IPv6 o una dirección con nombre para un servidor, una red, un host o un destino de mensaje de difusión. Si el formato de la dirección es incorrecto, puede usar el método [CNetAddressCtrl::D isplayerrortip](#displayerrortip) para mostrar un cuadro de mensaje informativo que apunta gráficamente al cuadro de texto del control de dirección de red y muestra un mensaje de error predefinido.

La `CNetAddressCtrl` clase se deriva de la clase [CEDIT](../../mfc/reference/cedit-class.md) . Por lo tanto, el control de dirección de red proporciona acceso a todos los mensajes del control de edición de Windows.

En la ilustración siguiente se muestra un cuadro de diálogo que contiene un control de dirección de red. El cuadro de texto (1) para el control de dirección de red contiene una dirección de red no válida. Si la dirección de red no es válida, se muestra el mensaje de recuadro informativo (2).

![Cuadro de diálogo con un control de dirección de red y un] recuadro informativo. (../../mfc/reference/media/cnetaddctrl.png "Cuadro de diálogo con un control de dirección de red y un") recuadro informativo.

## <a name="example"></a>Ejemplo

El siguiente ejemplo de código es una parte de un cuadro de diálogo que valida una dirección de red. Los controladores de eventos de tres botones de radio especifican que la dirección de red puede ser de uno de los tres tipos de direcciones. El usuario escribe una dirección en el cuadro de texto del control de red y, a continuación, presiona un botón para validar la dirección. Si la dirección es válida, se muestra un mensaje de operación correcta; de lo contrario, se muestra el mensaje de error de recuadro informativo predefinido.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Ejemplo

El siguiente ejemplo de código del archivo de encabezado del cuadro de diálogo define las variables [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) y [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) que requiere el método [CNetAddressCtrl:: GetAddress](#getaddress) .

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

Esta clase es compatible con Windows Vista y versiones posteriores.

Los requisitos adicionales para esta clase se describen en [requisitos de compilación para los controles comunes de Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="cnetaddressctrl"></a>  CNetAddressCtrl::CNetAddressCtrl

Construye un objeto `CNetAddressCtrl`.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Comentarios

Use el método [CNetAddressCtrl:: Create](#create) o [CNetAddressCtrl:: CreateEx](#createex) para crear un control de red y adjuntarlo `CNetAddressCtrl` al objeto.

##  <a name="create"></a>  CNetAddressCtrl::Create

Crea un control de dirección de red con los estilos especificados y lo adjunta `CNetAddressCtrl` al objeto actual.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*dwStyle*|de Combinación bit a bit de los estilos que se van a aplicar al control. Para obtener más información, vea [Editar estilos](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*rect*|de Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que contiene la posición y el tamaño del control.|
|*pParentWnd*|de Un puntero no nulo a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del control.|
|*nID*|de IDENTIFICADOR del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="createex"></a>  CNetAddressCtrl::CreateEx

Crea un control de dirección de red con los estilos extendidos especificados y lo `CNetAddressCtrl` adjunta al objeto actual.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*dwExStyle*|de Combinación bit a bit (o) de estilos extendidos que se va a aplicar al control. Para obtener más información, vea el parámetro *dwExStyle* de la función [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .|
|*dwStyle*|de Combinación bit a bit (o) de estilos que se va a aplicar al control. Para obtener más información, vea [Editar estilos](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*rect*|de Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que contiene la posición y el tamaño del control.|
|*pParentWnd*|de Un puntero no nulo a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del control.|
|*nID*|de IDENTIFICADOR del control.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="displayerrortip"></a>  CNetAddressCtrl::DisplayErrorTip

Muestra un mensaje de error en el globo de sugerencias que está asociado con el control de dirección de red actual.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Valor devuelto

Valor `S_OK` si este método se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

Use el método [CNetAddressCtrl:: SetAllowType](#setallowtype) para especificar los tipos de direcciones que el control de dirección de red actual puede admitir. Use el método [CNetAddressCtrl:: GetAddress](#getaddress) para validar y analizar la dirección de red que especifica el usuario. Use el método [CNetAddressCtrl::D isplayerrortip](#displayerrortip) para mostrar un mensaje de error representativo si el método [CNetAddressCtrl:: GetAddress](#getaddress) no se realiza correctamente.

Este mensaje invoca la macro [NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) , que se describe en el Windows SDK. Esa macro envía el `NCM_DISPLAYERRORTIP` mensaje.

##  <a name="getaddress"></a>  CNetAddressCtrl::GetAddress

Recupera una representación validada y analizada de la dirección de red que está asociada con el control de dirección de red actual.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Parámetros

*pAddress*<br/>
[in, out] Puntero a una estructura [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) .  Establezca el miembro *pAddrInfo* de esta estructura en la dirección de una estructura [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) antes de llamar al método GetAddress.

### <a name="return-value"></a>Valor devuelto

El valor S_OK si este método se realiza correctamente; de lo contrario, un código de error COM. Para obtener más información sobre los posibles códigos de error, vea la sección valor devuelto de la macro [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) .

### <a name="remarks"></a>Comentarios

Si este método se realiza correctamente, la estructura [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) contiene información adicional sobre la dirección de red.

Use el método [CNetAddressCtrl:: SetAllowType](#setallowtype) para especificar los tipos de direcciones que el control de dirección de red actual puede admitir. Use el método [CNetAddressCtrl:: GetAddress](#getaddress) para validar y analizar la dirección de red que especifica el usuario. Use el método [CNetAddressCtrl::D isplayerrortip](#displayerrortip) para mostrar un mensaje de error representativo si el método [CNetAddressCtrl:: GetAddress](#getaddress) no se realiza correctamente.

Este método invoca la macro [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) , que se describe en el Windows SDK. Esa macro envía el mensaje NCM_GETADDRESS.

##  <a name="getallowtype"></a>  CNetAddressCtrl::GetAllowType

Recupera el tipo de dirección de red que el control de dirección de red actual puede admitir.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Valor devuelto

Combinación bit a bit (o) de marcas que especifica los tipos de direcciones que el control de dirección de red puede admitir. Para obtener más información, vea [NET_STRING](/windows/win32/shell/net-string).

### <a name="remarks"></a>Comentarios

Este mensaje invoca la macro [NetAddr_GetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) , que se describe en el Windows SDK. Esa macro envía el mensaje NCM_GETALLOWTYPE.

##  <a name="setallowtype"></a>  CNetAddressCtrl::SetAllowType

Establece el tipo de dirección de red que puede admitir el control de dirección de red actual.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*dwAddrMask*|de Combinación bit a bit (o) de marcas que especifica los tipos de direcciones que el control de dirección de red puede admitir. Para obtener más información, vea [NET_STRING](/windows/win32/shell/net-string).|

### <a name="return-value"></a>Valor devuelto

S_OK si este método se realiza correctamente; de lo contrario, un código de error COM.

### <a name="remarks"></a>Comentarios

Use el método [CNetAddressCtrl:: SetAllowType](#setallowtype) para especificar los tipos de direcciones que el control de dirección de red actual puede admitir. Use el método [CNetAddressCtrl:: GetAddress](#getaddress) para validar y analizar la dirección de red que especifica el usuario. Use el método [CNetAddressCtrl::D isplayerrortip](#displayerrortip) para mostrar un mensaje de error representativo si el método [CNetAddressCtrl:: GetAddress](#getaddress) no se realiza correctamente.

Este mensaje invoca la macro [NetAddr_SetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) , que se describe en el Windows SDK. Esa macro envía el mensaje NCM_SETALLOWTYPE.

## <a name="see-also"></a>Vea también

[CNetAddressCtrl (clase)](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)
