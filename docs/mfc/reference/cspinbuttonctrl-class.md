---
title: CSpinButtonCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSpinButtonCtrl
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CSpinButtonCtrl
- CSpinButtonCtrl class
- CSpinButtonCtrl class, common controls
- up-down controls, spin button control
- spin button control
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
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
ms.openlocfilehash: 486a0842ed04f0e760bbb332986a97a35ce9851f
ms.lasthandoff: 02/24/2017

---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl (clase)
Proporciona la funcionalidad del control de botón de número común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSpinButtonCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Construye un objeto `CSpinButtonCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSpinButtonCtrl::Create](#create)|Crea un control de botón de número y lo adjunta a un `CSpinButtonCtrl` objeto.|  
|[CSpinButtonCtrl::CreateEx](#createex)|Crea un control de botón de número con los estilos extendidos de Windows especificados y lo asocia a un `CSpinButtonCtrl` objeto.|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|Recupera información de aceleración para un control de botón de número.|  
|[CSpinButtonCtrl::GetBase](#getbase)|Recupera la base actual de un control de botón de número.|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Recupera un puntero a la ventana de contacto actual.|  
|[CSpinButtonCtrl::GetPos](#getpos)|Recupera la posición actual de un control de botón de número.|  
|[CSpinButtonCtrl::GetRange](#getrange)|Recupera los límites superiores e inferiores (intervalo) de un control de botón de número.|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|Establece la aceleración de un control de botón de número.|  
|[CSpinButtonCtrl::SetBase](#setbase)|Establece la base de un control de botón de número.|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Establece la ventana relacionada para un control de botón de número.|  
|[CSpinButtonCtrl::SetPos](#setpos)|Establece la posición actual del control.|  
|[CSpinButtonCtrl:: SetRange](#setrange)|Establece los límites superiores e inferiores (intervalo) de un control de botón de número.|  
  
## <a name="remarks"></a>Comentarios  
 Un "número control button" (también conocido como control de flechas) es un par de botones de flecha que el usuario puede hacer clic para incrementar o disminuir un valor, como una posición de desplazamiento o un número que se muestra en un control complementario. El valor asociado a un control de botón de número se llama su posición actual. Un control de botón de número se suele utilizar con un control complementario, denominado "ventana relacionada".  
  
 Este control (y por tanto la `CSpinButtonCtrl` clase) está disponible sólo para los programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 Para el usuario, un control de botón de número y su ventana relacionada a menudo parecen un único control. Puede especificar que un control de botón de número automáticamente colocarse junto a su ventana relacionada y que establece automáticamente el título de la ventana relacionada a su posición actual. Puede utilizar un control de botón de número con un control de edición para preguntar al usuario para entrada numérica.  
  
 Haga clic en la flecha hacia arriba mueve la posición actual en el valor máximo, y haga clic en la flecha hacia abajo mueve la posición actual hacia el valor mínimo. De forma predeterminada, el mínimo es 100 y el máximo es 0. Siempre que el valor mínimo es mayor que el máximo (por ejemplo, cuando se utiliza la configuración predeterminada), haga clic en las salidas de flecha hacia arriba el valor de posición y haga clic en la flecha hacia abajo aumenta.  
  
 Un control de botón de número sin ventana relacionada funciona como una especie de barra de desplazamiento simplificada. Por ejemplo, un control de pestaña muestra a veces un control de botón de número para permitir al usuario Desplazar fichas adicionales en la vista.  
  
 Para obtener más información sobre el uso de `CSpinButtonCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [CSpinButtonCtrl utilizando](../../mfc/using-cspinbuttonctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="a-namecreatea--cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::Create  
 Crea un control de botón de número y lo adjunta a un `CSpinButtonCtrl` objeto...  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control de botón de número. Aplicar cualquier combinación de estilos de control de botón de número para el control. Estos estilos se describen en [estilos de Control de flechas](http://msdn.microsoft.com/library/windows/desktop/bb759885) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `rect`  
 Especifica el tamaño y la posición del control de botón de número. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) (estructura)  
  
 `pParentWnd`  
 Un puntero a la ventana de elemento primario del control de botón de número, normalmente un `CDialog`. No debe ser **NULL.**  
  
 `nID`  
 Especifica el identificador. del control de botón de número  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la inicialización es correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CSpinButtonCtrl` objeto en dos pasos en primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de botón de número y lo adjunta a la `CSpinButtonCtrl` objeto.  
  
 Para crear un control de botón de número con estilos de ventana extendidos, llame a [CSpinButtonCtrl::CreateEx](#createex) en lugar de **crear**.  
  
##  <a name="a-namecreateexa--cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::CreateEx  
 Crea un control (una ventana secundaria) y lo asocia a la `CSpinButtonCtrl` objeto.  
  
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
 Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Especifica el estilo del control de botón de número. Aplicar cualquier combinación de estilos de control de botón de número para el control. Estos estilos se describen en [estilos de Control de flechas](http://msdn.microsoft.com/library/windows/desktop/bb759885) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
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
  
##  <a name="a-namecspinbuttonctrla--cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl  
 Construye un objeto `CSpinButtonCtrl`.  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="a-namegetaccela--cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonCtrl::GetAccel  
 Recupera información de aceleración para un control de botón de número.  
  
```  
UINT GetAccel(
    int nAccel,  
    UDACCEL* pAccel) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nAccel`  
 Número de elementos de la matriz especificada por `pAccel`.  
  
 `pAccel`  
 Puntero a una matriz de [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) estructuras que recibe información de aceleración.  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera el número de estructuras de acelerador.  
  
##  <a name="a-namegetbasea--cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl::GetBase  
 Recupera la base actual de un control de botón de número.  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor base actual.  
  
##  <a name="a-namegetbuddya--cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy  
 Recupera un puntero a la ventana de contacto actual.  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana relacionada actual.  
  
##  <a name="a-namegetposa--cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonCtrl::GetPos  
 Recupera la posición actual de un control de botón de número.  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  ```  
  
### Parameters  
 *lpbError*  
 A pointer to a boolean value that is set to zero if the value is successfully retrieved or non-zero if an error occurs. If this parameter is set to **NULL**, errors are not reported.  
  
### Return Value  
 The first version returns the 16-bit current position in the low-order word. The high-order word is nonzero if an error occurred.  
  
 The second version returns the 32-bit position.  
  
### Remarks  
 When it processes the value returned, the control updates its current position based on the caption of the buddy window. The control returns an error if there is no buddy window or if the caption specifies an invalid or out-of-range value.  
  
##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange  
 Retrieves the upper and lower limits (range) for a spin button control.  
  
```  
DWORD GetRange() const;  
  
void GetRange (int aspecto inferior,  
    int aspecto superior) const;  
  
void GetRange32 (int aspecto inferior,  
    int aspecto superior) const;  
```  
  
### Parameters  
 *lower*  
 Reference to an integer that receives the lower limit for the control.  
  
 *upper*  
 Reference to an integer that receives the upper limit for the control.  
  
### Return Value  
 The first version returns a 32-bit value containing the upper and lower limits. The low-order word is the upper limit for the control, and the high-order word is the lower limit.  
  
### Remarks  
 The member function `GetRange32` retrieves the spin button control's range as a 32-bit integer.  
  
##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel  
 Sets the acceleration for a spin button control.  
  
```  
BOOL funciones miembro SetAccel (nAccel int,  
    UDACCEL* pAccel);
```  
  
### Parameters  
 `nAccel`  
 Number of [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) structures specified by `pAccel`.  
  
 `pAccel`  
 Pointer to an array of `UDACCEL` structures, which contain acceleration information. Elements should be sorted in ascending order based on the **nSec** member.  
  
### Return Value  
 Nonzero if successful; otherwise 0.  
  
##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase  
 Sets the base for a spin button control.  
  
```  
int SetBase (int nBase);
```  
  
### Parameters  
 `nBase`  
 New base value for the control. It can be 10 for decimal or 16 for hexadecimal.  
  
### Return Value  
 The previous base value if successful, or zero if an invalid base is given.  
  
### Remarks  
 The base value determines whether the buddy window displays numbers in decimal or hexadecimal digits. Hexadecimal numbers are always unsigned; decimal numbers are signed.  
  
##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy  
 Sets the buddy window for a spin button control.  
  
```  
CWnd* SetBuddy (CWnd* pWndBuddy);
```  
  
### Parameters  
 `pWndBuddy`  
 Pointer to the new buddy window.  
  
### Return Value  
 A pointer to the previous buddy window.  
  
### Remarks  
 A spin control is almost always associated with another window, such as an edit control, that displays some content. This other window is called the "buddy" of the spin control.  
  
##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos  
 Sets the current position for a spin button control.  
  
```  
int SetPos (int nPos);  
int SetPos32(int nPos);
```  
  
### Parameters  
 `nPos`  
 New position for the control. This value must be in the range specified by the upper and lower limits for the control.  
  
### Return Value  
 The previous position (16-bit precision for `SetPos`, 32-bit precision for `SetPos32`).  
  
### Remarks  
 `SetPos32` sets the 32-bit position.  
  
##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange  
 Sets the upper and lower limits (range) for a spin button control.  
  
```  
void SetRange (short nLower,  
    breve nUpper);

 
void SetRange32 (nLower int,  
    int nUpper);
```  
  
### Parameters  
 `nLower`and `nUpper`  
 Upper and lower limits for the control. For `SetRange`, neither limit can be greater than **UD_MAXVAL** or less than **UD_MINVAL**; in addition, the difference between the two limits cannot exceed **UD_MAXVAL**. `SetRange32` places no restrictions on the limits; use any integers.  
  
### Remarks  
 The member function `SetRange32` sets the 32-bit range for the spin button control.  
  
> [!NOTE]
>  The default range for the spin button has the maximum set to zero (0) and the minimum set to 100. Because the maximum value is less than the minimum value, clicking the up arrow will decrease the position and clicking the down arrow will increase it. Use `CSpinButtonCtrl::SetRange` to adjust these values.  
  
## See Also  
 [MFC Sample CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd Class](../../mfc/reference/cwnd-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl Class](../../mfc/reference/csliderctrl-class.md)

