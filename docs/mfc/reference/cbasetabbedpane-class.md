---
title: Clase CBaseTabbedPane | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
dev_langs:
- C++
helpviewer_keywords:
- CBaseTabbedPane class
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b72804dd8b2ca2253caff4cebf5b0631ae6040c6
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane (Clase)
Amplía la funcionalidad de la [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) para admitir la creación de ventanas con fichas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CBaseTabbedPane::AddTab](#addtab)|Agrega una nueva pestaña a un panel con fichas.|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica si se puede destruir un panel con fichas vacío.|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Se aplica la configuración de ficha, que se carga desde el registro, en un panel con fichas.|  
|[CBaseTabbedPane::CanFloat](#canfloat)|Determina si el panel puede flotar. (Invalida [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina si el título para el panel con fichas debe mostrar el mismo texto como la ficha activa.|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Invalida [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|  
|[CBaseTabbedPane::DetachPane](#detachpane)|Convierte uno o más paneles acoplables en documentos con fichas de MDI.|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Habilita o deshabilita la capacidad del panel con fichas para sincronizar el texto de título con el texto de etiqueta en la ficha activa.|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Restaura el orden de tabulación interno a un estado predeterminado.|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Devuelve un panel que se encuentra en una ficha cuando la pestaña se identifica mediante un índice de base cero de tabulación.|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Devuelve un panel que se identifica mediante el identificador del panel.|  
|[CBaseTabbedPane::FloatTab](#floattab)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable.|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Devuelve el orden predeterminado de las fichas en el panel.|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Recupera un puntero a la primera ficha mostrada.|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|Recupera el mínimo tamaño permitido para el panel. (Invalida [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Devuelve un identificador para el icono del panel. (Invalida [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Devuelve una lista de los paneles que están contenidos en el panel con fichas.|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Devuelve los rectángulos delimitadores para las áreas de pestaña superior e inferior.|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Devuelve el número de fichas en una ventana de ficha.|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Obtiene la ventana de pestaña (ajustado) subyacente.|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Devuelve el número de fichas mostradas.|  
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Determina si el panel con fichas se puede cambiar a modo de ocultación automática.|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Determina si se oculta el panel con fichas si sólo se muestra una ficha.|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Se utiliza internamente durante la serialización.|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Vuelve a calcular la información de diseño para el panel. (Invalida [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|  
|[CBaseTabbedPane::RemovePane](#removepane)|Quita un panel del panel con fichas.|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|Se utiliza internamente durante la serialización.|  
|`CBaseTabbedPane::Serialize`|(Invalida [CDockablePane::Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6).)|  
|`CBaseTabbedPane::SerializeTabWindow`|Se utiliza internamente durante la serialización.|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Determina si la barra de controles de fichas se destruirán automáticamente.|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Alterna entre mostrar el panel de acoplamiento y modo de ocultación automática. (Invalida [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|  
|[CBaseTabbedPane::ShowTab](#showtab)|Muestra u oculta una pestaña.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase es una clase abstracta y no se pueden crear instancias. Implementa los servicios que son comunes a todos los tipos de las fichas.  
  
 Actualmente, la biblioteca incluye dos clases derivadas de panel con fichas: [CTabbedPane clase](../../mfc/reference/ctabbedpane-class.md) y [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Un `CBaseTabbedPane` objeto contiene un puntero a un [CMFCBaseTabCtrl clase](../../mfc/reference/cmfcbasetabctrl-class.md) objeto. [Clase CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) se convierte en una ventana secundaria del panel con fichas.  
  
 Para obtener más información sobre cómo crear paneles con fichas, consulte [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), [CTabbedPane clase](../../mfc/reference/ctabbedpane-class.md), y [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 `CBaseTabbedPane`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxBaseTabbedPane.h  
  
##  <a name="addtab"></a>CBaseTabbedPane::AddTab  
 Agrega una nueva pestaña a un panel con fichas.  
  
```  
virtual BOOL AddTab(
    CWnd* pNewBar,  
    BOOL bVisible = TRUE,  
    BOOL bSetActive = TRUE,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pNewBar`  
 Un puntero al panel para agregar. Este puntero puede ser válido después de llamar a este método. Para obtener más información, vea la sección Comentarios.  
  
 [in] `bVisible`  
 `TRUE`para mostrar la ficha; de lo contrario, `FALSE`.  
  
 [in] `bSetActive`  
 `TRUE`para realizar la pestaña de la pestaña activa; de lo contrario, `FALSE`.  
  
 [in] `bDetachable`  
 `TRUE`Para hacer que la ficha desmontable; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se agregó correctamente como una pestaña y no se destruye en el proceso. `FALSE`Si el panel que se va a agregar es un objeto de tipo `CBaseTabbedPane`. Para obtener más información, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para agregar un panel como una nueva pestaña en un panel con fichas. Si `pNewBar` apunta a un objeto de tipo `CBaseTabbedPane`, se copian todas sus fichas en el panel con fichas y, a continuación, `pNewBar` se destruye. Por lo tanto, `pNewBar` se convierte en un puntero no válido y no debe usarse.  
  
##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 Especifica si se puede destruir un panel con fichas vacío.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede destruir un panel con fichas vacío; de lo contrario, `FALSE`. La implementación predeterminada siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Si no se permite que un panel con fichas vacío se destruye, el marco de trabajo oculta el panel en su lugar.  
  
##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo  
 Carga la configuración de la ficha del registro y los aplica a un panel con fichas.  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bUseTabIndexes`  
 Este parámetro se utiliza internamente por el marco de trabajo.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se vuelva a cargar la información de estado de acoplamiento del registro. El método obtiene información sobre el orden de tabulación y los nombres de ficha de un panel con fichas.  
  
##  <a name="canfloat"></a>CBaseTabbedPane::CanFloat  
 Especifica si puede flotar el panel con fichas.  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede flotar; de lo contrario, `FALSE`.  
  
##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName  
 Determina si el título para el panel con fichas debe mostrar el mismo texto como la ficha activa.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establece el texto del título del panel con fichas en el texto de la pestaña activa; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El método se utiliza para determinar si el texto muestra en los duplicados de título del panel con fichas la etiqueta de la ficha activa. Puede habilitar o deshabilitar esta funcionalidad mediante una llamada a [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).  
  
##  <a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument  
 Convierte uno o más paneles acoplables en documentos con fichas de MDI.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActiveTabOnly`  
 Al convertir un panel con fichas, especifique `TRUE` para convertir sólo la pestaña activa. Especificar `FALSE` para convertir todas las fichas en el panel.  
  
##  <a name="detachpane"></a>CBaseTabbedPane::DetachPane  
 Desasocia un panel desde el panel con fichas.  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Puntero al panel para separar.  
  
 [in] `bHide`  
 Parámetro booleano que especifica si el marco de trabajo oculta el panel después de que se desasocia.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de trabajo correctamente separa el panel; `FALSE` si `pBar` es `NULL` o hace referencia a un panel que no está en el panel con fichas.  
  
### <a name="remarks"></a>Comentarios  
 El marco de flota el panel separado si es posible. Para obtener más información, consulte [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).  
  
##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName  
 Habilita o deshabilita la capacidad del panel con fichas para sincronizar el texto de título con el texto de etiqueta en la ficha activa.  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`para sincronizar el título del panel con fichas con el título de la pestaña activa; de lo contrario, `FALSE`.  
  
##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray  
 Restaura el orden de tabulación interno a un estado predeterminado.  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama cuando el marco de trabajo restaura una barra de Outlook en un estado inicial.  
  
##  <a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID  
 Devuelve un panel identificado por el identificador del panel.  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uBarID`  
 Especifica el identificador del panel para buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al panel si se encuentra; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Este método compara todas las fichas en el panel y devuelve el marcado con el identificador especificado por el `uBarID` parámetro.  
  
##  <a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber  
 Devuelve un panel que se encuentra en una ficha.  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTabNum`  
 Especifica el índice de base cero de la ficha para recuperar.  
  
 [in] `bGetWrappedBar`  
 `TRUE`para devolver la ventana subyacente (ajustada) del panel en lugar del panel. de lo contrario, `FALSE`. Esto sólo se aplica a los paneles que se deriva de [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Si no se encuentra el panel, se devuelve un puntero válido para el panel que se va a buscar; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar el panel que se encuentran en la ficha especificada por el `nTabNum` parámetro.  
  
##  <a name="floattab"></a>CBaseTabbedPane::FloatTab  
 Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pBar`  
 Un puntero al panel para float.  
  
 [in] `nTabID`  
 Especifica el índice de base cero de la ficha para float.  
  
 [in] `dockMethod`  
 Especifica el método que utilice para hacer flotar el panel. Para obtener más información, vea la sección Comentarios.  
  
 [in] `bHide`  
 `TRUE`Para ocultar el panel antes flotante; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel flotante; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para convertir en flotante un panel que se encuentra actualmente en una pestaña desmontable.  
  
 Si desea desasociar un panel mediante programación, especifique `DM_SHOW` para el `dockMethod` parámetro. Si desea que el panel en la misma posición que flota previamente flotante, especifique `DM_DBL_CLICK` como el `dockMethod` parámetro.  
  
##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder  
 Devuelve el orden predeterminado de las fichas en el panel.  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CArray` objeto que especifica el orden predeterminado de las fichas en el panel.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando una barra de Outlook se restablece a un estado inicial.  
  
##  <a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab  
 Recupera un puntero a la primera ficha mostrada.  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTabNum`  
 Una referencia a un entero. Este método escribe el índice de base cero de la primera ficha mostrada en este parámetro, o -1 si no muestra ficha se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un puntero a la primera ficha mostrada; de lo contrario, `NULL`.  
  
##  <a name="getminsize"></a>CBaseTabbedPane::GetMinSize  
 Recupera el mínimo tamaño permitido para el panel.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `size`  
 Un `CSize` objeto que se rellena con el mínimo tamaño permitido.  
  
### <a name="remarks"></a>Comentarios  
 Si está activo el tratamiento coherente de tamaño mínimo del panel ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` se rellena con el mínimo tamaño permitido para la ficha activa. De lo contrario, `size` se rellena con el valor devuelto de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon  
 Recupera el mínimo tamaño permitido para el panel.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `size`  
 Un `CSize` objeto que se rellena con el mínimo tamaño permitido.  
  
### <a name="remarks"></a>Comentarios  
 Si está activo el tratamiento coherente de tamaño mínimo del panel ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` se rellena con el mínimo tamaño permitido para la ficha activa. De lo contrario, `size` se rellena con el valor devuelto de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpanelist"></a>CBaseTabbedPane::GetPaneList  
 Devuelve una lista de los paneles que están contenidos en el panel con fichas.  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `lst`  
 Un `CObList` que se rellena con los paneles que se encuentran en el panel con fichas.  
  
 [in] `pRTCFilter`  
 Si no es `NULL`, la lista devuelta contiene sólo los paneles de la clase en tiempo de ejecución.  
  
##  <a name="gettabarea"></a>CBaseTabbedPane::GetTabArea  
 Devuelve los rectángulos delimitadores para las áreas de pestaña superior e inferior.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectTabAreaTop`  
 Recibe las coordenadas de pantalla del área de ficha superior.  
  
 [out] `rectTabAreaBottom`  
 Recibe las coordenadas de pantalla de la parte inferior de la ficha.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para determinar los rectángulos delimitadores, en coordenadas de pantalla para las áreas de pestaña superior e inferior.  
  
##  <a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum  
 Devuelve el número de fichas en una ventana de ficha.  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de fichas en el panel con fichas.  
  
##  <a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow  
 Obtiene la ventana de pestaña (ajustado) subyacente.  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana de la ficha subyacente.  
  
##  <a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum  
 Devuelve el número de fichas visibles.  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de fichas visibles, que será mayor o igual que cero.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para determinar el número de fichas visibles en el panel con fichas.  
  
##  <a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode  
 Determina si el panel con pestañas se puede cambiar a modo de ocultación automática.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede cambiar a modo de ocultación automática; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si el modo de ocultación automática está deshabilitado, ningún botón de pin se muestra en el título del panel con fichas.  
  
##  <a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab  
 Determina si se oculta el panel con fichas si sólo se muestra una ficha.  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si no se muestra la ventana de la ficha cuando hay sólo una ficha visible; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si el panel no se muestra porque está abierta sólo una ficha, puede llamar a este método para determinar si el panel con fichas funciona correctamente.  
  
##  <a name="removepane"></a>CBaseTabbedPane::RemovePane  
 Quita un panel del panel con fichas.  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pBar`  
 Un puntero al panel para quitar del panel con fichas.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha quitado correctamente el panel desde el panel con fichas y el panel con fichas sigue siendo válido. `FALSE`Si se ha quitado el último panel desde el panel con fichas y el panel con fichas está a punto de ser destruidos. Si el valor devuelto es `FALSE`, no utilice el panel con fichas más.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para quitar el panel especificado por el `pBar` parámetro desde el panel con fichas.  
  
##  <a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy  
 Determina si la barra de controles de fichas se destruirán automáticamente.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAutoDestroy`  
 `TRUE`Si el panel con fichas se crea dinámicamente y no se controla su duración; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Establecer el modo auto-destruir `TRUE` si crea dinámicamente un panel con fichas y si no se controla su duración. Si destruir automáticamente el modo es `TRUE`, el panel con fichas se destruirán automáticamente por el marco de trabajo.  
  
##  <a name="showtab"></a>CBaseTabbedPane::ShowTab  
 Muestra u oculta una pestaña.  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero al panel para mostrar u ocultar.  
  
 [in] `bShow`  
 `TRUE`para mostrar el panel; `FALSE` para ocultar el panel.  
  
 [in] `bDelay`  
 `TRUE`Para retrasar el ajuste del diseño de ficha; de lo contrario, `FALSE`.  
  
 [in] `bActivate`  
 `TRUE`para realizar la pestaña de la pestaña activa; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ficha se muestra o se oculta correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a este método, un panel se muestra o se oculta, dependiendo del valor de la `bShow` parámetro. Si oculta una ficha y es la última ficha visible en la ventana ficha subyacente, se oculta el panel con fichas. Si aparece una ficha cuando anteriormente no había ninguna ficha visible, se muestra el panel con fichas.  
  
##  <a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout  
 Vuelve a calcular la información de diseño para el panel.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el panel está flotando, este método notifica al marco para cambiar el tamaño del panel para el tamaño actual del marco mínima.  
  
 Si el panel está acoplado, este método no hace nada.  
  
##  <a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode  
 Establece el modo de ocultación automática para separables paneles en el panel con fichas.  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMode`  
 `TRUE`Para habilitar el modo de ocultación automática; `FALSE` para habilitar el modo de acoplamiento regular.  
  
 [in] `dwAlignment`  
 Especifica la alineación del panel de ocultación automática que se crea. Para obtener una lista de valores posibles, consulte [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).  
  
 [in] [out]`pCurrAutoHideBar`  
 Puntero a la barra de herramientas de ocultación automática actual. Puede ser `NULL`.  
  
 [in] `bUseTimer`  
 Especifica si utilizar el efecto de ocultar automáticamente cuando el usuario cambia el panel a modo de ocultación automática o para ocultar el panel inmediatamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la barra de herramientas Ocultar automáticamente que se crea para cambiar al modo de ocultación automática, o `NULL` si no se ha creado ninguna barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un usuario elige el botón de anclaje para cambiar el panel con fichas a modo de ocultación automática o al modo normal de acoplamiento.  
  
 Modo de ocultación automática se establece para cada panel intercambiables en el panel con fichas. Se omiten los paneles que no son intercambiables. Para obtener más información, consulte [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).  
  
 Llamar a este método para pasar un panel con fichas al modo de ocultación automática mediante programación. El panel debe acoplarse a la ventana de marco principal ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) debe devolver un puntero válido a la [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)

