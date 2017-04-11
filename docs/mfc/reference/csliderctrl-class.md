---
title: CSliderCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CSliderCtrl
- slider controls, CSliderCtrl class
- CSliderCtrl class, common controls
- CSliderCtrl class
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 745dc253ac0837ffc62f47db2038e6302b83b558
ms.lasthandoff: 04/01/2017

---
# <a name="csliderctrl-class"></a>CSliderCtrl (clase)
Proporciona la funcionalidad del control deslizante común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|Construye un objeto `CSliderCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSliderCtrl::ClearSel](#clearsel)|Borra la selección actual en un control deslizante.|  
|[CSliderCtrl::ClearTics](#cleartics)|Quita las marcas de graduación actual de un control deslizante.|  
|[CSliderCtrl::Create](#create)|Crea un control deslizante y lo adjunta a un `CSliderCtrl` objeto.|  
|[CSliderCtrl::CreateEx](#createex)|Crea un control deslizante con los estilos extendidos de Windows especificados y lo adjunta a un `CSliderCtrl` objeto.|  
|[CSliderCtrl::GetBuddy](#getbuddy)|Recupera el identificador de ventana deslizante control relacionada en una ubicación especificada.|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|Recupera el tamaño del canal del control deslizante.|  
|[CSliderCtrl::GetLineSize](#getlinesize)|Recupera el tamaño de la línea de un control deslizante.|  
|[CSliderCtrl::GetNumTics](#getnumtics)|Recupera el número de marcas de graduación en un control deslizante.|  
|[CSliderCtrl::GetPageSize](#getpagesize)|Recupera el tamaño de página de un control deslizante.|  
|[CSliderCtrl::GetPos](#getpos)|Recupera la posición actual del control deslizante.|  
|[CSliderCtrl::GetRange](#getrange)|Recupera las posiciones mínimas y máxima para un control deslizante.|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|Recupera la posición máxima para un control deslizante.|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|Recupera la posición mínima para un control deslizante.|  
|[CSliderCtrl::GetSelection](#getselection)|Recupera el intervalo de la selección actual.|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|Recupera la longitud del control deslizante en el control de barra de seguimiento actual.|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|Recupera el tamaño de la posición del control deslizante.|  
|[CSliderCtrl::GetTic](#gettic)|Recupera la posición de la marca de graduación especificado.|  
|[CSliderCtrl::GetTicArray](#getticarray)|Recupera la matriz de posiciones de marca de graduación para un control deslizante.|  
|[CSliderCtrl::GetTicPos](#getticpos)|Recupera la posición de la marca de graduación especificado, en coordenadas de cliente.|  
|[CSliderCtrl::GetToolTips](#gettooltips)|Recupera el identificador del control de información sobre herramientas asignado para el control deslizante, si lo hay.|  
|[CSliderCtrl::SetBuddy](#setbuddy)|Asigna una ventana como la ventana relacionada para un control deslizante.|  
|[CSliderCtrl::SetLineSize](#setlinesize)|Establece el tamaño de la línea de un control deslizante.|  
|[CSliderCtrl::SetPageSize](#setpagesize)|Establece el tamaño de página de un control deslizante.|  
|[CSliderCtrl::SetPos](#setpos)|Establece la posición actual del control deslizante.|  
|[CSliderCtrl::SetRange](#setrange)|Establece las posiciones mínimas y máxima para un control deslizante.|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|Establece la posición máxima para un control deslizante.|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|Establece la posición mínima para un control deslizante.|  
|[CSliderCtrl::SetSelection](#setselection)|Establece la duración de la selección actual.|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|Establece la longitud del control deslizante en el control de barra de seguimiento actual.|  
|[CSliderCtrl::SetTic](#settic)|Establece la posición de la marca de graduación especificado.|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|Establece la frecuencia de TIC marcas por incremento del control deslizante.|  
|[CSliderCtrl::SetTipSide](#settipside)|Posiciones un control de información sobre herramientas utilizado por un control de barra de seguimiento.|  
|[CSliderCtrl::SetToolTips](#settooltips)|Asigna un control de información sobre herramientas para un control deslizante.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control deslizante" (también conocido como una barra de seguimiento) es una ventana que contiene un control deslizante y las marcas de graduación opcionales. Cuando el usuario mueve el control deslizante, con el mouse o las teclas de dirección, el control envía mensajes de notificación para indicar el cambio.  
  
 Controles deslizantes son útiles cuando desea que el usuario seleccione un valor discreto o un conjunto de valores consecutivos en un intervalo. Por ejemplo, podría usar un control deslizante para permitir al usuario establecer la velocidad de repetición del teclado moviendo el control deslizante hasta una marca de graduación determinado.  
  
 Este control (y, por tanto, la `CSliderCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 El control deslizante se mueve en incrementos que especifican al crearlo. Por ejemplo, si se especifica que el control deslizante debe tener un intervalo de cinco, el control deslizante solo puede ocupar seis posiciones: una posición en el lado izquierdo del control deslizante y una posición para cada incremento en el intervalo. Normalmente, cada una de estas posiciones se identifica mediante una marca de graduación.  
  
 Crear un control deslizante mediante el constructor y el **crear** función miembro de `CSliderCtrl`. Una vez haya creado un control deslizante, puede usar funciones de miembro en `CSliderCtrl` para cambiar muchos de sus propiedades. Cambios que puede realizar incluyen establecer las posiciones mínimas y máxima para el control deslizante, dibujar las marcas de graduación, establecer un intervalo de selección y volver a colocar el control deslizante.  
  
 Para obtener más información sobre el uso de `CSliderCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CSliderCtrl](../../mfc/using-csliderctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="clearsel"></a>CSliderCtrl::ClearSel  
 Borra la selección actual en un control deslizante.  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bRedraw`  
 Volver a dibujar la marca. Si este parámetro es **TRUE**, se vuelve a dibujarse el control deslizante una vez borrada la selección; en caso contrario, el control deslizante no vuelve a dibujarse.  
  
