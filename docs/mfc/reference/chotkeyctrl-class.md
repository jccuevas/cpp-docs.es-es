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
ms.openlocfilehash: 758fb78fbd4e25a0e2fb8cea300c5371ece04fb4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366880"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl (clase)

Proporciona la funcionalidad del control común de tecla de acceso rápido de Windows.

## <a name="syntax"></a>Sintaxis

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Construye un objeto `CHotKeyCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHotKeyCtrl::Crear](#create)|Crea un control de tecla de `CHotKeyCtrl` acceso rápido y lo adjunta a un objeto.|
|[CHotKeyCtrl::CreateEx](#createex)|Crea un control de tecla de acceso rápido con `CHotKeyCtrl` los estilos extendidos de Windows especificados y lo asocia a un objeto.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Recupera el código de clave virtual y los indicadores modificadores de una tecla de acceso rápido de un control de tecla de acceso rápido.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Recupera el nombre de clave, en el juego de caracteres local, asignado a una tecla de acceso rápido.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Recupera el nombre de clave, en el juego de caracteres local, asignado al código de clave virtual especificado.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Establece la combinación de teclas de acceso rápido para un control de tecla de acceso rápido.|
|[CHotKeyCtrl::SetRules](#setrules)|Define las combinaciones no válidas y la combinación de modificadores predeterminada para un control de tecla de acceso rápido.|

## <a name="remarks"></a>Observaciones

Un "control de teclas de acceso rápido" es una ventana que permite al usuario crear una tecla de acceso rápido. Una "tecla de acceso rápido" es una combinación de teclas que el usuario puede presionar para realizar una acción rápidamente. (Por ejemplo, un usuario puede crear una tecla de acceso rápido que active una ventana determinada y la lleva a la parte superior del orden Z.) El control de tecla de acceso rápido muestra las opciones del usuario y garantiza que el usuario selecciona una combinación de teclas válida.

Este control (y, por lo tanto, la `CHotKeyCtrl` clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Cuando el usuario ha elegido una combinación de teclas, la aplicación puede recuperar la combinación de teclas especificada del control y utilizar el mensaje de WM_SETHOTKEY para configurar la tecla de acceso rápido en el sistema. Cada vez que el usuario presiona la tecla de acceso rápido a partir de entonces, desde cualquier parte del sistema, la ventana especificada en el mensaje WM_SETHOTKEY recibe un mensaje WM_SYSCOMMAND especificando SC_HOTKEY. Este mensaje activa la ventana que lo recibe. La tecla de acceso rápido sigue siendo válida hasta que se cierra la aplicación que llamó a WM_SETHOTKEY.

Este mecanismo es diferente de la compatibilidad con teclas de acceso rápido que depende del mensaje WM_HOTKEY y las funciones [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) y [UnregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) de Windows.

Para obtener más `CHotKeyCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y uso de [CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl

Construye un objeto `CHotKeyCtrl`.

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a>CHotKeyCtrl::Crear

Crea un control de tecla de `CHotKeyCtrl` acceso rápido y lo adjunta a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de tecla de acceso rápido. Aplique cualquier combinación de estilos de control. Consulte [Estilos](/windows/win32/Controls/common-control-styles) de control comunes en el Windows SDK para obtener más información.

*Rect*<br/>
Especifica el tamaño y la posición del control de tecla de acceso rápido. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una [estructura RECT](/windows/win32/api/windef/ns-windef-rect).

*pParentWnd*<br/>
Especifica la ventana primaria del control de tecla de acceso rápido, normalmente un [CDialog](../../mfc/reference/cdialog-class.md). No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de tecla de acceso rápido.

### <a name="return-value"></a>Valor devuelto

Distinto de cero, si la inicialización se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Construir un `CHotKeyCtrl` objeto en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CHotKeyCtrl` llame a , que crea el control de tecla de acceso rápido y lo adjunta al objeto.

Si desea utilizar estilos de ventanas extendidas `Create`con el control, llame a [CreateEx](#createex) en lugar de .

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a>CHotKeyCtrl::CreateEx

Llame a esta función para crear un control `CHotKeyCtrl` (una ventana secundaria) y asociarlo con el objeto.

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
Especifica el estilo del control de tecla de acceso rápido. Aplique cualquier combinación de estilos de control. Para obtener más información, consulte [Estilos](/windows/win32/Controls/common-control-styles) de control comunes en el Windows SDK.

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

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a>CHotKeyCtrl::GetHotKey

Recupera el código de clave virtual y los indicadores modificadores de un método abreviado de teclado de un control de tecla de acceso rápido.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Parámetros

*wVirtualKeyCode*<br/>
[fuera] Código de tecla virtual del método abreviado de teclado. Para obtener una lista de códigos de clave virtuales estándar, consulte Winuser.h.

*wModifiers*<br/>
[fuera] Una combinación bit a bit (OR) de indicadores que indican las teclas modificadoras en el método abreviado de teclado.

Los indicadores modificadores son los siguientes:

|Marca|Llave correspondiente|
|----------|-----------------------|
|HOTKEYF_ALT|tecla ALT|
|HOTKEYF_CONTROL|Tecla CTRL|
|HOTKEYF_EXT|Llave extendida|
|HOTKEYF_SHIFT|Tecla SHIFT|

### <a name="return-value"></a>Valor devuelto

En el primer método sobrecargado, un DWORD que contiene el código de clave virtual y los indicadores modificadores. El byte de orden inferior de la palabra de orden inferior contiene el código de clave virtual, el byte de orden superior de la palabra de orden inferior contiene los indicadores modificadores y la palabra de orden superior es cero.

### <a name="remarks"></a>Observaciones

El código de tecla virtual y las teclas modificadoras juntos definen el método abreviado de teclado.

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName

Llame a esta función miembro para obtener el nombre localizado de la tecla de acceso rápido.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre localizado de la tecla de acceso rápido seleccionada actualmente. Si no hay ninguna `GetHotKeyName` tecla de acceso rápido seleccionada, devuelve una cadena vacía.

### <a name="remarks"></a>Observaciones

El nombre que devuelve esta función miembro procede del controlador de teclado. Puede instalar un controlador de teclado no localizado en una versión localizada de Windows y viceversa.

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a>CHotKeyCtrl::GetKeyName

Llame a esta función miembro para obtener el nombre localizado de la clave asignada a un código de clave virtual especificado.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Parámetros

*Vk*<br/>
El código de clave virtual.

*fExtended*<br/>
Si el código de clave virtual es una clave extendida, TRUE; de lo contrario FALSO.

### <a name="return-value"></a>Valor devuelto

El nombre localizado de la clave especificada por el parámetro *vk.* Si la clave no `GetKeyName` tiene ningún nombre asignado, devuelve una cadena vacía.

### <a name="remarks"></a>Observaciones

El nombre de clave que devuelve esta función procede del controlador de teclado, por lo que puede instalar un controlador de teclado no localizado en una versión localizada de Windows y viceversa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a>CHotKeyCtrl::SetHotKey

Establece el método abreviado de teclado para un control de tecla de acceso rápido.

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Parámetros

*wVirtualKeyCode*<br/>
[en] Código de tecla virtual del método abreviado de teclado. Para obtener una lista de códigos de clave virtuales estándar, consulte Winuser.h.

*wModifiers*<br/>
[en] Una combinación bit a bit (OR) de indicadores que indican las teclas modificadoras en el método abreviado de teclado.

Los indicadores modificadores son los siguientes:

|Marca|Llave correspondiente|
|----------|-----------------------|
|HOTKEYF_ALT|tecla ALT|
|HOTKEYF_CONTROL|Tecla CTRL|
|HOTKEYF_EXT|Llave extendida|
|HOTKEYF_SHIFT|Tecla SHIFT|

### <a name="remarks"></a>Observaciones

El código de tecla virtual y las teclas modificadoras juntos definen el método abreviado de teclado.

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a>CHotKeyCtrl::SetRules

Llame a esta función para definir las combinaciones no válidas y la combinación de modificadores predeterminada para un control de tecla de acceso rápido.

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Parámetros

*wInvalidComb*<br/>
Matriz de indicadores que especifica combinaciones de teclas no válidas. Puede ser una combinación de los siguientes valores:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL+ALT

- HKCOMB_NONE claves sin modificar

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT+ALT

- HKCOMB_SC SHIFT+CTRL

- HKCOMB_SCA SHIFT+CTRL+ALT

*wModifiers*<br/>
Matriz de indicadores que especifica la combinación de teclas que se usará cuando el usuario escriba una combinación no válida. Para obtener más información sobre los indicadores modificadores, vea [GetHotKey](#gethotkey).

### <a name="remarks"></a>Observaciones

Cuando un usuario escribe una combinación de claves no válida, tal como se define en los indicadores especificados en *wInvalidComb*, el sistema utiliza el operador OR para combinar las claves introducidas por el usuario con las marcas especificadas en *wModifiers*. La combinación de teclas resultante se convierte en una cadena y, a continuación, se muestra en el control de tecla de acceso rápido.

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
