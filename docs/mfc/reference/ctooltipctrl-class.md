---
title: CToolTipCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
dev_langs:
- C++
helpviewer_keywords:
- tool tips [C++], tool tip controls
- data tips [C++]
- CToolTipCtrl class
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 982aae01dc1308896e9c625e2c2e118b65ec2e64
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class
Encapsula la funcionalidad de un "control de información sobre herramientas", una pequeña ventana emergente que muestra una única línea de texto que describe el propósito de una herramienta de una aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Construye un objeto `CToolTipCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CToolTipCtrl::Activate](#activate)|Activa y desactiva el control de información sobre herramientas.|  
|[CToolTipCtrl::AddTool](#addtool)|Registra una herramienta con el control de información sobre herramientas.|  
|[CToolTipCtrl::AdjustRect](#adjustrect)|Convierte entre el texto del control de información sobre herramientas muestra el rectángulo de la ventana y el rectángulo.|  
|[CToolTipCtrl::Create](#create)|Crea un control de información sobre herramienta y lo adjunta a un `CToolTipCtrl` objeto.|  
|[CToolTipCtrl::CreateEx](#createex)|Crea un control de información sobre herramientas con los estilos extendidos de Windows especificados y lo adjunta a un `CToolTipCtrl` objeto.|  
|[CToolTipCtrl::DelTool](#deltool)|Quita una herramienta desde el control de información sobre herramientas.|  
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Recupera el tamaño de la información sobre herramientas.|  
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Recupera información, como el tamaño, la posición y el texto de la ventana de información sobre herramientas que muestra el control de información sobre herramientas actual.|  
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Recupera la inicial, emergente y reshow control de información sobre las duraciones que actualmente están establecidas para una herramienta.|  
|[CToolTipCtrl::GetMargin](#getmargin)|Recupera la parte superior, izquierda, inferior y los márgenes derecho que se establecen para una ventana de información.|  
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Recupera el ancho máximo de una ventana de información.|  
|[CToolTipCtrl::GetText](#gettext)|Recupera el texto que un control de información sobre herramientas mantiene para una herramienta.|  
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Recupera el color de fondo en una ventana de información.|  
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Recupera el color del texto en una ventana de información.|  
|[CToolTipCtrl::GetTitle](#gettitle)|Recupera el título del control de información sobre herramientas actual.|  
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Recupera un recuento de las herramientas que se mantiene un control de información sobre herramientas.|  
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Recupera la información que se mantiene un control de información sobre herramienta sobre una herramienta.|  
|[CToolTipCtrl::HitTest](#hittest)|Prueba en un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada. Si es así, recupera información acerca de la herramienta.|  
|[CToolTipCtrl::Pop](#pop)|Quita una ventana de información muestra la vista.|  
|[CToolTipCtrl::Popup](#popup)|Hace que el control de información sobre herramientas actual mostrar en las coordenadas del último mensaje de mouse.|  
|[CToolTipCtrl:: RelayEvent](#relayevent)|Pasa un mensaje del mouse a un control de información sobre herramientas para el procesamiento.|  
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Establece la inicial, emergente y reshow las duraciones de un control de información sobre herramientas.|  
|[CToolTipCtrl::SetMargin](#setmargin)|Establece la parte superior, izquierda, inferior y los márgenes derecho de una ventana de información.|  
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Establece el ancho máximo de una ventana de información.|  
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Establece el color de fondo en una ventana de información.|  
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Establece el color del texto en una ventana de información.|  
|[CToolTipCtrl::SetTitle](#settitle)|Agrega una cadena estándar de icono y el título de una información sobre herramientas.|  
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Establece la información que mantiene información sobre herramientas para una herramienta.|  
|[CToolTipCtrl::SetToolRect](#settoolrect)|Establece un nuevo rectángulo delimitador para una herramienta.|  
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Establece el estilo visual de la ventana.|  
|[CToolTipCtrl::Update](#update)|Fuerza a la herramienta actual se vuelva a dibujar.|  
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Establece el texto de sugerencia para una herramienta.|  
  
## <a name="remarks"></a>Comentarios  
 Un "tool" es cualquier ventana, como una ventana secundaria o de control o de un área rectangular definida por la aplicación dentro del área cliente de una ventana. Una información sobre herramientas se oculta la mayoría de las veces, que aparecen solo cuando el usuario coloca el cursor sobre una herramienta y deja ahí durante, aproximadamente, medio segundo. La información sobre herramientas aparece cerca del cursor y desaparece cuando el usuario hace clic en un botón del mouse o mueve el cursor de la herramienta.  
  
 `CToolTipCtrl`proporciona la funcionalidad al control de la hora inicial y la duración de la información sobre herramientas, el ancho de los márgenes que rodean el texto de sugerencia, el ancho de la propia ventana de punta de herramienta y el color de fondo y texto de la información sobre herramientas. Control de información sobre una única herramienta puede proporcionar información para más de una herramienta.  
  
 La `CToolTipCtrl` clase proporciona la funcionalidad de control de punta de herramienta común de Windows. Este control (y por tanto la `CToolTipCtrl` clase) está disponible sólo para los programas que se ejecutan en versiones de Windows 95 ó 98 y Windows NT 3.51 y posteriores.  
  
 Para obtener más información acerca de cómo habilitar información sobre herramientas, consulte [información sobre herramientas en ventanas no derivadas de CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
 Para obtener más información sobre el uso de `CToolTipCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [utilizando CToolTipCtrl](../../mfc/using-ctooltipctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="activate"></a>CToolTipCtrl::Activate  
 Llame a esta función para activar o desactivar un control de información sobre herramientas.  
  
```  
void Activate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 `bActivate`  
 Especifica si el control de información sobre herramientas está activado o desactivado.  
  
### <a name="remarks"></a>Comentarios  
 Si `bActivate` es **TRUE**, se activa el control; si **FALSE**, está desactivada.  
  
 Cuando un control de información sobre herramientas está activo, la información de información sobre herramientas aparece cuando el cursor está en una herramienta que se registra con el control; Cuando está inactivo, la información de la sugerencia de herramientas no aparece, incluso cuando el cursor esté sobre una herramienta.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="addtool"></a>CToolTipCtrl::AddTool  
 Registra una herramienta con el control de información sobre herramientas.  
  
```  
BOOL AddTool(
    CWnd* pWnd,  
    UINT nIDText,  
    LPCRECT lpRectTool = NULL,  
    UINT_PTR nIDTool = 0);

 
BOOL AddTool(
    CWnd* pWnd,  
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,  
    LPCRECT lpRectTool = NULL,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana que contiene la herramienta.  
  
 `nIDText`  
 Id. del recurso de cadena que contiene el texto de la herramienta.  
  
 *lpRectTool*  
 Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) rectángulo delimitador de estructura que contiene las coordenadas de la herramienta. Las coordenadas son relativas a la esquina superior izquierda del área cliente de la ventana identificado por `pWnd`.  
  
 `nIDTool`  
 Id. de la herramienta.  
  
 `lpszText`  
 Puntero al texto de la herramienta. Si este parámetro contiene el valor **LPSTR_TEXTCALLBACK**, **TTN_NEEDTEXT** mensajes de notificación irán al elemento primario de la ventana que `pWnd` señala.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El **lpRectTool** y **nIDTool** parámetros deben ser válidos, o si **lpRectTool** es NULL, **nIDTool** debe ser 0.  
  
 Un control de información sobre herramientas puede asociarse con más de una herramienta. Llame a esta función para registrar una herramienta con el control de información sobre herramientas, para que se muestre la información almacenada en la información sobre herramientas cuando el cursor está en la herramienta.  
  
> [!NOTE]
>  No se puede establecer una información sobre herramientas a un control estático mediante `AddTool`.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="adjustrect"></a>CToolTipCtrl::AdjustRect  
 Convierte entre el texto de un control de información sobre herramientas muestra el rectángulo y el rectángulo de la ventana.  
  
```  
BOOL AdjustRect(
    LPRECT lprc,  
    BOOL bLarger = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lprc`  
 Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que contiene un rectángulo de ventana de punta de herramienta o un rectángulo de presentación de texto.  
  
 `bLarger`  
 Si **TRUE**, `lprc` se utiliza para especificar un rectángulo de presentación de texto, y recibe el rectángulo de la ventana correspondiente. Si **FALSE**, `lprc` se utiliza para especificar un rectángulo de la ventana, y recibe el rectángulo de presentación de texto correspondientes.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el rectángulo se ajustó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro calcula el rectángulo de presentación de texto del control de información sobre herramienta de su rectángulo de la ventana o el rectángulo de ventana de sugerencia de herramienta necesaria para mostrar un rectángulo de presentación de texto especificado.  
  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_ADJUSTRECT](http://msdn.microsoft.com/library/windows/desktop/bb760352), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="create"></a>CToolTipCtrl::Create  
 Crea un control de información sobre herramienta y lo adjunta a un `CToolTipCtrl` objeto.  
  
```  
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Especifica la herramienta sugerencia ventana del control primario, normalmente un `CDialog`. No debe ser **NULL**.  
  
 `dwStyle`  
 Especifica el estilo del control de información sobre herramientas. Consulte la **comentarios** sección para obtener más información.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CToolTipCtrl` objeto se creó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CToolTipCtrl` en dos pasos. En primer lugar, llame al constructor para construir la `CToolTipCtrl` de objetos y, a continuación, llame a **crear** para crear el control de información sobre herramientas y adjuntarlo a la `CToolTipCtrl` objeto.  
  
 El `dwStyle` parámetro puede ser cualquier combinación de [estilos de ventana](../../mfc/reference/window-styles.md). Además, un control de información sobre herramientas tiene dos estilos de clase específico: **TTS_ALWAYSTIP** y **TTS_NOPREFIX**.  
  
|Estilo|Significado|  
|-----------|-------------|  
|**TTS_ALWAYSTIP**|Especifica que la información sobre herramientas aparece cuando el cursor esté sobre una herramienta, independientemente de si la ventana propietaria del control de información sobre herramientas está activa o inactiva. Sin este estilo, el control de información sobre herramientas aparece cuando está activa la ventana propietaria de la herramienta, pero no cuando está inactiva.|  
|**TTS_NOPREFIX**|Este estilo evita que el sistema quitando el carácter de y comercial (&) de una cadena. Si no tiene un control de información sobre herramientas la **TTS_NOPREFIX** estilo, el sistema quita automáticamente los caracteres y comercial, permitir que una aplicación utilice la misma cadena como un elemento de menú y como texto en un control de información sobre herramientas.|  
  
 Tiene un control de información sobre herramientas la `WS_POPUP` y **WS_EX_TOOLWINDOW** estilos de ventana, independientemente de si se especifica al crear el control.  
  
 Para crear un control de información sobre herramientas con los estilos extendidos de windows, llame a [CToolTipCtrl::CreateEx](#createex) en lugar de **crear**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="createex"></a>CToolTipCtrl::CreateEx  
 Crea un control (una ventana secundaria) y asociarlo con el `CToolTipCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwStyle = 0,  
    DWORD dwStyleEx = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Puntero a la ventana que es principal el control.  
  
 `dwStyle`  
 Especifica el estilo del control de información sobre herramientas. Consulte la **comentarios** sección de [crear](#create) para obtener más información.  
  
 *dwStyleEx*  
 Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 0 en caso contrario, es distinto de cero si se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `CreateEx` en lugar de **crear** para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="ctooltipctrl"></a>CToolTipCtrl::CToolTipCtrl  
 Construye un objeto `CToolTipCtrl`.  
  
```  
CToolTipCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Se debe llamar a **crear** después de crear el objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCControlLadenDialog&#74;](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]  
  
##  <a name="deltool"></a>CToolTipCtrl::DelTool  
 Quita la herramienta especificada por `pWnd` y `nIDTool` de la colección de herramientas compatibles con un control de información sobre herramientas.  
  
```  
void DelTool(
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana que contiene la herramienta.  
  
 `nIDTool`  
 Id. de la herramienta.  
  
##  <a name="getbubblesize"></a>CToolTipCtrl::GetBubbleSize  
 Recupera el tamaño de la información sobre herramientas.  
  
```  
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpToolInfo`  
 Un puntero a la sugerencia de herramienta [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETBUBBLESIZE](http://msdn.microsoft.com/library/windows/desktop/bb760387), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getcurrenttool"></a>CToolTipCtrl::GetCurrentTool  
 Recupera información, como el tamaño, la posición y el texto de la ventana de información sobre herramientas muestra el control de información sobre herramientas actual.  
  
```  
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `lpToolInfo`|Puntero a un [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) estructura que recibe información acerca de la ventana de información sobre herramientas actual.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si la información se recupera correctamente; de lo contrario,`false.`  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TTM_GETCURRENTTOOL](http://msdn.microsoft.com/library/windows/desktop/bb760389) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se recupera información sobre la ventana de información sobre herramientas actual.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1 Nº&6;](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]  
  
##  <a name="getdelaytime"></a>CToolTipCtrl::GetDelayTime  
 Recupera la inicial, emergente y reshow duraciones establecidas para un control de información sobre herramientas.  
  
```  
int GetDelayTime(DWORD dwDuration) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwDuration`  
 Marca que especifica qué valor de duración se recuperarán. Este parámetro puede ser uno de los siguientes valores:  
  
- `TTDT_AUTOPOP`Recuperar la longitud de tiempo que la ventana de información permanece visible si el puntero se detiene dentro del rectángulo de la herramienta.  
  
- `TTDT_INITIAL`Recuperar la longitud de tiempo que el puntero debe permanecer dentro del rectángulo de la herramienta antes de que aparezca la ventana de información.  
  
- `TTDT_RESHOW`Recuperar la longitud de tiempo que tarda en ventanas de información sobre herramientas subsiguientes a aparecer como el puntero se mueve de una herramienta a otra.  
  
### <a name="return-value"></a>Valor devuelto  
 El tiempo de retraso especificado, en milisegundos  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETDELAYTIME](http://msdn.microsoft.com/library/windows/desktop/bb760390), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getmargin"></a>CToolTipCtrl::GetMargin  
 Recupera la parte superior, izquierda, inferior y márgenes derecho establecido para una ventana de información.  
  
```  
void GetMargin(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lprc`  
 Dirección de un `RECT` estructura que recibirá la información de margen. Los miembros de la [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura no define un rectángulo delimitador. A efectos de este mensaje, los miembros de estructura se interpretan como sigue:  
  
|Miembro|Representación|  
|------------|--------------------|  
|**top**|Distancia entre el borde superior y la parte superior del texto de sugerencia, en píxeles.|  
|**left**|Distancia entre el borde izquierdo y el extremo izquierdo del texto de sugerencia, en píxeles.|  
|**parte inferior**|Distancia entre el borde inferior y la parte inferior del texto de sugerencia, en píxeles.|  
|**right**|Distancia entre el borde derecho y el extremo derecho del texto de sugerencia, en píxeles.|  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb760391), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getmaxtipwidth"></a>CToolTipCtrl::GetMaxTipWidth  
 Recupera el ancho máximo de una ventana de información.  
  
```  
int GetMaxTipWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho máximo de una ventana de información.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETMAXTIPWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760392), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="gettext"></a>CToolTipCtrl::GetText  
 Recupera el texto que un control de información sobre herramientas mantiene para una herramienta.  
  
```  
void GetText(
    CString& str,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 Hacer referencia a un `CString` objeto que recibe el texto de la herramienta.  
  
 `pWnd`  
 Puntero a la ventana que contiene la herramienta.  
  
 `nIDTool`  
 Id. de la herramienta.  
  
### <a name="remarks"></a>Comentarios  
 El `pWnd` y `nIDTool` parámetros identifican la herramienta. Si esa herramienta se ha registrado anteriormente con el control de información sobre herramientas a través de una llamada anterior a **CToolTipCtrl::AddTool**, el objeto al que hace referencia el `str` parámetro se asigna el texto de la herramienta.  
  
##  <a name="gettipbkcolor"></a>CToolTipCtrl::GetTipBkColor  
 Recupera el color de fondo en una ventana de información.  
  
```  
COLORREF GetTipBkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que representa el color de fondo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETTIPBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760394), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="gettiptextcolor"></a>CToolTipCtrl::GetTipTextColor  
 Recupera el color del texto en una ventana de información.  
  
```  
COLORREF GetTipTextColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que representa el color del texto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_GETTIPTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760395), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="gettitle"></a>CToolTipCtrl::GetTitle  
 Recupera el título del control de información sobre herramientas actual.  
  
```  
void GetTitle(PTTGETTITLE pttgt) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `pttgt`|Puntero a un [TTGETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760260) estructura que contiene información sobre el control de información sobre herramientas. Cuando este método finaliza, el `pszTitle` miembro de la [TTGETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760260) estructura de puntos para el texto del título.|  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TTM_GETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760396) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="gettoolcount"></a>CToolTipCtrl::GetToolCount  
 Recupera un recuento de las herramientas que se registra con el control de información sobre herramientas.  
  
```  
int GetToolCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un recuento de herramientas registradas con el control de información sobre herramientas.  
  
##  <a name="gettoolinfo"></a>CToolTipCtrl::GetToolInfo  
 Recupera la información que se mantiene un control de información sobre herramienta sobre una herramienta.  
  
```  
BOOL GetToolInfo(
    CToolInfo& ToolInfo,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *ToolInfo*  
 Hacer referencia a un `TOOLINFO` objeto que recibe el texto de la herramienta.  
  
 `pWnd`  
 Puntero a la ventana que contiene la herramienta.  
  
 `nIDTool`  
 Id. de la herramienta.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El **hwnd** y **uId** los miembros de la [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) estructura al que hace referencia *CToolInfo* identificar la herramienta. Si esa herramienta se ha registrado con el control de información sobre herramientas a través de una llamada anterior a `AddTool`, el `TOOLINFO` estructura se rellena con información acerca de la herramienta.  
  
##  <a name="hittest"></a>CToolTipCtrl::HitTest  
 Prueba en un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada y, si es así, recuperar información acerca de la herramienta.  
  
```  
BOOL HitTest(
    CWnd* pWnd,  
    CPoint pt,  
    LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana que contiene la herramienta.  
  
 `pt`  
 Puntero a un `CPoint` objeto que contiene las coordenadas del punto que se va a probar.  
  
 `lpToolInfo`  
 Puntero a [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) estructura que contiene información acerca de la herramienta.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el punto especificado por la información de la prueba de posicionamiento está dentro del rectángulo delimitador de la herramienta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si esta función devuelve un valor distinto de cero, la estructura que apunta `lpToolInfo` se rellena con información sobre la herramienta cuyo rectángulo se encuentra el punto.  
  
 El `TTHITTESTINFO` estructura se define como sigue:  
  
 `typedef struct _TT_HITTESTINFO { // tthti`  
  
 `HWND hwnd;   // handle of tool or window with tool`  
  
 `POINT pt;    // client coordinates of point to test`  
  
 `TOOLINFO ti; // receives information about the tool`  
  
 `} TTHITTESTINFO, FAR * LPHITTESTINFO;`  
  
 **HWND**  
 Especifica el identificador de la herramienta.  
  
 **PT**  
 Especifica las coordenadas de un punto, si el punto está en la herramienta rectángulo de límite.  
  
 **inteligencia de tiempo**  
 Información acerca de la herramienta. Para obtener más información acerca de la `TOOLINFO` estructura, vea [CToolTipCtrl::GetToolInfo](#gettoolinfo).  
  
##  <a name="pop"></a>CToolTipCtrl::Pop  
 Quita una ventana de información muestra la vista.  
  
```  
void Pop();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_POP](http://msdn.microsoft.com/library/windows/desktop/bb760401), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="popup"></a>CToolTipCtrl::Popup  
 Hace que el control de información sobre herramientas actual mostrar en las coordenadas del último mensaje de mouse.  
  
```  
void Popup();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TTM_POPUP](http://msdn.microsoft.com/library/windows/desktop/bb760402) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra una ventana de información sobre herramientas.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s&#1;7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]  
  
##  <a name="relayevent"></a>CToolTipCtrl:: RelayEvent  
 Pasa un mensaje del mouse a un control de información sobre herramientas para el procesamiento.  
  
```  
void RelayEvent(LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpMsg`  
 Puntero a un [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) estructura que contiene el mensaje de retransmisión.  
  
### <a name="remarks"></a>Comentarios  
 Un control de información sobre herramienta procesa sólo los mensajes siguientes, que se le envían por `RelayEvent`:  
  
|WM_LBUTTONDOWN|WM_MOUSEMOVE|  
|---------------------|-------------------|  
|`WM_LBUTTONUP`|`WM_RBUTTONDOWN`|  
|`WM_MBUTTONDOWN`|`WM_RBUTTONUP`|  
|`WM_MBUTTONUP`||  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="setdelaytime"></a>CToolTipCtrl::SetDelayTime  
 Establece el tiempo de retraso para un control de información sobre herramientas.  
  
```  
void SetDelayTime(UINT nDelay);

 
void SetDelayTime(
    DWORD dwDuration,  
    int iTime);
```  
  
### <a name="parameters"></a>Parámetros  
 *nDelay*  
 Especifica el nuevo tiempo de retraso, en milisegundos.  
  
 `dwDuration`  
 Marca que especifica qué valor de duración se recuperarán. Consulte [CToolTipCtrl::GetDelayTime](#getdelaytime) para obtener una descripción de los valores válidos.  
  
 *iTime*  
 El tiempo de retraso especificado, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 El tiempo de retardo es la longitud de tiempo que debe permanecer el cursor sobre una herramienta antes de que aparezca la ventana de información. El tiempo de retraso predeterminado es 500 milisegundos.  
  
##  <a name="setmargin"></a>CToolTipCtrl::SetMargin  
 Establece la parte superior, izquierda, inferior y los márgenes derecho de una ventana de información.  
  
```  
void SetMargin(LPRECT lprc);
```  
  
### <a name="parameters"></a>Parámetros  
 `lprc`  
 Dirección de un `RECT` estructura que contiene la información de margen para establecer. Los miembros de la `RECT` estructura no define un rectángulo delimitador. Consulte [CToolTipCtrl::GetMargin](#getmargin) para obtener una descripción de la información de margen.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb760406), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setmaxtipwidth"></a>CToolTipCtrl::SetMaxTipWidth  
 Establece el ancho máximo de una ventana de información.  
  
```  
int SetMaxTipWidth(int iWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 *iWidth*  
 Ancho de ventana de sugerencia de herramienta máximo se establezca.  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho máximo de sugerencia anterior.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETMAXTIPWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760408), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="settipbkcolor"></a>CToolTipCtrl::SetTipBkColor  
 Establece el color de fondo en una ventana de información.  
  
```  
void SetTipBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 `clr`  
 El nuevo color de fondo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTIPBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760411), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="settiptextcolor"></a>CToolTipCtrl::SetTipTextColor  
 Establece el color del texto en una ventana de información.  
  
```  
void SetTipTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 `clr`  
 El nuevo color de texto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTIPTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760413), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="settitle"></a>CToolTipCtrl::SetTitle  
 Agrega una cadena estándar de icono y el título de una información sobre herramientas.  
  
```  
BOOL SetTitle(
    UINT uIcon,  
    LPCTSTR lpstrTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 *uIcon*  
 Consulte *icono* en [TTM_SETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760414) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *lpstrTitle*  
 Puntero a la cadena de título.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TTM_SETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760414), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="settoolinfo"></a>CToolTipCtrl::SetToolInfo  
 Establece la información que mantiene información sobre herramientas para una herramienta.  
  
```  
void SetToolInfo(LPTOOLINFO lpToolInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpToolInfo`  
 Un puntero a un [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) estructura que especifica la información para establecer.  
  
##  <a name="settoolrect"></a>CToolTipCtrl::SetToolRect  
 Establece un nuevo rectángulo delimitador para una herramienta.  
  
```  
void SetToolRect(
    CWnd* pWnd,  
    UINT_PTR nIDTool,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Puntero a la ventana que contiene la herramienta.  
  
 `nIDTool`  
 Id. de la herramienta.  
  
 `lpRect`  
 Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que especifica el nuevo rectángulo delimitador.  
  
##  <a name="setwindowtheme"></a>CToolTipCtrl::SetWindowTheme  
 Establece el estilo visual de la ventana.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszSubAppName`  
 Un puntero a una cadena Unicode que contiene el estilo visual a establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 No se utiliza el valor devuelto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [TTM_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb760418) de mensajes, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="update"></a>CToolTipCtrl::Update  
 Fuerza a la herramienta actual se vuelva a dibujar.  
  
```  
void Update();
```  
  
##  <a name="updatetiptext"></a>CToolTipCtrl::UpdateTipText  
 Actualiza el texto de sugerencia para herramientas de este control.  
  
```  
void UpdateTipText(
    LPCTSTR lpszText,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);

 
void UpdateTipText(
    UINT nIDText,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszText`  
 Puntero al texto de la herramienta.  
  
 `pWnd`  
 Puntero a la ventana que contiene la herramienta.  
  
 `nIDTool`  
 Id. de la herramienta.  
  
 `nIDText`  
 Id. del recurso de cadena que contiene el texto de la herramienta.  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CToolBar (clase)](../../mfc/reference/ctoolbar-class.md)

