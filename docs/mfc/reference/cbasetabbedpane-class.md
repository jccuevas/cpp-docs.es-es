---
title: CBaseTabbedPane (clase) | Documentos de Microsoft
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
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be9752822ee009ceddb735806d36ea3507242951
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane (clase)
Extiende la funcionalidad de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) para permitir la creación de ventanas con pestañas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Cbasetabbedpane:: addTab](#addtab)|Agrega una nueva pestaña a un panel con fichas.|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica si un panel con fichas vacío puede ser destruido.|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Aplica la configuración de ficha, que se carga desde el registro, en un panel con fichas.|  
|[CBaseTabbedPane::CanFloat](#canfloat)|Determina si el panel puede flotar. (Invalida [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina si el título para el panel con fichas debería mostrar el mismo texto como la pestaña activa.|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Invalida [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|  
|[Cbasetabbedpane:: Detachpane](#detachpane)|Convierte uno o más paneles acoplables en documentos MDI con fichas.|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Habilita o deshabilita la posibilidad de panel con pestañas para sincronizar el texto de título con el texto de etiqueta en la pestaña activa.|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Restaura el orden de tabulación interno a un estado predeterminado.|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Devuelve un panel que se encuentra en una ficha cuando la pestaña se identifica mediante un índice de base cero de tabulación.|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Devuelve un panel que se identifica mediante el identificador del panel.|  
|[Cbasetabbedpane:: Floattab](#floattab)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable.|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Devuelve el orden predeterminado de las pestañas en el panel.|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Recupera un puntero a la primera pestaña mostrada.|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|Recupera el mínimo tamaño permitido para el panel. (Invalida [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Devuelve un identificador para el icono del panel. (Invalida [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Devuelve una lista de paneles que se encuentran en el panel con fichas.|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Devuelve los rectángulos delimitadores para las áreas de la pestaña superior e inferior.|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Devuelve el número de fichas de una ventana de la ficha.|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Obtiene la ventana de pestaña (ajustado) subyacente.|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Devuelve el número de fichas mostradas.|  
|[Cbasetabbedpane:: Hasautohidemode](#hasautohidemode)|Determina si el panel con fichas se puede cambiar a modo de ocultación automática.|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Determina si el panel con pestañas se oculta si solo se muestra una pestaña.|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Se usa internamente durante la serialización.|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Recalcula la información de diseño para el panel. (Invalida [CPANE:: RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|  
|[CBaseTabbedPane::RemovePane](#removepane)|Quita un panel desde el panel con pestañas.|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|Se usa internamente durante la serialización.|  
|`CBaseTabbedPane::Serialize`|(Invalida [CDockablePane:: Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6).)|  
|`CBaseTabbedPane::SerializeTabWindow`|Se usa internamente durante la serialización.|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Determina si se destruirán automáticamente la barra de control de pestaña.|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Alterna entre mostrar el panel de acoplamiento y modo de ocultación automática. (Invalida [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|  
|[CBaseTabbedPane::ShowTab](#showtab)|Muestra u oculta una pestaña.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase es una clase abstracta y no se pueden crear instancias. Implementa los servicios que son comunes a todos los tipos de paneles con pestañas.  
  
 Actualmente, la biblioteca incluye dos clases derivadas panel con fichas: [CTabbedPane clase](../../mfc/reference/ctabbedpane-class.md) y [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 A `CBaseTabbedPane` objeto encapsula un puntero a un [clase CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) objeto. [Clase CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) , a continuación, se convierte en una ventana secundaria de panel con pestañas.  
  
 Para obtener más información sobre cómo crear paneles con pestañas, consulte [clase CDockablePane](../../mfc/reference/cdockablepane-class.md), [CTabbedPane clase](../../mfc/reference/ctabbedpane-class.md), y [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md).  
  
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
  
##  <a name="addtab"></a>Cbasetabbedpane:: addTab  
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
 Un puntero al panel para agregar. This (puntero) puede no ser válida después de llamar a este método. Para obtener más información, vea la sección Comentarios.  
  
 [in] `bVisible`  
 `TRUE`Para hacer que la pestaña visible; en caso contrario, `FALSE`.  
  
 [in] `bSetActive`  
 `TRUE`para realizar la pestaña de la pestaña activa; en caso contrario, `FALSE`.  
  
 [in] `bDetachable`  
 `TRUE`Para hacer que la pestaña desmontable; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se ha agregado correctamente como una pestaña y no se destruye en el proceso. `FALSE`Si el panel que se va a agregar es un objeto de tipo `CBaseTabbedPane`. Para obtener más información, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para agregar un panel como una nueva pestaña en un panel con fichas. Si `pNewBar` apunta a un objeto de tipo `CBaseTabbedPane`, se copian todas sus pestañas en el panel con fichas y, a continuación, `pNewBar` se destruye. Por lo tanto, `pNewBar` se convierte en un puntero no válido y no debe usarse.  
  
##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 Especifica si un panel con fichas vacío puede ser destruido.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si un panel con fichas vacío se puedan destruir; en caso contrario, `FALSE`. La implementación predeterminada siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Si un panel con fichas vacío no puede ser destruidos, el marco de trabajo oculta el panel en su lugar.  
  
##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo  
 Carga la configuración de las tabulaciones desde el registro y los aplica a un panel con fichas.  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bUseTabIndexes`  
 Este parámetro se utiliza internamente por el marco de trabajo.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando vuelve a cargar la información de estado de acoplamiento del registro. El método obtiene información sobre el orden de tabulación y nombres de las pestañas de un panel con fichas.  
  
##  <a name="canfloat"></a>CBaseTabbedPane::CanFloat  
 Especifica si el panel con fichas puede flotar.  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel puede flotar; en caso contrario, `FALSE`.  
  
##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName  
 Determina si el título para el panel con fichas debería mostrar el mismo texto como la pestaña activa.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establece el texto del título del panel con pestañas en el texto de la pestaña activa; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El método se utiliza para determinar si el texto muestra en los duplicados de título de panel con fichas la etiqueta de la pestaña activa. Puede habilitar o deshabilitar esta funcionalidad mediante una llamada a [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).  
  
##  <a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument  
 Convierte uno o más paneles acoplables en documentos MDI con fichas.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActiveTabOnly`  
 Al convertir un panel con fichas, especifique `TRUE` para convertir sólo la pestaña activa. Especificar `FALSE` para convertir todas las fichas en el panel.  
  
##  <a name="detachpane"></a>Cbasetabbedpane:: Detachpane  
 Desasocia un panel desde el panel con pestañas.  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Puntero al panel para separar.  
  
 [in] `bHide`  
 Parámetro booleano que especifica si el marco de trabajo oculta el panel después de que ésta se separa.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de trabajo correctamente separa el panel; `FALSE` si `pBar` es `NULL` o hace referencia a un panel que no está en el panel con fichas.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo queda flotando el panel desasociado si es posible. Para obtener más información, consulte [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).  
  
##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName  
 Habilita o deshabilita la posibilidad de panel con pestañas para sincronizar el texto de título con el texto de etiqueta en la pestaña activa.  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`para sincronizar el título del panel con fichas con el título de la pestaña activa; en caso contrario, `FALSE`.  
  
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
 Un puntero al panel si se encuentra; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Este método compara todas las fichas en el panel y devuelve el marcado con el identificador especificado por el `uBarID` parámetro.  
  
##  <a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber  
 Devuelve un panel que se encuentra en una pestaña.  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTabNum`  
 Especifica el índice de base cero de la pestaña para recuperar.  
  
 [in] `bGetWrappedBar`  
 `TRUE`para devolver la ventana subyacente (ajustada) del panel en lugar del panel sí; en caso contrario, `FALSE`. Esto solo se aplica a los paneles que se deriva de [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Si no se encuentra el panel, se devuelve un puntero válido para el panel que se va a buscar; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para recuperar el panel que residen en la pestaña especificada por el `nTabNum` parámetro.  
  
##  <a name="floattab"></a>Cbasetabbedpane:: Floattab  
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
 Un puntero al panel a float.  
  
 [in] `nTabID`  
 Especifica el índice de base cero de la pestaña para float.  
  
 [in] `dockMethod`  
 Especifica el método que utilice para hacer flotar el panel. Para obtener más información, vea la sección Comentarios.  
  
 [in] `bHide`  
 `TRUE`Para ocultar el panel antes flotante; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel flota; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para convertir en flotante un panel que se encuentra actualmente en una pestaña desmontable.  
  
 Si desea desasociar un panel mediante programación, especifique `DM_SHOW` para el `dockMethod` parámetro. Si desea hacer flotar el panel en la misma posición que flota anteriormente, especifique `DM_DBL_CLICK` como el `dockMethod` parámetro.  
  
##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder  
 Devuelve el orden predeterminado de las pestañas en el panel.  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CArray` objeto que especifica el orden predeterminado de las pestañas en el panel.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se restablece una barra de Outlook en un estado inicial.  
  
##  <a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab  
 Recupera un puntero a la primera pestaña mostrada.  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTabNum`  
 Una referencia a un entero. Este método escribe el índice de base cero de la primera pestaña mostrado para este parámetro, o -1 si no se muestran se encuentra la ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un puntero a la primera pestaña mostrado; en caso contrario, `NULL`.  
  
##  <a name="getminsize"></a>CBaseTabbedPane::GetMinSize  
 Recupera el mínimo tamaño permitido para el panel.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `size`  
 Un `CSize` objeto que se rellena con el mínimo tamaño permitido.  
  
### <a name="remarks"></a>Comentarios  
 Si el tratamiento coherente de los tamaños mínimo del panel está activo ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` se rellena con el mínimo tamaño permitido para la pestaña activa. En caso contrario, `size` se rellena con el valor devuelto de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon  
 Recupera el mínimo tamaño permitido para el panel.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `size`  
 Un `CSize` objeto que se rellena con el mínimo tamaño permitido.  
  
### <a name="remarks"></a>Comentarios  
 Si el tratamiento coherente de los tamaños mínimo del panel está activo ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` se rellena con el mínimo tamaño permitido para la pestaña activa. En caso contrario, `size` se rellena con el valor devuelto de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpanelist"></a>CBaseTabbedPane::GetPaneList  
 Devuelve una lista de paneles que se encuentran en el panel con fichas.  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `lst`  
 Un `CObList` que se rellena con los paneles que se encuentran en el panel con fichas.  
  
 [in] `pRTCFilter`  
 Si no lo es `NULL`, la lista devuelta contiene solo los paneles que pertenecen a la clase en tiempo de ejecución especificado.  
  
##  <a name="gettabarea"></a>CBaseTabbedPane::GetTabArea  
 Devuelve los rectángulos delimitadores para las áreas de la pestaña superior e inferior.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectTabAreaTop`  
 Recibe las coordenadas de pantalla del área de ficha superior.  
  
 [out] `rectTabAreaBottom`  
 Recibe las coordenadas de pantalla de la parte inferior de la pestaña.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para determinar los rectángulos delimitadores, en coordenadas de pantalla, para las áreas de la pestaña superior e inferior.  
  
##  <a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum  
 Devuelve el número de fichas de una ventana de la ficha.  
  
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
 Un puntero a la ventana de la ficha subyacente.  
  
##  <a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum  
 Devuelve el número de pestañas visibles.  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de pestañas visibles, que será mayor que o igual a cero.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para determinar el número de pestañas visibles en el panel con fichas.  
  
##  <a name="hasautohidemode"></a>Cbasetabbedpane:: Hasautohidemode  
 Determina si el panel con pestañas se puede cambiar a modo de ocultación automática.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede cambiar a modo de ocultación automática; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si el modo de ocultación automática está deshabilitado, ningún botón de pin se muestra en el título del panel con fichas.  
  
##  <a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab  
 Determina si el panel con pestañas se oculta si solo se muestra una pestaña.  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si no se muestra la ventana de la ficha cuando hay solo una sola pestaña visible; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si no se muestra el panel porque sólo una ficha está abierta, puede llamar a este método para determinar si el panel con pestañas está funcionando correctamente.  
  
##  <a name="removepane"></a>CBaseTabbedPane::RemovePane  
 Quita un panel desde el panel con pestañas.  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pBar`  
 Un puntero al panel para quitar del panel con pestañas.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se ha quitado correctamente desde el panel con pestañas y el panel con fichas sigue siendo válido. `FALSE`Si se ha quitado el último panel desde el panel con pestañas y el panel con pestañas está a punto de ser destruidos. Si el valor devuelto es `FALSE`, no use el panel con fichas más.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para quitar el panel especificado por el `pBar` parámetro desde el panel con pestañas.  
  
##  <a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy  
 Determina si se destruirán automáticamente la barra de control de pestaña.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAutoDestroy`  
 `TRUE`Si el panel con fichas se creó dinámicamente y no se controlan su duración; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Establecer el modo de destruir automáticamente `TRUE` si crea dinámicamente un panel con fichas y si no se controla su duración. Si destruir automáticamente el modo es `TRUE`, el panel con fichas se destruirán automáticamente por el marco de trabajo.  
  
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
 `TRUE`Para retrasar el ajuste del diseño de pestaña; en caso contrario, `FALSE`.  
  
 [in] `bActivate`  
 `TRUE`para realizar la pestaña de la pestaña activa; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ficha se muestra o se oculta correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a este método, un panel se muestra o se ocultan, según el valor de la `bShow` parámetro. Si ocultar una pestaña y es la última ficha visible en la ventana de la ficha subyacente, se oculta el panel con fichas. Si aparece una ficha cuando anteriormente no había ningún pestañas visible, se muestra el panel con fichas.  
  
##  <a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout  
 Recalcula la información de diseño para el panel.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Si el panel está flotando, este método notifica el marco de trabajo para cambiar el tamaño del panel para el tamaño actual de marco reducido.  
  
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
 `TRUE`Para habilitar el modo de ocultación automática; `FALSE` para habilitar el modo de acoplamiento normal.  
  
 [in] `dwAlignment`  
 Especifica la alineación del panel de ocultación automática que va a crearse. Para obtener una lista de valores posibles, consulte [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).  
  
 [in] [out]`pCurrAutoHideBar`  
 Un puntero a la barra de herramientas de ocultación automática actual. Puede ser `NULL`.  
  
 [in] `bUseTimer`  
 Especifica si desea utilizar el efecto de ocultación automática cuando el usuario cambia el panel a modo de ocultación automática, o para ocultar el panel inmediatamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la barra de herramientas de ocultación automática que se crea cuando se cambia al modo de ocultación automática, o `NULL` si no se ha creado ninguna barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando un usuario elige el botón de anclaje para alternar el panel con fichas a modo de ocultación automática o a modo de acoplamiento normal.  
  
 Modo de ocultación automática está establecido para cada panel en el panel con pestañas separables. Se omiten los paneles que son no se puede desasociar. Para obtener más información, consulte [cmfcbasetabctrl:: Enabletabdetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).  
  
 Llamar a este método para cambiar un panel con fichas a modo de ocultación automática mediante programación. Se debe acoplar el panel a la ventana de marco principal ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) debe devolver un puntero válido a la [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockablePane (clase)](../../mfc/reference/cdockablepane-class.md)
