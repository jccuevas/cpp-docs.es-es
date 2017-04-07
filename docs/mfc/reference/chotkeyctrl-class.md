---
title: CHotKeyCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- hot key controls
- CHotKeyCtrl class
- Windows common controls [C++], CHotKeyCtrl
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: cbcc720d2b934cde9f8beb9bb95499d9cc569413
ms.lasthandoff: 02/24/2017

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
|[CHotKeyCtrl::Create](#create)|Crea un control de tecla de acceso rápido y lo adjunta a un `CHotKeyCtrl` objeto.|  
|[CHotKeyCtrl::CreateEx](#createex)|Crea un control de tecla de acceso rápido con los estilos extendidos de Windows especificados y lo asocia a un `CHotKeyCtrl` objeto.|  
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Recupera las marcas de código y el modificador virtuales teclas de método abreviado de un control de tecla de acceso rápido.|  
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Recupera el nombre de clave en el conjunto de caracteres locales, asignado a una tecla de acceso rápido.|  
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Recupera el nombre de clave en el juego de caracteres local asignado para el código de tecla virtual especificado.|  
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Establece la combinación de teclas de acceso rápida para un control de tecla de acceso rápido.|  
|[CHotKeyCtrl::SetRules](#setrules)|Define las combinaciones no válidas y la combinación de modificador predeterminado para un control de tecla de acceso rápido.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control hot key" es una ventana que permite al usuario crear una tecla de acceso rápido. Una "tecla de acceso rápido" es una combinación de teclas que presiona el usuario para realizar una acción rápidamente. (Por ejemplo, un usuario puede crear una tecla de acceso rápido que activa una ventana determinada y la pone en la parte superior del orden Z). El control de tecla de acceso rápido muestra las opciones del usuario y garantiza que el usuario selecciona una combinación de teclas válida.  
  
 Este control (y por tanto la `CHotKeyCtrl` clase) está disponible sólo para los programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 Cuando el usuario ha elegido una combinación de teclas, la aplicación puede recuperar la combinación de teclas especificada en el control y utilice la **mensaje WM_SETHOTKEY** mensaje para establecer la tecla de acceso rápido en el sistema. Cuando el usuario presiona la tecla de acceso rápido a partir de entonces, desde cualquier parte del sistema, la ventana especificada en el **mensaje WM_SETHOTKEY** mensaje recibe un `WM_SYSCOMMAND` mensaje especificando **SC_HOTKEY**. Este mensaje activa la ventana que lo recibe. La tecla de acceso rápido sigue siendo válida hasta que la aplicación que llama **mensaje WM_SETHOTKEY** sale.  
  
 Este mecanismo es diferente de la compatibilidad de clave activa que depende de la **WM_HOTKEY** mensaje y Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309) y [UnregisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646327) funciones.  
  
 Para obtener más información sobre el uso de `CHotKeyCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [CHotKeyCtrl utilizando](../../mfc/using-chotkeyctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHotKeyCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl  
 Construye un objeto `CHotKeyCtrl`.  
  
```  
CHotKeyCtrl();
```  
  
##  <a name="create"></a>CHotKeyCtrl::Create  
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
 Especifica el estilo del control clave activa. Aplicar cualquier combinación de estilos de control. Consulte [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información.  
  
 `rect`  
 Especifica el tamaño y la posición del control clave activo. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [estructura RECT](../../mfc/reference/rect-structure1.md).  
  
 `pParentWnd`  
 Especifica el activo clave ventana primaria de control, normalmente un [CDialog](../../mfc/reference/cdialog-class.md). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control clave activa  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero, si la inicialización es correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CHotKeyCtrl` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de tecla de acceso rápido y lo adjunta a la `CHotKeyCtrl` objeto.  
  
 Si desea utilizar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de **crear**.  
  
##  <a name="createex"></a>CHotKeyCtrl::CreateEx  
 Llame a esta función para crear un control (una ventana secundaria) y asociarla con el `CHotKeyCtrl` objeto.  
  
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
 Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Especifica el estilo del control clave activa. Aplicar cualquier combinación de estilos de control. Para obtener más información, consulte [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente `pParentWnd`.  
  
 `pParentWnd`  
 Puntero a la ventana que es principal el control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="gethotkey"></a>CHotKeyCtrl::GetHotKey  
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
  
 Los marcadores modificadores son los siguientes:  
  
|Marcar|Clave correspondiente|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|tecla ALT|  
|`HOTKEYF_CONTROL`|Tecla CTRL|  
|`HOTKEYF_EXT`|Clave extendida|  
|`HOTKEYF_SHIFT`|Tecla MAYÚS|  
  
### <a name="return-value"></a>Valor devuelto  
 En el primer método sobrecargado, un `DWORD` que contiene los marcadores de código y el modificador claves virtuales. El byte de orden inferior de la palabra de orden inferior contiene el código de clave virtual, el byte de orden superior de la palabra de orden inferior contiene los marcadores modificadores y la palabra de orden superior es cero.  
  
### <a name="remarks"></a>Comentarios  
 El código de tecla virtual y las teclas modificadoras juntas definen el método abreviado de teclado.  
  
##  <a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName  
 Llame a esta función miembro para obtener el nombre traducido de la tecla de acceso rápido.  
  
```  
CString GetHotKeyName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre traducido de la tecla de acceso rápido seleccionada actualmente. Si no hay ninguna tecla de acceso rápido, `GetHotKeyName` devuelve una cadena vacía.  
  
### <a name="remarks"></a>Comentarios  
 El nombre que devuelve esta función miembro procede el controlador de teclado. Puede instalar un controlador de teclado no localizada en una versión localizada de Windows y viceversa.  
  
##  <a name="getkeyname"></a>CHotKeyCtrl::GetKeyName  
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
 Esta función devuelve el nombre de clave proviene el controlador de teclado, por lo que puede instalar un controlador de teclado no localizada en una versión localizada de Windows y viceversa.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog&#69;](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]  
  
##  <a name="sethotkey"></a>CHotKeyCtrl::SetHotKey  
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
  
 Los marcadores modificadores son los siguientes:  
  
|Marcar|Clave correspondiente|  
|----------|-----------------------|  
|`HOTKEYF_ALT`|tecla ALT|  
|`HOTKEYF_CONTROL`|Tecla CTRL|  
|`HOTKEYF_EXT`|Clave extendida|  
|`HOTKEYF_SHIFT`|Tecla MAYÚS|  
  
### <a name="remarks"></a>Comentarios  
 El código de tecla virtual y las teclas modificadoras juntas definen el método abreviado de teclado.  
  
##  <a name="setrules"></a>CHotKeyCtrl::SetRules  
 Llame a esta función para definir las combinaciones no válidas y la combinación de modificador predeterminado para un control de tecla de acceso rápido.  
  
```  
void SetRules(
    WORD wInvalidComb,  
    WORD wModifiers);
```  
  
### <a name="parameters"></a>Parámetros  
 `wInvalidComb`  
 Matriz de indicadores que especifica las combinaciones de teclas no válidas. Puede ser una combinación de los siguientes valores:  
  
- `HKCOMB_A`ALT  
  
- `HKCOMB_C`CTRL  
  
- `HKCOMB_CA`CTRL + ALT  
  
- `HKCOMB_NONE`Claves no modificadas  
  
- `HKCOMB_S`MAYÚS  
  
- `HKCOMB_SA`MAYÚS + ALT  
  
- `HKCOMB_SC`MAYÚS + CTRL  
  
- `HKCOMB_SCA`MAYÚS + CTRL + ALT  
  
 `wModifiers`  
 Matriz de indicadores que especifica la combinación de teclas que se usará cuando el usuario especifica una combinación no válida. Para obtener más información sobre los marcadores modificadores, vea [GetHotKey](#gethotkey).  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario introduce una combinación de clave no válida, de acuerdo con las marcas especificadas en `wInvalidComb`, el sistema utiliza el operador OR para combinar las claves escritas por el usuario con las marcas especificadas en `wModifiers`. La combinación de teclas resultante se convierte en una cadena y, a continuación, se muestra en el control de tecla de acceso rápido.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)




