---
title: Clase CAutoHideDockSite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::CanAcceptPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::DockPane
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::GetAlignRect
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::RepositionPanes
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetLeft
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::SetOffsetRight
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::UnSetAutoHideMode
- AFXAUTOHIDEDOCKSITE/CAutoHideDockSite::m_nExtraSpace
dev_langs:
- C++
helpviewer_keywords:
- CAutoHideDockSite [MFC], CanAcceptPane
- CAutoHideDockSite [MFC], DockPane
- CAutoHideDockSite [MFC], GetAlignRect
- CAutoHideDockSite [MFC], RepositionPanes
- CAutoHideDockSite [MFC], SetOffsetLeft
- CAutoHideDockSite [MFC], SetOffsetRight
- CAutoHideDockSite [MFC], UnSetAutoHideMode
- CAutoHideDockSite [MFC], m_nExtraSpace
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5778b5be050fec50d30215a8b9cef2ca6e4b6dd4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709688"
---
# <a name="cautohidedocksite-class"></a>Clase CAutoHideDockSite
El `CAutoHideDockSite` amplía la [clase CDockSite](../../mfc/reference/cdocksite-class.md) para implementar paneles de acoplamiento de ocultación automática.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CAutoHideDockSite : public CDockSite  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CAutoHideDockSite::CAutoHideDockSite`|Construye un objeto `CAutoHideDockSite`.|  
|`CAutoHideDockSite::~CAutoHideDockSite`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Indica si el `CAutoHideDockSite` se muestra en el menú del panel.|  
|[CAutoHideDockSite::CanAcceptPane](#canacceptpane)|Determina si un objeto de base de panel se deriva el [clase CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md).|  
|[CAutoHideDockSite::DockPane](#dockpane)|Acopla un panel a este `CAuotHideDockSite` objeto.|  
|[CAutoHideDockSite::GetAlignRect](#getalignrect)|Recupera el tamaño del sitio de acoplamiento en coordenadas de pantalla.|  
|[CAutoHideDockSite::RepositionPanes](#repositionpanes)|Vuelve a dibujar el panel en el `CAutoHideDockSite` con los márgenes globales y el espaciado de botón.|  
|[CAutoHideDockSite::SetOffsetLeft](#setoffsetleft)|Establece el margen en el lado izquierdo de la barra de acoplamiento.|  
|[CAutoHideDockSite::SetOffsetRight](#setoffsetright)|Establece el margen en el lado derecho de la barra de acoplamiento.|  
|[CAutoHideDockSite::UnSetAutoHideMode](#unsetautohidemode)|Las llamadas [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) para los objetos en el `CAutoHideDockSite`.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|nombre|Descripción|  
|[CAutoHideDockSite::m_nExtraSpace](#m_nextraspace)|Define el tamaño del espacio entre las barras de herramientas y el borde de la barra de acoplamiento. Este espacio se mide desde el borde izquierdo o el borde superior, según la alineación para el espacio de acoplamiento.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando se llama a [CFrameWndEx::EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes), el marco crea automáticamente un `CAutoHideDockSite` objeto. En la mayoría de los casos, no debe tener que crear una instancia o utilice esta clase directamente.  
  
 La barra de acoplamiento es la separación entre el lado izquierdo del panel de acoplamiento y el lado izquierdo de la [clase CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar un `CAutoHideDockSite` objeto desde un `CMFCAutoHideBar` objeto y cómo establecer los márgenes izquierdos y derecho de la barra de acoplamiento.  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/cpp/cautohidedocksite-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxautohidedocksite.h  
  
##  <a name="canacceptpane"></a>  CAutoHideDockSite::CanAcceptPane  
 Determina si un panel de base es un [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objeto o derivado de `CMFCAutoHideBar`.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|*pBar*|[in] El panel de base que el marco de prueba.|  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si *pBar* se deriva de `CMFCAutoHideBar`; FALSE en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Si se deriva de un objeto de panel base `CMFCAutoHideBar`, que puede contener un `CAutoHideDockSite`.  
  
##  <a name="dockpane"></a>  CAutoHideDockSite::DockPane  
 Acopla un panel a este [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) objeto.  
  
```  
virtual void DockPane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod,  
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|*conquistado*|[in] El panel que se acopla el marco de trabajo.|  
|*dockMethod*|[in] Opciones para el panel de acoplamiento.|  
|*lpRect*|[in] Un rectángulo que especifica los límites del panel acoplado.|  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no utiliza el parámetro *dockMethod*, que se proporciona para su uso futuro.  
  
 Si *lpRect* es NULL, el marco de trabajo coloca el panel en la ubicación predeterminada en el sitio de vinculación. Si el sitio de vinculación es horizontal, la ubicación predeterminada es a la izquierda el sitio de vinculación. En caso contrario, la ubicación predeterminada es la parte superior del sitio de la vinculación.  
  
