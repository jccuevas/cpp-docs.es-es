---
title: CControlBar (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
dev_langs:
- C++
helpviewer_keywords:
- CControlBar class
- OLE resize bars
- OLE resize bars, base class
- dialog bars, base class
- toolbars [C++], base class
- control bars [C++], base class
- status bars, base class
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
caps.latest.revision: 22
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
ms.openlocfilehash: 9720c4c11656834923c0e42a2017d51543c08f53
ms.lasthandoff: 02/24/2017

---
# <a name="ccontrolbar-class"></a>CControlBar Class
La clase base para las clases de barra de controles [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md), y [COleResizeBar](../../mfc/reference/coleresizebar-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CControlBar : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CControlBar::CControlBar](#ccontrolbar)|Construye un objeto `CControlBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Devuelve el tamaño de una barra de controles dinámica como un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.|  
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Devuelve el tamaño de la barra de control como un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.|  
|[CControlBar::CalcInsideRect](#calcinsiderect)|Devuelve las dimensiones actuales del área de la barra de controles, incluidos los bordes.|  
|[CControlBar::DoPaint](#dopaint)|Representa los bordes y la barra de redimensionamiento de la barra de controles.|  
|[CControlBar::DrawBorders](#drawborders)|Representa los bordes de la barra de controles.|  
|[CControlBar::DrawGripper](#drawgripper)|Representa la barra de redimensionamiento de la barra de controles.|  
|[CControlBar:: EnableDocking](#enabledocking)|Permite que una barra de controles esté acoplada o flotante.|  
|[CControlBar::](#getbarstyle)|Recupera la configuración de estilo de la barra de controles.|  
|[CControlBar::GetBorders](#getborders)|Recupera los valores de borde de la barra de controles.|  
|[CControlBar::GetCount](#getcount)|Devuelve el número de no `HWND` elementos en la barra de control.|  
|[CControlBar::GetDockingFrame](#getdockingframe)|Devuelve un puntero al marco al que está acoplada una barra de controles.|  
|[CControlBar::IsFloating](#isfloating)|Devuelve un valor distinto de cero si la barra de controles en cuestión es una barra de controles flotante.|  
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Llama a los controladores de la interfaz de usuario de comandos.|  
|[SetBarStyle](#setbarstyle)|Modifica la configuración de estilo de la barra de controles.|  
|[CControlBar::SetBorders](#setborders)|Establece los valores de borde de la barra de controles.|  
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Cambia el propietario en contexto de una barra de controles.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.|  
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Propietario en contexto de la barra de controles.|  
  
## <a name="remarks"></a>Comentarios  
 Una barra de controles es una ventana que suele estar alineada a la izquierda o a la derecha de una ventana de marco. Puede contener elementos secundarios que son `HWND`- based controles, que son ventanas que generan y responden a los mensajes de Windows, o no - `HWND`-según los elementos que no son windows y se administran mediante código de aplicación o marco. Cuadros de lista y controles de edición son ejemplos de `HWND`- controles basados en; los paneles de la barra de estado y botones de mapa de bits son ejemplos de no - `HWND`-controles basados en.  
  
 Las ventanas de barra de controles suelen ser ventanas secundarias de una ventana de marco principal y suelen ser elementos relacionados de la vista del cliente o del cliente MDI de la ventana de marco. Un objeto `CControlBar` utiliza información acerca del rectángulo cliente de su ventana primaria para colocarse. Después informa a la ventana primaria de cuánto espacio queda sin asignar en el área cliente de la ventana primaria.  
  
 Para obtener más información sobre `CControlBar`, vea:  
  
- [Barras de control](../../mfc/control-bars.md)  
  
- [Nota técnica 31: Barras de Control](../../mfc/tn031-control-bars.md).  
  
-   Artículo Q242577 de Knowledge Base: PRB: Los controladores de la interfaz de usuario de comandos de actualización no funcionan para un menú asociado a un cuadro de diálogo  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="calcdynamiclayout"></a>CControlBar::CalcDynamicLayout  
 El marco de trabajo llama a esta función miembro para calcular las dimensiones de una barra de herramientas dinámica.  
  
```  
virtual CSize CalcDynamicLayout(
    int nLength,  
    DWORD nMode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nLength`  
 La dimensión solicitada de la barra de control, ya sea horizontal o vertical, en función de `dwMode`.  
  
 `nMode`  
 Las marcas predefinidas siguientes se utilizan para determinar el alto y ancho de la barra de control dinámico. Utilice el operador OR bit a bit (|) para combinar los indicadores.  
  
|Marcadores de modo de diseño|Lo que significa|  
|-----------------------|-------------------|  
|`LM_STRETCH`|Indica si la barra de control debe ajustarse al tamaño del marco. Establece si la barra no es una barra de acoplamiento (no disponible para acoplar). No establecer cuando la barra es acoplada o flotante (disponible para acoplar). Si establece, `LM_STRETCH` omite `nLength` y devuelve las dimensiones según la `LM_HORZ` estado. `LM_STRETCH`funciona de forma similar a la `bStretch` parámetro utilizado en [CalcFixedLayout](#calcfixedlayout); consulte esa función de miembro para obtener más información sobre la relación entre expansión y orientación.|  
|`LM_HORZ`|Indica que la barra está orientada horizontal o verticalmente. Establece si la barra se orienta horizontalmente y si es una orientación vertical, no se establece. `LM_HORZ`funciona de forma similar a la `bHorz` parámetro utilizado en [CalcFixedLayout](#calcfixedlayout); consulte esa función de miembro para obtener más información sobre la relación entre expansión y orientación.|  
|**LM_MRUWIDTH**|Usados más recientemente ancho dinámica. Omite `nLength` parámetro y usa el recordados ancho usados más recientemente.|  
|`LM_HORZDOCK`|Horizontal había acoplada dimensiones. Omite `nLength` parámetro y devuelve el tamaño dinámico con el ancho mayor.|  
|`LM_VERTDOCK`|Vertical había acoplada dimensiones. Omite `nLength` parámetro y devuelve el tamaño dinámico con el alto máximo.|  
|`LM_LENGTHY`|Establece si `nLength` indica alto (dirección del eje Y) en lugar de ancho.|  
|`LM_COMMIT`|Restablece **LM_MRUWIDTH** al ancho actual de la barra de control flotante.|  
  
### <a name="return-value"></a>Valor devuelto  
 La barra de control de tamaño, en píxeles, de un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro para proporcionar su propio diseño dinámico en las clases que derivan de `CControlBar`. Clases MFC derivadas de `CControlBar`, como [CToolbar](../../mfc/reference/ctoolbar-class.md), reemplace esta función miembro y proporcionar su propia implementación.  
  
##  <a name="calcfixedlayout"></a>CControlBar::CalcFixedLayout  
 Llame a esta función miembro para calcular el tamaño horizontal de una barra de controles.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 `bStretch`  
 Indica si la barra debe ajustarse al tamaño del marco. El `bStretch` parámetro es distinto de cero cuando la barra no es una barra de acoplamiento (no disponible para acoplar) y es 0 si es acoplada o flotante (disponible para acoplar).  
  
 `bHorz`  
 Indica que la barra está orientada horizontal o verticalmente. El `bHorz` parámetro es distinto de cero si la barra se orienta horizontalmente y es 0 si es una orientación vertical.  
  
### <a name="return-value"></a>Valor devuelto  
 La barra de control de tamaño, en píxeles, de un `CSize` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Barras de controles, como barras de herramientas para estirar horizontal o verticalmente alojar los botones incluidos en la barra de control.  
  
 Si `bStretch` es **TRUE**, expandir la dimensión a lo largo de la orientación proporcionada por `bHorz`. En otras palabras, si `bHorz` es **FALSE**, la barra de control se expande verticalmente. Si `bStretch` es **FALSE**, se produce ningún ajuste. La siguiente tabla muestra las permutaciones posibles y estilos de barra de control resultante, de `bStretch` y `bHorz`.  
  
|bStretch|bHorz|Expandir|Orientación|Acoplamiento de acoplamiento o no.|  
|--------------|-----------|----------------|-----------------|--------------------------|  
|**ES TRUE**|**ES TRUE**|Ampliación horizontal|Orientación horizontal|Acoplamiento no|  
|**ES TRUE**|**FALSE**|Ampliación vertical|Orientan verticalmente|Acoplamiento no|  
|**FALSE**|**ES TRUE**|Sin estiramiento disponibles|Orientación horizontal|Acoplamiento|  
|**FALSE**|**FALSE**|Sin estiramiento disponibles|Orientan verticalmente|Acoplamiento|  
  
##  <a name="calcinsiderect"></a>CControlBar::CalcInsideRect  
 El marco de trabajo llama a esta función para calcular el área de cliente de la barra de control.  
  
```  
virtual void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Contiene las dimensiones actuales de la barra de controles; incluso los bordes.  
  
 `bHorz`  
 Indica que la barra está orientada horizontal o verticalmente. El `bHorz` parámetro es distinto de cero si la barra se orienta horizontalmente y es 0 si es una orientación vertical.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca antes de que se dibuje la barra de control.  
  
 Reemplazar esta función para personalizar la representación de los bordes y la barra de controles de la barra de control.  
  
##  <a name="ccontrolbar"></a>CControlBar::CControlBar  
 Construye un objeto `CControlBar`.  
  
```  
CControlBar();
```  
  
##  <a name="dopaint"></a>CControlBar::DoPaint  
 Llamado por el marco para representar los bordes y la barra de controles de la barra de control.  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Señala al contexto de dispositivo que se usará para representar los bordes y la barra de redimensionamiento de la barra de control.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar el comportamiento de dibujo de la barra de control.  
  
 Otro método de personalización es reemplazar el `DrawBorders` y `DrawGripper` las funciones y agregar código de dibujo personalizado de los bordes y agarrador. Dado que el valor predeterminado llama a estos métodos `DoPaint` método, un reemplazo de `DoPaint` no es necesaria.  
  
##  <a name="drawborders"></a>CControlBar::DrawBorders  
 Llamado por el marco para representar los bordes de la barra de control.  
  
```  
virtual void DrawBorders(
    CDC* pDC,  
    CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Señala al contexto de dispositivo que se usará para representar los bordes de la barra de control.  
  
 `rect`  
 Un `CRect` objeto que contiene las dimensiones de la barra de control.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar la apariencia de los bordes de la barra de control.  
  
##  <a name="drawgripper"></a>CControlBar::DrawGripper  
 Llamado por el marco para representar al redimensionamiento de la barra de control.  
  
```  
virtual void DrawGripper(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Señala al contexto de dispositivo que se usará para representar a los controles de barra de control.  
  
 `rect`  
 Un `CRect` objeto que contiene las dimensiones de los controles de barra de control.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar la apariencia de los controles de barra de control.  
  
##  <a name="enabledocking"></a>CControlBar:: EnableDocking  
 Llame a esta función para habilitar una barra de controles acoplada.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDockStyle`  
 Especifica si la barra de control admite el acoplamiento y los lados de la ventana primaria a la que se puede acoplar la barra de control, si es compatible. Puede ser uno o varios de los siguientes:  
  
- `CBRS_ALIGN_TOP`Permite acoplar en la parte superior del área cliente.  
  
- `CBRS_ALIGN_BOTTOM`Permite acoplar en la parte inferior del área de cliente.  
  
- `CBRS_ALIGN_LEFT`Permite acoplar en el lado izquierdo del área cliente.  
  
- `CBRS_ALIGN_RIGHT`Permite acoplar en el lado derecho del área de cliente.  
  
- `CBRS_ALIGN_ANY`Permite acoplar en cualquier lado del área de cliente.  
  
- `CBRS_FLOAT_MULTI`Permite que varias barras de control que se dejará flotando en una ventana de marco reducido único.  
  
 Si es 0 (es decir, no indica ningún indicador), no se acopla la barra de control.  
  
### <a name="remarks"></a>Comentarios  
 Los lados especificados deben coincidir con uno de los lados habilitados para el acoplamiento en la ventana de marco de destino o la barra de control no se puede acoplar a esa ventana de marco.  
  
##  <a name="getbarstyle"></a>CControlBar::  
 Llame a esta función para determinar qué **CBRS_** (estilos de barra de control) están actualmente configurados para la barra de control.  
  
```  
DWORD GetBarStyle();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Actual **CBRS_** (estilos de barra de control) de configuración de la barra de control. Consulte [SetBarStyle](#setbarstyle) para obtener una lista completa de los estilos disponibles.  
  
### <a name="remarks"></a>Comentarios  
 No controla **WS_** (ventana) de estilos.  
  
##  <a name="getborders"></a>CControlBar::GetBorders  
 Devuelve los valores de borde de la barra de control actual.  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CRect` objeto que contiene el ancho actual (en píxeles) de cada lado del objeto de barra de control. Por ejemplo, el valor de la `left` miembro de [CRect](../../atl-mfc-shared/reference/crect-class.md) de objeto, que es el ancho del borde izquierdo.  
  
##  <a name="getcount"></a>CControlBar::GetCount  
 Devuelve el número de no `HWND` elementos en la `CControlBar` objeto.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de no `HWND` elementos en la `CControlBar` objeto. Esta función devuelve 0 para un [CDialogBar](../../mfc/reference/cdialogbar-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El tipo del elemento depende el objeto derivado: los paneles de [CStatusBar](../../mfc/reference/cstatusbar-class.md) objetos, botones y separadores de [CToolBar](../../mfc/reference/ctoolbar-class.md) objetos.  
  
##  <a name="getdockingframe"></a>CControlBar::GetDockingFrame  
 Llame a esta función miembro para obtener un puntero a la ventana de marco actual a la que se acopla la barra de control.  
  
```  
CFrameWnd* GetDockingFrame() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a una ventana de marco, si es correcto; de lo contrario, **NULL**.  
  
 Si la barra de control no se acopla a una ventana de marco (es decir, si la barra de control es flotante), esta función devuelve un puntero a su elemento primario [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las barras de control acoplable, consulte [CControlBar:: EnableDocking](#enabledocking) y [CFrameWnd:: DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).  
  
##  <a name="isfloating"></a>CControlBar::IsFloating  
 Llame a esta función miembro para determinar si la barra de controles es acoplada o flotante.  
  
```  
BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la barra de control es flotante; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para cambiar el estado de una barra de controles de acoplada a flotante, llame a [CFrameWnd:: FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).  
  
##  <a name="m_bautodelete"></a>CControlBar::m_bAutoDelete  
 Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Comentarios  
 `m_bAutoDelete`es una variable pública de tipo **BOOL**.  
  
 Normalmente, un objeto de barra de controles está incrustado en un objeto de ventana de marco. En este caso, `m_bAutoDelete` es 0 porque el objeto de barra de control incrustado se destruye cuando se destruye la ventana de marco.  
  
 Establecer esta variable en un valor distinto de cero si asigna un `CControlBar` objeto en el montón y no tiene previsto llamar a **eliminar**.  
  
##  <a name="m_pinplaceowner"></a>CControlBar::m_pInPlaceOwner  
 Propietario en contexto de la barra de controles.  
  
```  
CWnd* m_pInPlaceOwner;  
```  
  
##  <a name="onupdatecmdui"></a>CControlBar::OnUpdateCmdUI  
 Esta función miembro se llama el marco de trabajo para actualizar el estado de la barra de herramientas o barra de estado.  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pTarget`  
 Apunta a la ventana de marco principal de la aplicación. Este puntero se utiliza para enrutar mensajes de actualización.  
  
 `bDisableIfNoHndler`  
 Marca que indica si un control que no tiene ningún controlador de actualización debe mostrarse automáticamente como deshabilitado.  
  
### <a name="remarks"></a>Comentarios  
 Para actualizar un botón individual o un panel, use la `ON_UPDATE_COMMAND_UI` macro en el mapa de mensajes para establecer un controlador de actualización de forma adecuada. Consulte [ON_UPDATE_COMMAND_UI](http://msdn.microsoft.com/library/c4de3c21-2d2e-4b89-a4ce-d0c0e2d9edc4) para obtener más información acerca de cómo utilizar esta macro.  
  
 `OnUpdateCmdUI`es llamado por el marco cuando la aplicación está inactiva. La ventana de marco actualizarse debe ser una ventana secundaria, al menos indirectamente, de una ventana de marco visibles. `OnUpdateCmdUI`avanzada reemplazable.  
  
##  <a name="setbarstyle"></a>SetBarStyle  
 Llame a esta función para establecer el deseado **CBRS_** estilos de la barra de control.  
  
```  
void SetBarStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Los estilos que desee de la barra de control. Puede ser uno o varios de los siguientes:  
  
- `CBRS_ALIGN_TOP`Permite la barra de control se acopla a la parte superior del área cliente de una ventana de marco.  
  
- `CBRS_ALIGN_BOTTOM`Permite que la barra de control se acopla a la parte inferior del área de cliente de una ventana de marco.  
  
- `CBRS_ALIGN_LEFT`Permite que la barra de control se acopla al lado izquierdo del área cliente de una ventana de marco.  
  
- `CBRS_ALIGN_RIGHT`Permite que la barra de control se acopla a la derecha del área de cliente de una ventana de marco.  
  
- `CBRS_ALIGN_ANY`Permite que la barra de control se puede acoplar a cualquier lado del área de cliente de una ventana de marco.  
  
- `CBRS_BORDER_TOP`Hace que un borde se dibujen en el borde superior de la barra de control cuando serían visible.  
  
- `CBRS_BORDER_BOTTOM`Hace que un borde se dibuje en la parte inferior de la barra de control cuando puedan ser visible.  
  
- `CBRS_BORDER_LEFT`Hace que un borde se dibujen en el borde izquierdo de la barra de control cuando serían visible.  
  
- `CBRS_BORDER_RIGHT`Hace que un borde se dibujen en el borde derecho de la barra de control cuando serían visible.  
  
- `CBRS_FLOAT_MULTI`Permite que varias barras de control que se dejará flotando en una ventana de marco reducido único.  
  
- `CBRS_TOOLTIPS`Provoca la información sobre herramientas que se mostrará en la barra de control.  
  
- `CBRS_FLYBY`Hace que el texto de mensaje se actualicen al mismo tiempo como información sobre herramientas.  
  
- **CBRS_GRIPPER** hace un agarre, similar al utilizado en bandas en una **CReBar** objeto dibujarse para cualquier `CControlBar`-clase derivada.  
  
### <a name="remarks"></a>Comentarios  
 No afecta a la **WS_** configuración (estilo de ventana).  
  
##  <a name="setborders"></a>CControlBar::SetBorders  
 Llame a esta función para establecer el tamaño de los bordes de la barra de control.  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 *cxLeft*  
 El ancho (en píxeles) del borde izquierdo de la barra de control.  
  
 *cyTop*  
 El alto (en píxeles) del borde superior de la barra de control.  
  
 *cxRight*  
 El ancho (en píxeles) del borde derecho de la barra de control.  
  
 *cyBottom*  
 El alto (en píxeles) del borde inferior de la barra de control.  
  
 `lpRect`  
 Un puntero a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el ancho actual (en píxeles) de cada borde del objeto de barra de control.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente establece los bordes superior e inferior de la barra de control de 5 píxeles y los bordes izquierdos y derecho a 2 píxeles:  
  
 [!code-cpp[NVC_MFCControlLadenDialog&#61;](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]  
  
##  <a name="setinplaceowner"></a>CControlBar::SetInPlaceOwner  
 Cambia el propietario en contexto de una barra de controles.  
  
```  
void SetInPlaceOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Un puntero a un `CWnd` objeto.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [CTRLBARS de ejemplo de MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CToolBar (clase)](../../mfc/reference/ctoolbar-class.md)   
 [CDialogBar (clase)](../../mfc/reference/cdialogbar-class.md)   
 [CStatusBar (clase)](../../mfc/reference/cstatusbar-class.md)   
 [CReBar (clase)](../../mfc/reference/crebar-class.md)

