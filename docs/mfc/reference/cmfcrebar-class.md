---
title: Clase CMFCReBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCReBar
- AFXREBAR/CMFCReBar
- AFXREBAR/CMFCReBar::AddBar
- AFXREBAR/CMFCReBar::CalcFixedLayout
- AFXREBAR/CMFCReBar::CanFloat
- AFXREBAR/CMFCReBar::Create
- AFXREBAR/CMFCReBar::EnableDocking
- AFXREBAR/CMFCReBar::GetReBarBandInfoSize
- AFXREBAR/CMFCReBar::GetReBarCtrl
- AFXREBAR/CMFCReBar::OnShowControlBarMenu
- AFXREBAR/CMFCReBar::OnToolHitTest
- AFXREBAR/CMFCReBar::OnUpdateCmdUI
- AFXREBAR/CMFCReBar::SetPaneAlignment
dev_langs: C++
helpviewer_keywords:
- CMFCReBar [MFC], AddBar
- CMFCReBar [MFC], CalcFixedLayout
- CMFCReBar [MFC], CanFloat
- CMFCReBar [MFC], Create
- CMFCReBar [MFC], EnableDocking
- CMFCReBar [MFC], GetReBarBandInfoSize
- CMFCReBar [MFC], GetReBarCtrl
- CMFCReBar [MFC], OnShowControlBarMenu
- CMFCReBar [MFC], OnToolHitTest
- CMFCReBar [MFC], OnUpdateCmdUI
- CMFCReBar [MFC], SetPaneAlignment
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 118c792b1b732fa1e8b024bb6b80da5ea0e7aa31
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcrebar-class"></a>Clase CMFCReBar
Un `CMFCReBar` objeto es una barra de controles que proporciona información de diseño, persistencia y estado para controles rebar.  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCReBar : public CPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCReBar::AddBar](#addbar)|Agrega una banda a un control rebar.|  
|[CMFCReBar::CalcFixedLayout](#calcfixedlayout)|(Invalida [cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCReBar::CanFloat](#canfloat)|(Invalida [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CMFCReBar::Create](#create)|Crea el control rebar y lo adjunta a la `CMFCReBar` objeto.|  
|[CMFCReBar::EnableDocking](#enabledocking)|(Invalida [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking).)|  
|[CMFCReBar::GetReBarBandInfoSize](#getrebarbandinfosize)||  
|[CMFCReBar::GetReBarCtrl](#getrebarctrl)|Proporciona acceso directo a subyacente [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) control común.|  
|[CMFCReBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|(Invalida [CPANE:: Onshowcontrolbarmenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCReBar::OnToolHitTest](#ontoolhittest)|(Invalida [CWnd::OnToolHitTest](../../mfc/reference/cwnd-class.md#ontoolhittest).)|  
|[CMFCReBar::OnUpdateCmdUI](#onupdatecmdui)|(Invalida [CBasePane::OnUpdateCmdUI](http://msdn.microsoft.com/en-us/e139f06a-9793-4ee2-bc3d-517389368c77).)|  
|[CMFCReBar::SetPaneAlignment](#setpanealignment)|(Invalida [CBasePane::SetPaneAlignment](../../mfc/reference/cbasepane-class.md#setpanealignment).)|  
  
## <a name="remarks"></a>Comentarios  
 Un `CMFCReBar` objeto puede contener una variedad de las ventanas secundarias. Esto incluye cuadros de edición, barras de herramientas y cuadros de lista. Puede cambiar el tamaño del rebar mediante programación, o el usuario puede cambiar manualmente el tamaño del rebar arrastrando su barra de sujeción. También puede establecer el fondo de un objeto rebar en un mapa de bits de su elección.  
  
 Un objeto rebar se comporta de forma similar a un objeto de barra de herramientas. Un control rebar puede contener una o más bandas, y cada banda puede contener una barra de controles, un mapa de bits, una etiqueta de texto y una ventana secundaria.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCReBar` clase. En el ejemplo se muestra cómo crear un control rebar y agregar una banda a él. Las funciones de banda como una barra de herramientas interno. Este fragmento de código forma parte de la [ejemplo de prueba de Rebar](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/cpp/cmfcrebar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRebar.h  
  
##  <a name="addbar"></a>CMFCReBar::AddBar  
 Agrega una banda a un control rebar.  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pBar`  
 Un puntero a la ventana secundaria que se va a insertar en el control rebar. El objeto que se hace referencia debe tener la **WS_CHILD** estilo de ventana.  
  
 [in] `pszText`  
 Especifica el texto que aparece en el control rebar. El texto no forma parte de la ventana secundaria. En su lugar, se muestra en el control rebar propio.  
  
 [in] [out]`pbmp`  
 Especifica el mapa de bits que se mostrará en el fondo del control rebar.  
  
 [in] `dwStyle`  
 Contiene el estilo que se va a aplicar a la banda. Para obtener una lista completa de los estilos de banda, vea la descripción de `fStyle` en el [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) estructura en la documentación del SDK de Windows.  
  
 [in] `clrFore`  
 Representa el color de primer plano del rebar.  
  
 [in] `clrBack`  
 Representa el color de fondo del rebar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la banda se agregó correctamente a rebar; en caso contrario, `FALSE`.  
  
##  <a name="create"></a>CMFCReBar::Create  
 Crea el control rebar y lo adjunta a la [CMFCReBar](../../mfc/reference/cmfcrebar-class.md) objeto.  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pParentWnd`  
 Un puntero a la ventana primaria de este control rebar.  
  
 [in] `dwCtrlStyle`  
 Especifica el estilo del control rebar. El valor de estilo predeterminado es **RBS_BANDBORDERS**, que muestra restringir líneas para separar las bandas adyacentes en el control rebar. Para obtener una lista de estilos válidos, consulte [estilos de Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774377) en la documentación del SDK de Windows.  
  
 [in] `dwStyle`  
 El estilo de ventana del control rebar. Para obtener una lista de estilos válidos, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] `nID`  
 Identificador de ventana secundaria. del rebar  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control rebar se creó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrebarctrl"></a>CMFCReBar::GetReBarCtrl  
 Proporciona acceso directo a `CReBarCtrl` control común subyacente para `CMFCReBar` objetos.  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a subyacente `CReBarCtrl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para aprovechar las ventajas de la funcionalidad de control común de Windows rebar al personalizar el control rebar.  
  
##  <a name="calcfixedlayout"></a>CMFCReBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="canfloat"></a>CMFCReBar::CanFloat  

  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enabledocking"></a>CMFCReBar::EnableDocking  

  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwDockStyle`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrebarbandinfosize"></a>CMFCReBar::GetReBarBandInfoSize  

  
```  
UINT GetReBarBandInfoSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onshowcontrolbarmenu"></a>CMFCReBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CPoint`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ontoolhittest"></a>CMFCReBar::OnToolHitTest  

  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 [in] `pTI`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onupdatecmdui"></a>CMFCReBar::OnUpdateCmdUI  

  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTarget`  
 [in] `bDisableIfNoHndler`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpanealignment"></a>CMFCReBar::SetPaneAlignment  

  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwAlignment`  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CReBarCtrl (clase)](../../mfc/reference/crebarctrl-class.md)   
 [CPane (clase)](../../mfc/reference/cpane-class.md)
