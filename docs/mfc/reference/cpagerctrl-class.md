---
title: Clase CPagerCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CPagerCtrl class
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
caps.latest.revision: 26
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
ms.openlocfilehash: 8b8bf05873239f274a9b1285797c01123fe071f7
ms.lasthandoff: 02/24/2017

---
# <a name="cpagerctrl-class"></a>Clase CPagerCtrl
La clase `CPagerCtrl` ajusta el control de paginación de Windows, que puede desplazar en la vista una ventana contenida que no cabe en la ventana contenedora.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Construye un objeto `CPagerCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPagerCtrl::Create](#create)|Crea un control de paginación con los estilos especificados y lo adjunta a la corriente `CPagerCtrl` objeto.|  
|[CPagerCtrl::CreateEx](#createex)|Crea un control de paginación con estilos extendidos especificados y lo adjunta a la corriente `CPagerCtrl` objeto.|  
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Habilita o deshabilita el reenvío [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) mensajes en la ventana que se encuentra en el control de paginación actual.|  
|[CPagerCtrl::GetBkColor](#getbkcolor)|Recupera el color de fondo del control de paginación actual.|  
|[CPagerCtrl::GetBorder](#getborder)|Recupera el tamaño del borde del control de paginación actual.|  
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Recupera el tamaño de los botones del control de paginación actual.|  
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Recupera el estado del botón especificado en el control de paginación actual.|  
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Recupera el [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interfaz para el control de paginación actual.|  
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Recupera la posición de desplazamiento del control de paginación actual.|  
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Indica si el botón especificado del control de paginación actual está en `pressed` estado.|  
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Indica si el botón especificado del control de paginación actual está en `grayed` estado.|  
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Indica si el botón especificado del control de paginación actual está en `hot` estado.|  
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Indica si el botón especificado del control de paginación actual está en `invisible` estado.|  
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Indica si el botón especificado del control de paginación actual está en `normal` estado.|  
|[CPagerCtrl::RecalcSize](#recalcsize)|Hace que el control de paginación actual volver a calcular el tamaño de la ventana independiente.|  
|[CPagerCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo del control de paginación actual.|  
|[CPagerCtrl::SetBorder](#setborder)|Establece el tamaño del borde del control de paginación actual.|  
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Establece el tamaño de los botones del control de paginación actual.|  
|[CPagerCtrl::SetChild](#setchild)|Establece la ventana independiente para el control de paginación actual.|  
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Establece la posición de desplazamiento del control de paginación actual.|  
  
## <a name="remarks"></a>Comentarios  
 Un control de paginación es una ventana que contiene otra ventana que es mayor que la ventana contenedora y lineal y permite desplazar la ventana contenida en la vista. El control de paginación muestra dos botones de desplazamiento que desaparecen automáticamente cuando se desplaza la ventana contenida en su alcance más alejada y vuelva a aparecer en caso contrario. Puede crear un control de paginación que se desplaza horizontalmente o verticalmente.  
  
 Por ejemplo, si la aplicación tiene una barra de herramientas no es lo suficientemente ancha para mostrar todos sus elementos, puede asignar la barra de herramientas a un control de paginación y los usuarios podrán desplazarse a la izquierda o derecha para tener acceso a todos los elementos de la barra de herramientas. Microsoft Internet Explorer versión 4.0 (versión commctrl.dll 4.71) presenta el control de paginación.  
  
 El `CPagerCtrl` clase se deriva de la [CWnd](../../mfc/reference/cwnd-class.md) clase. Para obtener más información y una ilustración de un control de paginación, consulte [controles de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760855).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="a-namecpagerctrla--cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a>CPagerCtrl::CPagerCtrl  
 Construye un objeto `CPagerCtrl`.  
  
```  
CPagerCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CPagerCtrl::Create](#create) o [CPagerCtrl::CreateEx](#createex) método para crear un control de paginación y adjuntarlo a la `CPagerCtrl` objeto.  
  
##  <a name="a-namecreatea--cpagerctrlcreate"></a><a name="create"></a>CPagerCtrl::Create  
 Crea un control de paginación con los estilos especificados y lo adjunta a la corriente `CPagerCtrl` objeto.  
  
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
|[in] `dwStyle`|Una combinación bit a bit (OR) de [estilos de ventana](../../mfc/reference/window-styles.md) y [estilos de control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859) aplicarse al control.|  
|[in] `rect`|Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene la posición y el tamaño del control, en coordenadas de cliente.|  
|[in] `pParentWnd`|Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto de la ventana primaria del control. Este parámetro no puede ser `NULL`.|  
|[in] `nID`|El identificador del control.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Para crear un control de paginación, declare un `CPagerCtrl` variable, a continuación, llame a la [CPagerCtrl::Create](#create) o [CPagerCtrl::CreateEx](#createex) método en esa variable.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un control de paginación, a continuación, usa el [CPagerCtrl::SetChild](#setchild) método para asociar un control de botón mucho el control de paginación. El ejemplo se utiliza la [CPagerCtrl::SetButtonSize](#setbuttonsize) para establecer el alto del control de paginación en 20 píxeles y el [CPagerCtrl::SetBorder](#setborder) método para establecer el grosor del borde de 1 píxel.  
  
 [!code-cpp[1 NVC_MFC_CSplitButton_s2](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="a-namecreateexa--cpagerctrlcreateex"></a><a name="createex"></a>CPagerCtrl::CreateEx  
 Crea un control de paginación con estilos extendidos especificados y lo adjunta a la corriente `CPagerCtrl` objeto.  
  
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
|[in] `dwExStyle`|Una combinación bit a bit de los estilos extendidos que se aplicará al control. Para obtener más información, consulte el `dwExStyle` parámetro de la [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) (función).|  
|[in] `dwStyle`|Una combinación bit a bit (OR) de [estilos de ventana](../../mfc/reference/window-styles.md) y [estilos de control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859) aplicarse al control.|  
|[in] `rect`|Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene la posición y el tamaño del control, en coordenadas de cliente.|  
|[in] `pParentWnd`|Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto de la ventana primaria del control. Este parámetro no puede ser `NULL`.|  
|[in] `nID`|El identificador del control.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Para crear un control de paginación, declare un `CPagerCtrl` variable, a continuación, llame a la [CPagerCtrl::Create](#create) o [CPagerCtrl::CreateEx](#createex) método en esa variable.  
  
##  <a name="a-nameforwardmousea--cpagerctrlforwardmouse"></a><a name="forwardmouse"></a>CPagerCtrl::ForwardMouse  
 Habilita o deshabilita el reenvío [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) mensajes en la ventana que se encuentra en el control de paginación actual.  
  
```  
void ForwardMouse(BOOL bForward);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `bForward`|`true`para reenviar mensajes del mouse, o `false` para que no reenvíen mensajes del mouse.|  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_FORWARDMOUSE](http://msdn.microsoft.com/library/windows/desktop/bb760867) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetbordera--cpagerctrlgetborder"></a><a name="getborder"></a>CPagerCtrl::GetBorder  
 Recupera el tamaño del borde del control de paginación actual.  
  
```  
int GetBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del borde actual, expresado en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760869) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la [CPagerCtrl::GetBorder](#getborder) método para recuperar el grosor del borde del control de paginación.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]  
  
##  <a name="a-namegetbkcolora--cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a>CPagerCtrl::GetBkColor  
 Recupera el color de fondo del control de paginación actual.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que contiene el color de fondo actual del control de paginación.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760868) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la [CPagerCtrl::SetBkColor](#setbkcolor) para establecer el color de fondo del control de paginación en rojo y la [CPagerCtrl::GetBkColor](#getbkcolor) método para confirmar que se ha realizado el cambio.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2 Nº&4;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="a-namegetbuttonsizea--cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CPagerCtrl::GetButtonSize  
 Recupera el tamaño de los botones del control de paginación actual.  
  
```  
int GetButtonSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del botón actual, expresado en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760870) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Si el control de paginación tiene la `PGS_HORZ` estilo, el tamaño del botón determina el ancho de los botones de paginación, y si el control de paginación tiene la `PGS_VERT` estilo, el tamaño del botón determina el alto de los botones de buscapersonas. Para obtener más información, consulte [estilos de Control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859).  
  
##  <a name="a-namegetbuttonstatea--cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a>CPagerCtrl::GetButtonState  
 Recupera el estado del botón de desplazamiento especificada en el control de paginación actual.  
  
```  
DWORD GetButtonState(int iButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iButton`|Indica el botón que se recupera el estado. Si el estilo del control de paginación es `PGS_HORZ`, especifique `PGB_TOPORLEFT` para el botón izquierdo y `PGB_BOTTOMORRIGHT` para el botón secundario. Si el estilo del control de paginación es `PGS_VERT`, especifique `PGB_TOPORLEFT` para el botón superior y `PGB_BOTTOMORRIGHT` para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valor devuelto  
 El estado del botón especificado por el `iButton` parámetro. The state is either `PGF_INVISIBLE`, `PGF_NORMAL`, `PGF_GRAYED`, `PGF_DEPRESSED`, or `PGF_HOT`. Para obtener más información, consulte la sección de valor devuelto de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetdroptargeta--cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a>CPagerCtrl::GetDropTarget  
 Recupera el [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interfaz para el control de paginación actual.  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `IDropTarget` interfaz para el control de paginación actual.  
  
### <a name="remarks"></a>Comentarios  
 `IDropTarget`es una de las interfaces que se implementan para admitir las operaciones de arrastrar y colocar en la aplicación.  
  
 Este método envía el [PGM_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb760872) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. El llamador de este método es responsable de llamar a la `Release` miembro de la [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) cuando ya no se necesita la interfaz de la interfaz.  
  
##  <a name="a-namegetscrollposa--cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a>CPagerCtrl::GetScrollPos  
 Recupera la posición de desplazamiento del control de paginación actual.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La posición de desplazamiento actual, expresada en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760874) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la [CPagerCtrl::GetScrollPos](#getscrollpos) método para recuperar la posición de desplazamiento actual del control de paginación. Si el control de paginación no está ya se ha desplazado a cero, la posición más a la izquierda, el ejemplo utiliza la [CPagerCtrl::SetScrollPos](#setscrollpos) método para establecer la posición de desplazamiento en cero.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s&#2;7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]  
  
##  <a name="a-nameisbuttondepresseda--cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a>CPagerCtrl::IsButtonDepressed  
 Indica si el botón de desplazamiento especificada del control de paginación actual está en estado presionado.  
  
```  
BOOL IsButtonDepressed(int iButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iButton`|Indica el botón que se recupera el estado. Si el estilo del control de paginación es `PGS_HORZ`, especifique `PGB_TOPORLEFT` para el botón izquierdo y `PGB_BOTTOMORRIGHT` para el botón secundario. Si el estilo del control de paginación es `PGS_VERT`, especifique `PGB_TOPORLEFT` para el botón superior y `PGB_BOTTOMORRIGHT` para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el botón especificado está en estado presionado; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. A continuación, comprueba si el estado que se devuelve es `PGF_DEPRESSED`. Para obtener más información, consulte la sección de valor devuelto de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje.  
  
##  <a name="a-nameisbuttongrayeda--cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a>CPagerCtrl::IsButtonGrayed  
 Indica si el botón de desplazamiento especificada del control de paginación actual está en estado atenuado.  
  
```  
BOOL IsButtonGrayed(int iButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iButton`|Indica el botón que se recupera el estado. Si el estilo del control de paginación es `PGS_HORZ`, especifique `PGB_TOPORLEFT` para el botón izquierdo y `PGB_BOTTOMORRIGHT` para el botón secundario. Si el estilo del control de paginación es `PGS_VERT`, especifique `PGB_TOPORLEFT` para el botón superior y `PGB_BOTTOMORRIGHT` para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el botón especificado está en estado atenuado; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. A continuación, comprueba si el estado que se devuelve es `PGF_GRAYED`. Para obtener más información, consulte la sección de valor devuelto de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje.  
  
##  <a name="a-nameisbuttonhota--cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a>CPagerCtrl::IsButtonHot  
 Indica si el botón de desplazamiento especificada del control de paginación actual está en estado activo.  
  
```  
BOOL IsButtonHot(int iButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iButton`|Indica el botón que se recupera el estado. Si el estilo del control de paginación es `PGS_HORZ`, especifique `PGB_TOPORLEFT` para el botón izquierdo y `PGB_BOTTOMORRIGHT` para el botón secundario. Si el estilo del control de paginación es `PGS_VERT`, especifique `PGB_TOPORLEFT` para el botón superior y `PGB_BOTTOMORRIGHT` para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el botón especificado está en estado activo; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. A continuación, comprueba si el estado que se devuelve es `PGF_HOT`. Para obtener más información, consulte la sección de valor devuelto de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje.  
  
##  <a name="a-nameisbuttoninvisiblea--cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a>CPagerCtrl::IsButtonInvisible  
 Indica si el botón de desplazamiento especificada del control de paginación actual está en estado invisible.  
  
```  
BOOL IsButtonInvisible(int iButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iButton`|Indica el botón que se recupera el estado. Si el estilo del control de paginación es `PGS_HORZ`, especifique `PGB_TOPORLEFT` para el botón izquierdo y `PGB_BOTTOMORRIGHT` para el botón secundario. Si el estilo del control de paginación es `PGS_VERT`, especifique `PGB_TOPORLEFT` para el botón superior y `PGB_BOTTOMORRIGHT` para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el botón especificado está en estado invisible; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Windows oculta el botón de desplazamiento en una dirección determinada cuando se desplaza la ventana contenida en su alcance más alejada porque al hacer clic en el botón más no puede poner más de la ventana contenida en la vista.  
  
 Este método envía el [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. A continuación, comprueba si el estado que se devuelve es `PGF_INVISIBLE`. Para obtener más información, consulte la sección de valor devuelto de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) método para determinar si el control de paginación de la izquierda y los botones de desplazamiento a la derecha están visibles.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2 Nº&6;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]  
  
##  <a name="a-nameisbuttonnormala--cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a>CPagerCtrl::IsButtonNormal  
 Indica si el botón de desplazamiento especificada del control de paginación actual está en estado normal.  
  
```  
BOOL IsButtonNormal(int iButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iButton`|Indica el botón que se recupera el estado. Si el estilo del control de paginación es `PGS_HORZ`, especifique `PGB_TOPORLEFT` para el botón izquierdo y `PGB_BOTTOMORRIGHT` para el botón secundario. Si el estilo del control de paginación es `PGS_VERT`, especifique `PGB_TOPORLEFT` para el botón superior y `PGB_BOTTOMORRIGHT` para el botón de la parte inferior. Para obtener más información, consulte [estilos de Control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el botón especificado está en estado normal; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. A continuación, comprueba si el estado que se devuelve es `PGF_NORMAL`. Para obtener más información, consulte la sección de valor devuelto de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) mensaje.  
  
##  <a name="a-namerecalcsizea--cpagerctrlrecalcsize"></a><a name="recalcsize"></a>CPagerCtrl::RecalcSize  
 Hace que el control de paginación actual volver a calcular el tamaño de la ventana independiente.  
  
```  
void RecalcSize();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_RECALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760876) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Por consiguiente, el control de paginación envía el [PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864) notificación para obtener las dimensiones de desplazamiento de la ventana independiente.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la [CPagerCtrl::RecalcSize](#recalcsize) método para solicitar el control de paginación actual para volver a calcular su tamaño.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2&3;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza [reflexión de mensajes](../../mfc/tn062-message-reflection-for-windows-controls.md) para habilitar el control de paginación volver a calcular su propio tamaño en lugar de requerir el cuadro de diálogo del control primario para realizar el cálculo. El ejemplo se deriva el `MyPagerCtrl` desde el [clase CPagerCtrl](../../mfc/reference/cpagerctrl-class.md), a continuación, utiliza un mapa de mensajes para asociar el [PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864) notificación con el `OnCalcsize` controlador de notificación. En este ejemplo, el controlador de notificación establece el ancho y el alto del control de paginación en valores fijos.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2 Nº&8;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]  
  
##  <a name="a-namesetbkcolora--cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a>CPagerCtrl::SetBkColor  
 Establece el color de fondo del control de paginación actual.  
  
```  
COLORREF SetBkColor(COLORREF clrBk);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `clrBk`|Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que contiene el nuevo color de fondo del control de paginación.|  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que contiene el color de fondo anterior del control de paginación.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760878) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se utiliza la [CPagerCtrl::SetBkColor](#setbkcolor) para establecer el color de fondo del control de paginación en rojo y la [CPagerCtrl::GetBkColor](#getbkcolor) método para confirmar que se ha realizado el cambio.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2 Nº&4;](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="a-namesetbordera--cpagerctrlsetborder"></a><a name="setborder"></a>CPagerCtrl::SetBorder  
 Establece el tamaño del borde del control de paginación actual.  
  
```  
int SetBorder(int iBorder);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iBorder`|El nuevo tamaño del borde, expresado en píxeles. Si el `iBorder` parámetro es negativo, el tamaño del borde se establece en cero.|  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del borde anterior, expresado en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_SETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760880) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un control de paginación, a continuación, usa el [CPagerCtrl::SetChild](#setchild) método para asociar un control de botón mucho el control de paginación. El ejemplo se utiliza la [CPagerCtrl::SetButtonSize](#setbuttonsize) para establecer el alto del control de paginación en 20 píxeles y el [CPagerCtrl::SetBorder](#setborder) método para establecer el grosor del borde de 1 píxel.  
  
 [!code-cpp[1 NVC_MFC_CSplitButton_s2](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="a-namesetbuttonsizea--cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CPagerCtrl::SetButtonSize  
 Establece el tamaño de los botones del control de paginación actual.  
  
```  
int SetButtonSize(int iButtonSize);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iButtonSize`|El nuevo tamaño de botón, medido en píxeles.|  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del botón anterior, expresado en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_SETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760886) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Si el control de paginación tiene la `PGS_HORZ` estilo, el tamaño del botón determina el ancho de los botones de paginación, y si el control de paginación tiene la `PGS_VERT` estilo, el tamaño del botón determina el alto de los botones de buscapersonas. El tamaño predeterminado del botón es tres cuartos del ancho de la barra de desplazamiento y el tamaño de botón mínimo es de 12 píxeles. Para obtener más información, consulte [estilos de Control de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760859).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un control de paginación, a continuación, usa el [CPagerCtrl::SetChild](#setchild) método para asociar un control de botón mucho el control de paginación. El ejemplo se utiliza la [CPagerCtrl::SetButtonSize](#setbuttonsize) para establecer el alto del control de paginación en 20 píxeles y el [CPagerCtrl::SetBorder](#setborder) método para establecer el grosor del borde de 1 píxel.  
  
 [!code-cpp[1 NVC_MFC_CSplitButton_s2](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="a-namesetchilda--cpagerctrlsetchild"></a><a name="setchild"></a>CPagerCtrl::SetChild  
 Establece la ventana independiente para el control de paginación actual.  
  
```  
void SetChild(HWND hwndChild);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `hwndChild`|Identificador de la ventana que se debe incluir.|  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_SETCHILD](http://msdn.microsoft.com/library/windows/desktop/bb760884) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Este método no cambia al elemento primario de la ventana independiente; sólo se asigna un identificador de ventana para el control de paginación para el desplazamiento. En la mayoría de los casos, la ventana contenida será una ventana secundaria de control de paginación.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un control de paginación, a continuación, usa el [CPagerCtrl::SetChild](#setchild) método para asociar un control de botón mucho el control de paginación. El ejemplo se utiliza la [CPagerCtrl::SetButtonSize](#setbuttonsize) para establecer el alto del control de paginación en 20 píxeles y el [CPagerCtrl::SetBorder](#setborder) método para establecer el grosor del borde de 1 píxel.  
  
 [!code-cpp[1 NVC_MFC_CSplitButton_s2](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="a-namesetscrollposa--cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a>CPagerCtrl::SetScrollPos  
 Establece la posición de desplazamiento del control de paginación actual.  
  
```  
void SetScrollPos(int iPos);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iPos`|La nueva posición de desplazamiento, medido en píxeles.|  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PGM_SETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760886) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Clase CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Controles de paginación](http://msdn.microsoft.com/library/windows/desktop/bb760855)




