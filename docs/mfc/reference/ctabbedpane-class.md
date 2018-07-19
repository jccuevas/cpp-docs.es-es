---
title: Clase CTabbedPane | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
dev_langs:
- C++
helpviewer_keywords:
- CTabbedPane [MFC], DetachPane
- CTabbedPane [MFC], EnableTabAutoColor
- CTabbedPane [MFC], FloatTab
- CTabbedPane [MFC], GetTabArea
- CTabbedPane [MFC], GetTabWnd
- CTabbedPane [MFC], HasAutoHideMode
- CTabbedPane [MFC], IsTabLocationBottom
- CTabbedPane [MFC], ResetTabs
- CTabbedPane [MFC], SetTabAutoColors
- CTabbedPane [MFC], m_bTabsAlwaysTop
- CTabbedPane [MFC], m_pTabWndRTC
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9da7016e98d9bd84e62c3b05cae32346827142f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121843"
---
# <a name="ctabbedpane-class"></a>Clase CTabbedPane
Implementa la funcionalidad de un panel con pestañas separables.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CTabbedPane : public CBaseTabbedPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CTabbedPane::CTabbedPane`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTabbedPane::DetachPane](#detachpane)|(Invalida [cbasetabbedpane:: Detachpane](../../mfc/reference/cbasetabbedpane-class.md#detachpane).)|  
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|Habilita o deshabilita el coloreado automático de pestañas.|  
|[CTabbedPane::FloatTab](#floattab)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable. (Invalida [cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|  
|[CTabbedPane::GetTabArea](#gettabarea)|Devuelve el tamaño y la posición del área de pestañas de la ventana con pestañas.|  
|[CTabbedPane::GetTabWnd](#gettabwnd)||  
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|Determina si el panel con pestañas se puede cambiar a modo de ocultación automática. (Invalida [cbasetabbedpane:: Hasautohidemode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode).)|  
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|Determina si las pestañas se sitúan en la parte inferior de la ventana.|  
|[CTabbedPane::ResetTabs](#resettabs)|Restablece todos los paneles con pestañas al estado predeterminado.|  
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|Establece una lista de colores personalizados que se pueden usar cuando se habilita la característica de color automático.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|La ubicación predeterminada de las pestañas en la aplicación.|  
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|Información de clase en tiempo de ejecución para un derivado de `CMFCTabCtrl` personalizado.|  
  
## <a name="remarks"></a>Comentarios  
 El marco de trabajo crea automáticamente una instancia de esta clase cuando un usuario adjunta un panel a otro apuntando al título del segundo panel. Todos los paneles con pestañas que se crean mediante el marco de trabajo tienen un identificador de -1.  
  
 Para especificar pestañas normales en lugar de pestañas de tipo Outlook, pase el estilo de AFX_CBRS_REGULAR_TABS el [CDockablePane:: CreateEx](../../mfc/reference/cdockablepane-class.md#createex) método.  
  
 Si crea un panel con pestañas separables, el marco de trabajo puede destruir automáticamente el panel, por lo que no debe almacenar el puntero. Para obtener un puntero al panel con pestañas, llame al método `CBasePane::GetParentTabbedPane`.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, crearemos un objeto `CTabbedPane`. A continuación, usamos [cbasetabbedpane:: addTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) para asociar otras pestañas.  
  
```  
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),  
    TRUE, 
 (UINT) -1,  
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |  
    WS_CLIPCHILDREN | CBRS_LEFT |    
    CBRS_FLOAT_MULTI)) 
{  
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create  
}  
 
pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```  
  
## <a name="example"></a>Ejemplo  
 Otra manera de crear un objeto de barra de control con pestañas es usar [CDockablePane:: Attachtotabwnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd). El `AttachToTabWnd` método crea dinámicamente un objeto de panel con pestañas con información de clase en tiempo de ejecución establecida por [CDockablePane:: Settabbedpanertc](../../mfc/reference/cdockablepane-class.md#settabbedpanertc).  
  
 En este ejemplo se crea dinámicamente un panel con pestañas, se asocian dos pestañas y se convierte la segunda pestaña en no separable.  
  
```  
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;  
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxTabbedPane.h  
  