##  <a name="cleartics"></a>CSliderCtrl::ClearTics  
 Quita las marcas de graduación actual de un control deslizante.  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bRedraw`  
 Volver a dibujar la marca. Si este parámetro es **TRUE**, se vuelve a dibujarse el control deslizante después de que se desactivan las marcas de graduación; en caso contrario, el control deslizante no vuelve a dibujarse.  
  
##  <a name="create"></a>CSliderCtrl::Create  
 Crea un control deslizante y lo adjunta a un `CSliderCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control deslizante. Aplicar cualquier combinación de [estilos de control deslizante](http://msdn.microsoft.com/library/windows/desktop/bb760147), que se describen en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)], para el control.  
  
 `rect`  
 Especifica el tamaño y la posición del control deslizante. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.  
  
 `pParentWnd`  
 Especifica la ventana del elemento primario del control deslizante, normalmente un `CDialog`. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control deslizante  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización se realizó correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CSliderCtrl` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control deslizante y lo adjunta a la `CSliderCtrl` objeto.  
  
 Dependiendo de los valores establecidos para `dwStyle`, el control deslizante puede tener una orientación vertical u horizontal. Puede tener las marcas de graduación en cualquier lado, ambos o ninguno. También se puede utilizar para especificar un intervalo de valores consecutivos.  
  
 Para aplicar estilos de ventana extendidos para el control deslizante, llame al [CreateEx](#createex) en lugar de **crear**.  
  
##  <a name="createex"></a>CSliderCtrl::CreateEx  
 Crea un control (una ventana secundaria) y lo asocia a la `CSliderCtrl` objeto.  
  
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
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Especifica el estilo del control deslizante. Aplicar cualquier combinación de [estilos de control deslizante](http://msdn.microsoft.com/library/windows/desktop/bb760147), que se describen en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)], para el control.  
  
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
  
##  <a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl  
 Construye un objeto `CSliderCtrl`.  
  
```  
CSliderCtrl();
```  
  
##  <a name="getbuddy"></a>CSliderCtrl::GetBuddy  
 Recupera el identificador de ventana deslizante control relacionada en una ubicación especificada.  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `fLocation`  
 Un valor booleano que indica cuál de los dos identificadores de ventana conocido para recuperar. Puede presentar uno de los siguientes valores:  
  
- **TRUE** recupera el identificador para el contacto a la izquierda del control deslizante. Si usa el control deslizante de la `TBS_VERT` estilo, el mensaje recuperará el amigo encima del control deslizante.  
  
- **FALSE** recupera el identificador para el contacto a la derecha del control deslizante. Si usa el control deslizante de la `TBS_VERT` estilo, el mensaje recuperará el amigo debajo del control deslizante.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana relacionada en la ubicación especificada por `fLocation`, o **NULL** si no existe ninguna ventana amigo en esa ubicación.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_GETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760178), tal y como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getchannelrect"></a>CSliderCtrl::GetChannelRect  
 Recupera el tamaño y la posición del rectángulo delimitador para el canal del control deslizante.  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lprc`  
 Un puntero a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que contiene el tamaño y la posición del canal del rectángulo delimitador cuando la función devuelve.  
  
### <a name="remarks"></a>Comentarios  
 El canal es el área que se mueve el control deslizante y que contiene el elemento resaltado cuando se selecciona un intervalo.  
  
##  <a name="getlinesize"></a>CSliderCtrl::GetLineSize  
 Recupera el tamaño de la línea para un control deslizante.  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de una línea para el control deslizante.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de la línea afecta a la cantidad el control deslizante se mueve para la **TB_LINEUP** y **TB_LINEDOWN** notificaciones. La configuración predeterminada para el tamaño de línea es 1.  
  
##  <a name="getnumtics"></a>CSliderCtrl::GetNumTics  
 Recupera el número de marcas de graduación en un control deslizante.  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de marcas de graduación en el control deslizante.  
  
##  <a name="getpagesize"></a>CSliderCtrl::GetPageSize  
 Recupera el tamaño de la página de un control deslizante.  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de una página para el control deslizante.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de página afecta a la cantidad el control deslizante se mueve para la **TB_PAGEUP** y **TB_PAGEDOWN** notificaciones.  
  
##  <a name="getpos"></a>CSliderCtrl::GetPos  
 Recupera la posición actual del control deslizante en un control deslizante.  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Posición actual.  
  
##  <a name="getrange"></a>CSliderCtrl::GetRange  
 Recupera las posiciones mínimas y máxima para el control deslizante en un control deslizante.  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nMin`  
 Referencia a un entero que recibe la posición de mínimo.  
  
 `nMax`  
 Referencia a un entero que recibe la posición máxima.  
  
### <a name="remarks"></a>Comentarios  
 Esta función copia los valores a los enteros encontrados por `nMin` y `nMax`.  
  
##  <a name="getrangemax"></a>CSliderCtrl::GetRangeMax  
 Recupera la posición máxima para el control deslizante en un control deslizante.  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La posición del control máximo.  
  
##  <a name="getrangemin"></a>CSliderCtrl::GetRangeMin  
 Recupera la posición mínima para el control deslizante en un control deslizante.  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La posición del control mínimo.  
  
##  <a name="getselection"></a>CSliderCtrl::GetSelection  
 Recupera las posiciones inicial y finales de la selección actual en un control deslizante.  
  
```  
void GetSelection(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nMin`  
 Referencia a un entero que recibe la posición inicial de la selección actual.  
  
 `nMax`  
 Referencia a un entero que recibe la posición final de la selección actual.  
  
##  <a name="getthumblength"></a>CSliderCtrl::GetThumbLength  
 Recupera la longitud del control deslizante en el control de barra de seguimiento actual.  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud del control deslizante, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TBM_GETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760201) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getthumbrect"></a>CSliderCtrl::GetThumbRect  
 Recupera el tamaño y la posición del rectángulo delimitador para el control deslizante (USB) en un control deslizante.  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lprc`  
 Un puntero a un `CRect` objeto que contiene el rectángulo delimitador para el control deslizante cuando la función devuelve.  
  
##  <a name="gettic"></a>CSliderCtrl::GetTic  
 Recupera la posición de una marca de graduación en un control deslizante.  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nTic`  
 Índice basado en cero que identifica una marca de graduación.  
  
### <a name="return-value"></a>Valor devuelto  
 La posición de la marca de graduación especificado o - 1 si `nTic` no especifica un índice válido.  
  
##  <a name="getticarray"></a>CSliderCtrl::GetTicArray  
 Recupera la dirección de la matriz que contiene las posiciones de las marcas de graduación para un control deslizante.  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La dirección de la matriz que contiene las posiciones de marca de graduación para el control deslizante.  
  
##  <a name="getticpos"></a>CSliderCtrl::GetTicPos  
 Recupera la posición física actual de una marca de graduación en un control deslizante.  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nTic`  
 Índice basado en cero que identifica una marca de graduación.  
  
### <a name="return-value"></a>Valor devuelto  
 La posición física, en coordenadas de cliente, de la marca de graduación especificado o - 1 si `nTic` no especifica un índice válido.  
  
##  <a name="gettooltips"></a>CSliderCtrl::GetToolTips  
 Recupera el identificador del control de información sobre herramientas asignado para el control deslizante, si lo hay.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto, o **NULL** si la información sobre herramientas no está en uso. Si el control deslizante no usa el **TBS_TOOLTIPS** estilo, el valor devuelto es **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760209), tal y como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Tenga en cuenta que esta función miembro devuelve un `CToolTipCtrl` objeto en lugar de un identificador de un control.  
  
 Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setbuddy"></a>CSliderCtrl::SetBuddy  
 Asigna una ventana como la ventana relacionada para un control deslizante.  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndBuddy`  
 Un puntero a un `CWnd` objeto que se establecerá como amigo del control deslizante.  
  
 `fLocation`  
 Valor que especifica la ubicación en la que se va a mostrar la ventana relacionada. Este valor puede ser uno de los siguientes:  
  
- **TRUE** el amigo aparecerán a la izquierda de la barra de seguimiento si el control trackbar utiliza el `TBS_HORZ` estilo. Si la barra de seguimiento utiliza la `TBS_VERT` de estilo, el amigo aparece encima del control trackbar.  
  
- **FALSE** el amigo aparecerán a la derecha de la barra de seguimiento si el control de barra de seguimiento utiliza la `TBS_HORZ` estilo. Si la barra de seguimiento utiliza la `TBS_VERT` de estilo, el amigo aparece debajo del control trackbar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que se asignó previamente para el control deslizante en esa ubicación.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_SETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760213), tal y como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Tenga en cuenta que esta función miembro utiliza punteros a `CWnd` objetos, en lugar de identificadores de ventana para su valor devuelto y el parámetro.  
  
 Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setlinesize"></a>CSliderCtrl::SetLineSize  
 Establece el tamaño de la línea para un control deslizante.  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSize`  
 El nuevo tamaño de línea del control deslizante.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de la línea anterior.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de la línea afecta a la cantidad el control deslizante se mueve para la **TB_LINEUP** y **TB_LINEDOWN** notificaciones.  
  
##  <a name="setpagesize"></a>CSliderCtrl::SetPageSize  
 Establece el tamaño de la página de un control deslizante.  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>Parámetros  
 `nSize`  
 El nuevo tamaño de página del control deslizante.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de página anterior.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de página afecta a la cantidad el control deslizante se mueve para la **TB_PAGEUP** y **TB_PAGEDOWN** notificaciones.  
  
##  <a name="setpos"></a>CSliderCtrl::SetPos  
 Establece la posición actual del control deslizante en un control deslizante.  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Especifica la nueva posición del control deslizante.  
  
##  <a name="setrange"></a>CSliderCtrl::SetRange  
 Establece la duración (posiciones mínima y máxima) para el control deslizante en un control deslizante.  
  
```  
void SetRange(
    int nMin,  
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMin`  
 Posición mínimo para el control deslizante.  
  
 `nMax`  
 Posición máxima para el control deslizante.  
  
 `bRedraw`  
 La marca de renegociación. Si este parámetro es **TRUE**, se vuelve a dibujarse el control deslizante después de establece el intervalo; en caso contrario, el control deslizante no vuelve a dibujarse.  
  
##  <a name="setrangemax"></a>CSliderCtrl::SetRangeMax  
 Establece la duración máxima para el control deslizante en un control deslizante.  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMax`  
 Posición máxima para el control deslizante.  
  
 `bRedraw`  
 La marca de renegociación. Si este parámetro es **TRUE**, se vuelve a dibujarse el control deslizante después de establece el intervalo; en caso contrario, el control deslizante no vuelve a dibujarse.  
  
##  <a name="setrangemin"></a>CSliderCtrl::SetRangeMin  
 Establece la duración mínima para el control deslizante en un control deslizante.  
  
```  
void SetRangeMin(
    int nMin,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMin`  
 Posición mínimo para el control deslizante.  
  
 `bRedraw`  
 La marca de renegociación. Si este parámetro es **TRUE**, se vuelve a dibujarse el control deslizante después de establece el intervalo; en caso contrario, el control deslizante no vuelve a dibujarse.  
  
##  <a name="setselection"></a>CSliderCtrl::SetSelection  
 Establece las posiciones inicial y finales de la selección actual en un control deslizante.  
  
```  
void SetSelection(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMin`  
 Posición inicial para el control deslizante.  
  
 `nMax`  
 Posición final para el control deslizante.  
  
##  <a name="setthumblength"></a>CSliderCtrl::SetThumbLength  
 Establece la longitud del control deslizante en el control de barra de seguimiento actual.  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `nLength`|Longitud del control deslizante, en píxeles.|  
  
### <a name="remarks"></a>Comentarios  
 Este método requiere que el control trackbar se establezca en [TBS_FIXEDLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760147) estilo.  
  
 Este método envía el [TBM_SETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760234) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_sliderCtrl`, que se usa para tener acceso al control de barra de seguimiento actual. El ejemplo también define una variable, `thumbLength`, que se utiliza para almacenar la longitud predeterminada del componente de posición del control trackbar. Estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1 n.º 1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el componente de posición del control trackbar hasta dos veces su longitud predeterminada.  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1 n.º 2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="settic"></a>CSliderCtrl::SetTic  
 Establece la posición de una marca de graduación en un control deslizante.  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>Parámetros  
 `nTic`  
 Posición de la marca de graduación. Este parámetro debe especificar un valor positivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se establece la marca de graduación; en caso contrario es 0.  
  
##  <a name="setticfreq"></a>CSliderCtrl::SetTicFreq  
 Establece la frecuencia con que marca las marcas se muestran en un control deslizante.  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>Parámetros  
 *nFreq*  
 Frecuencia de las marcas de graduación.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, si la frecuencia se establece en 2, se muestra una marca de graduación para cada incremento otro intervalo del control deslizante. La configuración predeterminada para la frecuencia es 1 (es decir, cada incremento en el intervalo está asociado con una marca de graduación).  
  
 Debe crear el control con el `TBS_AUTOTICKS` estilo que se va a usar esta función. Para obtener más información, consulte [CSliderCtrl::Create](#create).  
  
##  <a name="settipside"></a>CSliderCtrl::SetTipSide  
 Posiciones un control de información sobre herramientas utilizado por un control de barra de seguimiento.  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>Parámetros  
 `nLocation`  
 Valor que representa la ubicación en la que se va a mostrar el control de información sobre herramientas. Para obtener una lista de valores posibles, vea el mensaje de Win32 [TBM_SETTIPSIDE](http://msdn.microsoft.com/library/windows/desktop/bb760240), tal y como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que representa la ubicación anterior del control de información sobre herramientas. El valor devuelto es igual a uno de los valores posibles para `nLocation`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 **TBM_SETTIPSIDE**, tal y como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Control deslizante controles que usan el **TBS_TOOLTIPS** aplicar estilo a mostrar información sobre herramientas. Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) en el [!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
##  <a name="settooltips"></a>CSliderCtrl::SetToolTips  
 Asigna un control de información sobre herramientas para un control deslizante.  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndTip`  
 Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto que contiene la información sobre herramientas para usar con el control deslizante.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TBM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760242), tal y como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Cuando se crea un control deslizante con el **TBS_TOOLTIPS** estilo, crea un control de información sobre herramientas predeterminada que aparece junto al control deslizante, mostrar la posición actual del control deslizante. Para obtener una descripción de los estilos de control deslizante, consulte [estilos del Control Trackbar](http://msdn.microsoft.com/library/windows/desktop/bb760147) en el [!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [CMNCTRL2 de ejemplo MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl (clase)](../../mfc/reference/cprogressctrl-class.md)