##  <a name="getalignrect"></a>  CAutoHideDockSite::GetAlignRect  
 Recupera el tamaño del sitio de acoplamiento en coordenadas de pantalla.  
  
```  
void GetAlignRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|*Rect*|[in] Una referencia a un rectángulo. El método almacena el tamaño del sitio de acoplamiento en este rectángulo.|  
  
### <a name="remarks"></a>Comentarios  
 El rectángulo se ajusta para los márgenes de desplazamiento para que no se incluyen.  
  
##  <a name="m_nextraspace"></a>  CAutoHideDockSite::m_nExtraSpace  
 El tamaño del espacio entre los bordes de la [clase CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) y [clase CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objetos.  
  
```  
static int m_nExtraSpace;  
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando un `CMFCAutoHideBar` se acopla en una `CAutoHideDockSite`, no debe ocupar el sitio de vinculación completa. Esta variable global controla el espacio adicional entre el borde izquierdo o superior de la `CMFCAutoHideBar` y la correspondiente `CAutoHideDockSite` edge. Si se usa el borde superior o izquierdo depende de la alineación actual.  
  
##  <a name="setoffsetleft"></a>  CAutoHideDockSite::SetOffsetLeft  
 Establece el margen en el lado izquierdo de la barra de acoplamiento.  
  
```  
void SetOffsetLeft(int nOffset);
```  
  
### <a name="parameters"></a>Parámetros  
*nOffset*<br/>
[in] El desplazamiento nuevo.  
  
### <a name="remarks"></a>Comentarios  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objetos se colocan de forma estática en el `CAutoHideDockSite` objeto. Esto significa que el usuario no puede cambiar manualmente la ubicación de `CMFCAutoHideBar` objetos. El `SetOffsetLeft` método controla el espaciado entre el lado izquierdo de la más a la izquierda `CMFCAutoHideBar` y el lado izquierdo de la `CAutoHideDockSite`.  
  
##  <a name="setoffsetright"></a>  CAutoHideDockSite::SetOffsetRight  
 Establece el margen en el lado derecho de la barra de acoplamiento.  
  
```  
void SetOffsetRight(int nOffset);
```  
  
### <a name="parameters"></a>Parámetros  
*nOffset*<br/>
[in] El desplazamiento nuevo.  
  
### <a name="remarks"></a>Comentarios  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) objetos se colocan de forma estática en el `CAutoHideDockSite` objeto. Esto significa que el usuario no puede cambiar manualmente la ubicación de la `CMFCAutoHideBar` objetos. El `SetOffsetRight` método controla el espaciado entre el lado derecho de la derecha `CMFCAutoHideBar` y el lado derecho de la `CAutoHideDockSite`.  
  
##  <a name="repositionpanes"></a>  CAutoHideDockSite::RepositionPanes  
 Vuelve a dibujar los paneles en el [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md).  
  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|*rectNewClientArea*|[in] Un valor reservado.|  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no utiliza *rectNewClientArea*. Vuelve a dibujar los paneles con los márgenes de la barra de herramientas global y el espaciado de botón.  
  
##  <a name="unsetautohidemode"></a>  CAutoHideDockSite::UnSetAutoHideMode  
 Las llamadas [CMFCAutoHideBar::UnSetAutoHideMode](../../mfc/reference/cmfcautohidebar-class.md#unsetautohidemode) para los objetos en el sitio de vinculación.  
  
```  
void UnSetAutoHideMode(CMFCAutoHideBar* pAutoHideToolbar);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|*pAutoHideToolbar*|[in] Un puntero a un [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md) panel de objetos que se encuentra en la `CAutoHideDockSite`.|  
  
### <a name="remarks"></a>Comentarios  
 Este método busca en la fila que contiene *pAutoHideToolbar*. Llama a `CMFCAutoHideBar.UnSetAutoHideMode` para todos los `CMFCAutoHideBar` objetos en esa fila. Si *pAutoHideToolbar* no se encuentra o es NULL, este método llama a `CMFCAutoHideBar.UnSetAutoHideMode` para todos los `CMFCAutoHideBar` objetos en el `CAutoHideDockSite`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockSite (clase)](../../mfc/reference/cdocksite-class.md)
