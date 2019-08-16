---
title: CHotKeyCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: 9818c32a7779d646ca5a9485a1331dfa393408ba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506146"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl (clase)

Proporciona la funcionalidad del control común de tecla de acceso rápido de Windows.

## <a name="syntax"></a>Sintaxis

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Construye un objeto `CHotKeyCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|Crea un control de tecla de acceso rápido y lo adjunta `CHotKeyCtrl` a un objeto.|
|[CHotKeyCtrl::CreateEx](#createex)|Crea un control de tecla de acceso rápido con los estilos extendidos de Windows especificados `CHotKeyCtrl` y lo adjunta a un objeto.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Recupera el código de tecla virtual y los marcadores modificadores de una tecla de acceso rápido de un control de tecla de acceso rápido.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Recupera el nombre de la clave, en el juego de caracteres local, asignado a una tecla de acceso rápido.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Recupera el nombre de la clave, en el juego de caracteres local, asignado al código de tecla virtual especificado.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Establece la combinación de teclas de acceso rápido de un control de tecla de acceso rápido.|
|[CHotKeyCtrl::SetRules](#setrules)|Define las combinaciones no válidas y la combinación de modificadores predeterminados para un control de tecla de acceso rápido.|

## <a name="remarks"></a>Comentarios

Un "control de tecla de acceso rápido" es una ventana que permite al usuario crear una tecla de acceso rápido. Una "tecla de acceso rápido" es una combinación de teclas que el usuario puede presionar para realizar una acción rápidamente. (Por ejemplo, un usuario puede crear una tecla de acceso rápido que activa una ventana determinada y la coloca en la parte superior del orden Z). El control de tecla de acceso rápido muestra las opciones del usuario y garantiza que el usuario selecciona una combinación de teclas válida.

Este control (y, por `CHotKeyCtrl` lo tanto, la clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3,51 y versiones posteriores.

Cuando el usuario ha elegido una combinación de teclas, la aplicación puede recuperar la combinación de teclas especificada del control y utilizar el mensaje WM_SETHOTKEY para configurar la tecla de acceso rápido en el sistema. Cada vez que el usuario presiona la tecla de acceso rápido, desde cualquier parte del sistema, la ventana especificada en el mensaje WM_SETHOTKEY recibe un mensaje WM_SYSCOMMAND que especifica SC_HOTKEY. Este mensaje activa la ventana que lo recibe. La tecla de acceso rápido sigue siendo válida hasta que se cierre la aplicación que llamó a WM_SETHOTKEY.

Este mecanismo es diferente de la compatibilidad con la tecla de acceso rápido que depende del mensaje WM_HOTKEY y las funciones [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) y [UnregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) de Windows.

Para obtener más información sobre `CHotKeyCtrl`el uso de, vea [controles](../../mfc/controls-mfc.md) y [usar CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="chotkeyctrl"></a>  CHotKeyCtrl::CHotKeyCtrl

Construye un objeto `CHotKeyCtrl`.

```
CHotKeyCtrl();
```

##  <a name="create"></a>  CHotKeyCtrl::Create

Crea un control de tecla de acceso rápido y lo adjunta `CHotKeyCtrl` a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de tecla de acceso rápido. Aplique cualquier combinación de estilos de control. Vea [estilos de control comunes](/windows/win32/Controls/common-control-styles) en el Windows SDK para obtener más información.

*rect*<br/>
Especifica el tamaño y la posición del control de tecla de acceso rápido. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una [estructura Rect](/windows/win32/api/windef/ns-windef-rect).

*pParentWnd*<br/>
Especifica la ventana primaria del control de tecla de acceso rápido, normalmente un [CDialog](../../mfc/reference/cdialog-class.md). No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de tecla de acceso rápido.

### <a name="return-value"></a>Valor devuelto

Distinto de cero, si la inicialización se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Un `CHotKeyCtrl` objeto se crea en dos pasos. En primer lugar, llame al constructor y `Create`, a continuación, llame `CHotKeyCtrl` a, que crea el control de tecla de acceso rápido y lo adjunta al objeto.

Si desea utilizar estilos extendidos de Windows con el control, llame a [CreateEx](#createex) en lugar `Create`de a.

##  <a name="createex"></a>  CHotKeyCtrl::CreateEx

Llame a esta función para crear un control (una ventana secundaria) y asociarlo `CHotKeyCtrl` al objeto.

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
Especifica el estilo del control de tecla de acceso rápido. Aplique cualquier combinación de estilos de control. Para obtener más información, vea [estilos de control comunes](/windows/win32/Controls/common-control-styles) en el Windows SDK.

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

##  <a name="gethotkey"></a>  CHotKeyCtrl::GetHotKey

Recupera el código de tecla virtual y los marcadores modificadores de un método abreviado de teclado de un control de tecla de acceso rápido.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Parámetros

*wVirtualKeyCode*<br/>
enuncia Código de tecla virtual del método abreviado de teclado. Para obtener una lista de códigos de tecla virtual estándar, vea Winuser. h.

*wModifiers*<br/>
enuncia Combinación bit a bit (o) de marcas que indican las teclas modificadoras del método abreviado de teclado.

Los marcadores modificadores son los siguientes:

|Marcar|Clave correspondiente|
|----------|-----------------------|
|HOTKEYF_ALT|tecla ALT|
|HOTKEYF_CONTROL|Tecla CTRL|
|HOTKEYF_EXT|Clave extendida|
|HOTKEYF_SHIFT|Tecla Mayús|

### <a name="return-value"></a>Valor devuelto

En el primer método sobrecargado, es un valor DWORD que contiene el código de tecla virtual y los marcadores de modificador. El byte de orden inferior de la palabra de orden inferior contiene el código de tecla virtual, el byte de orden superior de la palabra de orden inferior contiene las marcas modificadoras y la palabra de orden superior es cero.

### <a name="remarks"></a>Comentarios

El código de tecla virtual y las teclas modificadoras definen conjuntamente el método abreviado de teclado.

##  <a name="gethotkeyname"></a>  CHotKeyCtrl::GetHotKeyName

Llame a esta función miembro para obtener el nombre localizado de la tecla de acceso rápido.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre localizado de la tecla de acceso rápido seleccionada actualmente. Si no hay ninguna tecla de acceso rápido `GetHotKeyName` seleccionada, devuelve una cadena vacía.

### <a name="remarks"></a>Comentarios

El nombre que devuelve esta función miembro proviene del controlador del teclado. Puede instalar un controlador de teclado no localizado en una versión localizada de Windows y viceversa.

##  <a name="getkeyname"></a>  CHotKeyCtrl::GetKeyName

Llame a esta función miembro para obtener el nombre localizado de la clave asignada a un código de tecla virtual especificado.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Parámetros

*vk*<br/>
Código de tecla virtual.

*fExtended*<br/>
Si el código de tecla virtual es una clave extendida, TRUE; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Nombre localizado de la clave especificada por el parámetro *VK* . Si la clave no tiene ningún nombre asignado `GetKeyName` , devuelve una cadena vacía.

### <a name="remarks"></a>Comentarios

El nombre de clave que devuelve esta función procede del controlador de teclado, por lo que puede instalar un controlador de teclado no localizado en una versión localizada de Windows y viceversa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>  CHotKeyCtrl::SetHotKey

Establece el método abreviado de teclado para un control de tecla de acceso rápido.

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Parámetros

*wVirtualKeyCode*<br/>
de Código de tecla virtual del método abreviado de teclado. Para obtener una lista de códigos de tecla virtual estándar, vea Winuser. h.

*wModifiers*<br/>
de Combinación bit a bit (o) de marcas que indican las teclas modificadoras del método abreviado de teclado.

Los marcadores modificadores son los siguientes:

|Marcar|Clave correspondiente|
|----------|-----------------------|
|HOTKEYF_ALT|tecla ALT|
|HOTKEYF_CONTROL|Tecla CTRL|
|HOTKEYF_EXT|Clave extendida|
|HOTKEYF_SHIFT|Tecla Mayús|

### <a name="remarks"></a>Comentarios

El código de tecla virtual y las teclas modificadoras definen conjuntamente el método abreviado de teclado.

##  <a name="setrules"></a>  CHotKeyCtrl::SetRules

Llame a esta función para definir las combinaciones no válidas y la combinación de modificadores predeterminados para un control de tecla de acceso rápido.

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Parámetros

*wInvalidComb*<br/>
Matriz de marcas que especifica combinaciones de teclas no válidas. Puede ser una combinación de los siguientes valores:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE claves sin modificar

- HKCOMB_S SHIFT

- HKCOMB_SA MAYÚS + ALT

- HKCOMB_SC MAYÚS + CTRL

- HKCOMB_SCA MAYÚS + CTRL + ALT

*wModifiers*<br/>
Matriz de marcas que especifica la combinación de teclas que se va a usar cuando el usuario especifica una combinación no válida. Para obtener más información sobre las marcas modificadoras, vea [GetHotKey](#gethotkey).

### <a name="remarks"></a>Comentarios

Cuando un usuario escribe una combinación de teclas no válida, tal y como se define en las marcas especificadas en *wInvalidComb*, el sistema utiliza el operador OR para combinar las claves especificadas por el usuario con las marcas especificadas en *wModifiers*. La combinación de teclas resultante se convierte en una cadena y, a continuación, se muestra en el control de tecla de acceso rápido.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