##  <a name="detachpane"></a>  CTabbedPane::DetachPane  

  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBar*  
 [in] *bHide*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enabletabautocolor"></a>  CTabbedPane::EnableTabAutoColor  
 Habilita o deshabilita el coloreado automático de pestañas.  
  
```  
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHabilitar el*  
 TRUE para habilitar el coloreado automático de pestañas; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método estático para habilitar o deshabilitar el coloreado automático de las fichas en todos los paneles con pestañas de la aplicación. Cuando esta característica está habilitada, cada pestaña se rellena mediante su propio color. Puede encontrar la lista de colores que se usan para las pestañas de color mediante una llamada a la [CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors) método.  
  
 Puede especificar la lista de colores que se usará para las pestañas llamando [CTabbedPane::SetTabAutoColors](#settabautocolors).  
  
 De forma predeterminada, esta opción está deshabilitada.  
  
##  <a name="floattab"></a>  CTabbedPane::FloatTab  

  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBar*  
 [in] *nTabID*  
 [in] *dockMethod*  
 [in] *bHide*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettabarea"></a>  CTabbedPane::GetTabArea  
 Devuelve el tamaño y la posición del área de ficha en la ventana con pestañas.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] *rectTabAreaTop*  
 Contiene el tamaño y posición, en coordenadas de pantalla del área de ficha superior.  
  
 [out] *rectTabAreaBottom*  
 Contiene el tamaño y posición, en coordenadas de pantalla del área de pestañas de la parte inferior.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar cómo acoplar un panel que un usuario está arrastrando. Cuando el usuario arrastra un panel sobre el área de pestañas del panel de destino, el marco de trabajo intenta agregarlo como una nueva pestaña del panel de destino. En caso contrario, intenta acoplar el panel en el lado del panel de destino, que implica la creación de un nuevo contenedor de panel con un divisor que separa los dos paneles.  
  
 Invalide este método en un `CTabbedPane`-clase derivada para cambiar este comportamiento.  
  
##  <a name="gettabwnd"></a>  CTabbedPane::GetTabWnd  

  
```  
CMFCTabCtrl* GetTabWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hasautohidemode"></a>  CTabbedPane::HasAutoHideMode  

  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="istablocationbottom"></a>  CTabbedPane::IsTabLocationBottom  
 Determina si las pestañas se sitúan en la parte inferior de la ventana.  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el área de pestañas se encuentra en la parte inferior de la ventana con pestañas; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_btabsalwaystop"></a>  CTabbedPane::m_bTabsAlwaysTop  
 La ubicación predeterminada de las pestañas en la aplicación.  
  
```  
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer a este miembro estático en True para hacer que todas las fichas de la aplicación que se mostrará en la parte superior del panel con pestañas.  
  
 Debe establecer este valor antes de que se ha creado un panel con fichas.  
  
 El valor predeterminado es FALSE.  
  
##  <a name="m_ptabwndrtc"></a>  CTabbedPane::m_pTabWndRTC  
 Información de clase en tiempo de ejecución para un derivado de `CMFCTabCtrl` personalizado.  
  
```  
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer esta variable de miembro estático en un puntero a la información de clase en tiempo de ejecución de un `CMFCTabCtrl`-objeto derivado si se está usando una ventana con pestañas personalizada dentro de un panel con fichas.  
  
##  <a name="resettabs"></a>  CTabbedPane::ResetTabs  
 Restablece todos los paneles con pestañas al estado predeterminado.  
  
```  
static void ResetTabs();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para revertir todos los paneles con fichas a su estado predeterminado. Cuando se llama, este método restablece los tamaños de borde y el estado del color automática de todos los paneles con pestañas.  
  
##  <a name="settabautocolors"></a>  CTabbedPane::SetTabAutoColors  
 Establece una lista de colores personalizados que se utilizan cuando se habilita la característica de color automático.  
  
```  
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *arColors*  
 Contiene la matriz de colores para establecer.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para personalizar la lista de colores que se utilizan cuando se habilita la característica de color automático. Esto es una función estática y afecta a todas las fichas de la aplicación.  
  
 Use [CTabbedPane::EnableTabAutoColor](#enabletabautocolor) para habilitar o deshabilitar la característica de color automático.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [CBaseTabbedPane (clase)](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBar (clase)](../../mfc/reference/cmfcoutlookbar-class.md)
