---
title: CHotKeyCtrl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 590914ac312a4f998eb759beb08ed2e7935874fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368757"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl (clase)
Proporciona la funcionalidad del control común de tecla de acceso rápido de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CHotKeyCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Construye un objeto `CHotKeyCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHotKeyCtrl::Create](#create)|Crea un control de tecla de acceso rápido y lo adjunta a un `CHotKeyCtrl` objeto.|  
|[CHotKeyCtrl::CreateEx](#createex)|Crea un control de tecla de acceso rápido con los estilos extendidos de Windows especificados y lo adjunta a un `CHotKeyCtrl` objeto.|  
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Recupera las marcas de código y el modificador virtuales claves de una tecla de acceso rápido de un control de tecla de acceso rápido.|  
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Recupera el nombre de clave, en el conjunto de caracteres locales, que se asigna a una tecla de acceso rápido.|  
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Recupera el nombre de clave, en el juego de caracteres local asignado para el código de tecla virtual especificado.|  
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Establece la combinación de teclas de acceso rápida para un control de tecla de acceso rápido.|  
|[CHotKeyCtrl::SetRules](#setrules)|Define las combinaciones no válidas y la combinación de modificador predeterminado para un control de tecla de acceso rápido.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control hot key" es una ventana que permite al usuario crear una tecla de acceso rápido. Una "tecla de acceso rápido" es una combinación de teclas que el usuario puede presionar para realizar una acción rápidamente. (Por ejemplo, un usuario puede crear una tecla de acceso rápido que activa una ventana determinada y la pone en la parte superior del orden Z). El control de tecla de acceso rápido muestra las opciones del usuario y se asegura de que el usuario selecciona una combinación de teclas válida.  
  
 Este control (y, por tanto, la `CHotKeyCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 Cuando el usuario ha elegido una combinación de teclas, la aplicación puede recuperar la combinación de teclas especificada desde el control y utilizar el **mensaje WM_SETHOTKEY** mensaje para establecer la tecla de acceso rápido en el sistema. Cada vez que el usuario presiona la tecla de acceso rápido a partir de ahí, desde cualquier parte del sistema, la ventana especificada en el **mensaje WM_SETHOTKEY** mensaje recibe un `WM_SYSCOMMAND` mensaje especificando **SC_HOTKEY**. Este mensaje activa la ventana que lo recibe. La tecla de acceso rápido sigue siendo válida hasta que la aplicación que llama **mensaje WM_SETHOTKEY** se cierra.  
  
 Este mecanismo es diferente de la compatibilidad de clave activa que depende la **WM_HOTKEY** mensaje y las ventanas [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309) y [UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327) funciones.  
  
 Para obtener más información sobre el uso de `CHotKeyCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).  
  
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
 Crea un control de tecla de acceso rápido y lo adjunta a un `CHotKeyCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control clave activa. Aplicar cualquier combinación de estilos de control. Vea [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) en el SDK de Windows para obtener más información.  
  
 `rect`  
 Especifica el tamaño y la posición del control clave activo. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [estructura RECT](../../mfc/reference/rect-structure1.md).  
  
 `pParentWnd`  
 Especifica la activa clave ventana del control primario, normalmente un [CDialog](../../mfc/reference/cdialog-class.md). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control clave activa  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero, si la inicialización se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CHotKeyCtrl` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de tecla de acceso rápido y lo adjunta a la `CHotKeyCtrl` objeto.  
  
 Si desea utilizar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de **crear**.  
  
##  <a name="createex"></a>  CHotKeyCtrl::CreateEx  
 Llame a esta función para crear un control (una ventana secundaria) y asociarlo con el `CHotKeyCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) del SDK de Windows.  
  
 `dwStyle`  
 Especifica el estilo del control clave activa. Aplicar cualquier combinación de estilos de control. Para obtener más información, consulte [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) del SDK de Windows.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente de `pParentWnd`.  
  
 `pParentWnd`  
 Un puntero a la ventana que es primario del control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="gethotkey"></a>  CHotKeyCtrl::GetHotKey  
 Recupera las marcas de código y el modificador virtuales teclas de método abreviado de teclado de un control de tecla de acceso rápido.  
  
