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
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 91be67ccbf1fb7fb863aa4072d55bb3f330aa44f
ms.lasthandoff: 04/04/2017

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
|[CSpinButtonCtrl::CreateEx](#createex)|Crea un control de botón de número con los estilos extendidos de Windows especificados y lo adjunta a un `CSpinButtonCtrl` objeto.|  
|[CSpinButtonCtrl::GetAccel](#getaccel)|Recupera información de aceleración para un control de botón de número.|  
|[CSpinButtonCtrl::GetBase](#getbase)|Recupera la base actual para un control de botón de número.|  
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Recupera un puntero a la ventana relacionada actual.|  
|[CSpinButtonCtrl::GetPos](#getpos)|Recupera la posición actual de un control de botón de número.|  
|[CSpinButtonCtrl::GetRange](#getrange)|Recupera los límites superiores e inferiores (intervalo) para un control de botón de número.|  
|[CSpinButtonCtrl::SetAccel](#setaccel)|Establece la aceleración de un control de botón de número.|  
|[CSpinButtonCtrl::SetBase](#setbase)|Establece la base para un control de botón de número.|  
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Establece la ventana relacionada para un control de botón de número.|  
|[CSpinButtonCtrl::SetPos](#setpos)|Establece la posición actual del control.|  
|[CSpinButtonCtrl:: SetRange](#setrange)|Establece los límites superiores e inferiores (intervalo) para un control de botón de número.|  
  
## <a name="remarks"></a>Comentarios  
 Un "número control button" (también conocido como un control de flechas) es un par de botones de flecha que el usuario puede hacer clic para incrementar o disminuir un valor, como una posición de desplazamiento o un número que aparece en un control complementario. El valor asociado a un control de botón de número se llama a su posición actual. Un control de botón de número se suele utilizar con un control complementario, denominado "ventana relacionada".  
  
 Este control (y, por tanto, la `CSpinButtonCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 Para el usuario, un control de botón de número y su ventana relacionada a menudo parecen un control único. Puede especificar que un control de botón de número automáticamente colocarse junto a su ventana relacionada, y que establece automáticamente el título de la ventana relacionada en su posición actual. Puede utilizar un control de botón de número con un control de edición para preguntar al usuario para entrada numérica.  
  
 Haga clic en la flecha hacia arriba mueve la posición actual en el valor máximo, y haga clic en la flecha hacia abajo mueve la posición actual hacia el valor mínimo. De forma predeterminada, el valor mínimo es 100 y el máximo es 0. Siempre que el valor mínimo es mayor que el máximo configurado (por ejemplo, cuando se usa la configuración predeterminada), haga clic en se reduzca en la flecha hacia arriba el valor de posición y haga clic en la flecha hacia abajo aumenta.  
  
 Un control de botón de número sin ventana relacionada funciona como un tipo de barra de desplazamiento simplificada. Por ejemplo, un control de pestaña muestra a veces un control de botón de número para permitir al usuario desplazar las fichas adicionales en la vista.  
  
 Para obtener más información sobre el uso de `CSpinButtonCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSpinButtonCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="create"></a>CSpinButtonCtrl::Create  
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
 Especifica el tamaño y la posición del control de botón de número. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura  
  
 `pParentWnd`  
 Un puntero a la ventana del elemento primario del control de botón de número, normalmente un `CDialog`. No debe ser **NULL.**  
  
 `nID`  
 Especifica el identificador. del control de botón de número  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CSpinButtonCtrl` de dos pasos en primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de botón de número y lo adjunta a la `CSpinButtonCtrl` objeto.  
  
 Para crear un control de botón de número con estilos de ventana extendidos, llame a [CSpinButtonCtrl::CreateEx](#createex) en lugar de **crear**.  
  
##  <a name="createex"></a>CSpinButtonCtrl::CreateEx  
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
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos extendidos de windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Especifica el estilo del control de botón de número. Aplicar cualquier combinación de estilos de control de botón de número para el control. Estos estilos se describen en [estilos de Control de flechas](http://msdn.microsoft.com/library/windows/desktop/bb759885) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
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
  
##  <a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl  
 Construye un objeto `CSpinButtonCtrl`.  
  
```  
CSpinButtonCtrl();
```  
  
##  <a name="getaccel"></a>CSpinButtonCtrl::GetAccel  
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
 Recupera el número de estructuras de aceleración.  
  
##  <a name="getbase"></a>CSpinButtonCtrl::GetBase  
 Recupera la base actual para un control de botón de número.  
  
```  
UINT GetBase() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor base actual.  
  
##  <a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy  
 Recupera un puntero a la ventana relacionada actual.  
  
```  
CWnd* GetBuddy() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana relacionada actual.  
  
##  <a name="getpos"></a>CSpinButtonCtrl::GetPos  
 Recupera la posición actual de un control de botón de número.  
  
```  
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *lpbError*  
 Un puntero a un valor booleano que se establece en cero si el valor se recuperó correctamente o que se distinto de cero si se produce un error. Si este parámetro se establece en **NULL**, no se notifican los errores.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera versión devuelve la posición actual de 16 bits en la palabra de orden inferior. La palabra de orden superior es distinto de cero si se produjo un error.  
  
 La segunda versión devuelve la posición de 32 bits.  
  
### <a name="remarks"></a>Comentarios  
 Cuando procesa el valor devuelto, el control actualiza su posición actual basándose en el título de la ventana relacionada. El control devuelve un error si no hay ninguna ventana relacionada o si el título especifica un valor no válido o fuera de intervalo.  
  
##  <a name="getrange"></a>CSpinButtonCtrl::GetRange  
 Recupera los límites superiores e inferiores (intervalo) para un control de botón de número.  
  
```  
DWORD GetRange() const;  
  
void GetRange(
    int& lower,  
    int& upper) const;  
  
void GetRange32(
    int& lower,  
    int &upper) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *inferior*  
 Referencia a un entero que recibe el límite inferior para el control.  
  
 *superior*  
 Referencia a un entero que recibe el límite superior para el control.  
  
### <a name="return-value"></a>Valor devuelto  
 La primera versión devuelve un valor de 32 bits que contiene los límites superiores e inferiores. La palabra de orden inferior es el límite superior para el control y la palabra de orden superior es el límite inferior.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro `GetRange32` recupera el intervalo del control de botón de número como un entero de 32 bits.  
  
##  <a name="setaccel"></a>CSpinButtonCtrl::SetAccel  
 Establece la aceleración de un control de botón de número.  
  
```  
BOOL SetAccel(
    int nAccel,  
    UDACCEL* pAccel);
```  
  
### <a name="parameters"></a>Parámetros  
 `nAccel`  
 Número de [UDACCEL](http://msdn.microsoft.com/library/windows/desktop/bb759897) estructuras especificadas por `pAccel`.  
  
 `pAccel`  
 Puntero a una matriz de `UDACCEL` las estructuras, que contienen información de aceleración. Los elementos se deben ordenar en orden ascendente según la **nSec** miembro.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="setbase"></a>CSpinButtonCtrl::SetBase  
 Establece la base para un control de botón de número.  
  
```  
int SetBase(int nBase);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBase`  
 Nuevo valor de base para el control. Puede ser 10 para decimales o 16 en formato hexadecimal.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor base anterior si se realiza correctamente, o cero si no se proporciona una base no válida.  
  
### <a name="remarks"></a>Comentarios  
 El valor base determina si la ventana relacionada muestra los números de dígitos decimales o hexadecimales. Números hexadecimales siempre están firmados; se firman los números decimales.  
  
##  <a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy  
 Establece la ventana relacionada para un control de botón de número.  
  
```  
CWnd* SetBuddy(CWnd* pWndBuddy);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndBuddy`  
 Puntero a la nueva ventana relacionada.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana relacionada anterior.  
  
### <a name="remarks"></a>Comentarios  
 Un control de número casi siempre se asocia con otra ventana, por ejemplo, un control de edición, que muestra la parte del contenido. Esta otra ventana se denomina a "conocidos" del control de número.  
  
##  <a name="setpos"></a>CSpinButtonCtrl::SetPos  
 Establece la posición actual de un control de botón de número.  
  
```  
int SetPos(int nPos);  
int SetPos32(int nPos);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Nueva posición del control. Este valor debe ser en el intervalo especificado por los límites superiores e inferiores del control.  
  
### <a name="return-value"></a>Valor devuelto  
 La posición anterior (precisión de 16 bits para `SetPos`, 32 bits precisión para `SetPos32`).  
  
### <a name="remarks"></a>Comentarios  
 `SetPos32`establece la posición de 32 bits.  
  
##  <a name="setrange"></a>CSpinButtonCtrl:: SetRange  
 Establece los límites superiores e inferiores (intervalo) para un control de botón de número.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Parámetros  
 `nLower` y `nUpper`  
 Límites superior e inferior del control. Para `SetRange`, ningún límite puede ser mayor que **UD_MAXVAL** o menor que **UD_MINVAL**; Además, no puede superar la diferencia entre los dos límites **UD_MAXVAL**. `SetRange32`impone ninguna restricción sobre los límites; utilizar los enteros.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro `SetRange32` establece el intervalo de 32 bits para el control de botón de número.  
  
> [!NOTE]
>  El intervalo predeterminado para el botón de número tiene el máximo establecido en cero (0) y el mínimo establecido en 100. Dado que el valor máximo es menor que el valor mínimo, al hacer clic en la flecha arriba se reducirá la posición y al hacer clic en la flecha hacia abajo, aumentará. Use `CSpinButtonCtrl::SetRange` para ajustar estos valores.  
  
## <a name="see-also"></a>Vea también  
 [CMNCTRL2 de ejemplo MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CSliderCtrl (clase)](../../mfc/reference/csliderctrl-class.md)