```  
DWORD GetHotKey() const;  
  
void GetHotKey(
    WORD& wVirtualKeyCode,  
    WORD& wModifiers) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `wVirtualKeyCode`  
 Código de tecla virtual de método abreviado de teclado. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h.  
  
 [out] `wModifiers`  
 Una combinación bit a bit (OR) de marcas que indican las teclas modificadoras en el método abreviado de teclado.  
  
 Los indicadores modificadores son los siguientes:  
  
|Marcar|Clave correspondiente|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|tecla ALT|  
|`HOTKEYF_CONTROL`|Tecla CTRL|  
|`HOTKEYF_EXT`|Clave extendida|  
|`HOTKEYF_SHIFT`|Tecla MAYÚS|  
  
### <a name="return-value"></a>Valor devuelto  
 En el primer método sobrecargado, un `DWORD` que contiene las marcas de código y el modificador claves virtuales. El byte de orden inferior de la palabra de orden inferior contiene el código de tecla virtual, el byte de orden superior de la palabra de orden inferior contiene las marcas de modificador y la palabra de orden superior es cero.  
  
### <a name="remarks"></a>Comentarios  
 El código de tecla virtual y las teclas modificadoras juntas definen el método abreviado de teclado.  
  
##  <a name="gethotkeyname"></a>  CHotKeyCtrl::GetHotKeyName  
 Llame a esta función miembro para obtener el nombre traducido de la tecla de acceso rápido.  
  
```  
CString GetHotKeyName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre localizado de la tecla de acceso rápido actualmente seleccionado. Si no hay ninguna tecla de acceso rápido, `GetHotKeyName` devuelve una cadena vacía.  
  
### <a name="remarks"></a>Comentarios  
 El nombre que devuelve esta función miembro procede del controlador de teclado. Puede instalar un controlador de teclado no localizada en una versión localizada de Windows y viceversa.  
  
##  <a name="getkeyname"></a>  CHotKeyCtrl::GetKeyName  
 Llame a esta función miembro para obtener el nombre traducido de la clave asignada a un código de tecla virtual especificado.  
  
```  
static CString GetKeyName(
    UINT vk,  
    BOOL fExtended);
```  
  
### <a name="parameters"></a>Parámetros  
 `vk`  
 El código de tecla virtual.  
  
 *fExtended*  
 Si el código de tecla virtual es una clave extendida, **TRUE**; en caso contrario **FALSE**.  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre localizado de la clave especificada por el `vk` parámetro. Si la clave no tiene ningún nombre asignado, `GetKeyName` devuelve una cadena vacía.  
  
### <a name="remarks"></a>Comentarios  
 Incluye el nombre de clave que devuelve esta función desde el controlador de teclado, por lo que puede instalar un controlador de teclado no localizada en una versión localizada de Windows y viceversa.  
  
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
 [in] `wVirtualKeyCode`  
 Código de tecla virtual de método abreviado de teclado. Para obtener una lista de códigos de tecla virtuales estándares, vea Winuser.h.  
  
 [in] `wModifiers`  
 Una combinación bit a bit (OR) de marcas que indican las teclas modificadoras en el método abreviado de teclado.  
  
 Los indicadores modificadores son los siguientes:  
  
|Marcar|Clave correspondiente|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|tecla ALT|  
|`HOTKEYF_CONTROL`|Tecla CTRL|  
|`HOTKEYF_EXT`|Clave extendida|  
|`HOTKEYF_SHIFT`|Tecla MAYÚS|  
  
### <a name="remarks"></a>Comentarios  
 El código de tecla virtual y las teclas modificadoras juntas definen el método abreviado de teclado.  
  
##  <a name="setrules"></a>  CHotKeyCtrl::SetRules  
 Llame a esta función para definir las combinaciones no válidas y la combinación de modificador predeterminado para un control de tecla de acceso rápido.  
  
```  
void SetRules(
    WORD wInvalidComb,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>Parámetros  
 `wInvalidComb`  
 Matriz de marcas que especifica las combinaciones de teclas no válidas. Puede ser una combinación de los siguientes valores:  
  
- `HKCOMB_A` ALT  
  
- `HKCOMB_C` CTRL  
  
- `HKCOMB_CA` CTRL + ALT  
  
- `HKCOMB_NONE` Claves no modificadas  
  
- `HKCOMB_S` TECLA MAYÚS  
  
- `HKCOMB_SA` MAYÚS + ALT  
  
- `HKCOMB_SC` MAYÚS + CTRL  
  
- `HKCOMB_SCA` MAYÚS + CTRL + ALT  
  
 `wModifiers`  
 Matriz de marcas que especifica la combinación de teclas que se usará cuando el usuario especifica una combinación no válida. Para obtener más información sobre las marcas de modificador, consulte [GetHotKey](#gethotkey).  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario especifica una combinación de teclas no válida, tal como se define por marcas especificadas en `wInvalidComb`, el sistema usa el operador OR para combinar las claves especificadas por el usuario con las marcas especificadas en `wModifiers`. La combinación de teclas resultante se convierte en una cadena y, a continuación, se muestra en el control de tecla de acceso rápido.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



