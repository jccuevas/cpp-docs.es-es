---
title: Clase CMFCDropDownFrame | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::Create
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentMenuBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::GetParentPopupMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::RecalcLayout
- AFXDROPDOWNTOOLBAR/CMFCDropDownFrame::SetAutoDestroy
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownFrame [MFC], Create
- CMFCDropDownFrame [MFC], GetParentMenuBar
- CMFCDropDownFrame [MFC], GetParentPopupMenu
- CMFCDropDownFrame [MFC], RecalcLayout
- CMFCDropDownFrame [MFC], SetAutoDestroy
ms.assetid: 09ff81a9-de00-43ec-9df9-b626f7728c4b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01b3e5b56621d7bf8d42aad12e216208338bbacd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdropdownframe-class"></a>Clase CMFCDropDownFrame
Proporciona funcionalidad de la ventana de marco de la lista desplegable para las barras de herramientas de la lista desplegable y botones de barra de herramientas de lista desplegable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCDropDownFrame : public CMiniFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CMFCDropDownFrame::CMFCDropDownFrame`|Constructor predeterminado.|  
|`CMFCDropDownFrame::~CMFCDropDownFrame`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCDropDownFrame::Create](#create)|Crea un objeto `CMFCDropDownFrame`.|  
|`CMFCDropDownFrame::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCDropDownFrame::GetParentMenuBar](#getparentmenubar)|Recupera la barra de menús principal del marco de lista desplegable.|  
|[CMFCDropDownFrame::GetParentPopupMenu](#getparentpopupmenu)|Recupera el menú emergente principal del marco de lista desplegable.|  
|`CMFCDropDownFrame::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCDropDownFrame::RecalcLayout](#recalclayout)|Cambia de posición el marco de la lista desplegable.|  
|[CMFCDropDownFrame::SetAutoDestroy](#setautodestroy)|Establece si la ventana de la barra de herramientas desplegable secundaria se destruye automáticamente.|  
  
### <a name="remarks"></a>Comentarios  
 Esta clase no está diseñada para utilizarse directamente desde el código.  
  
 El marco de trabajo utiliza esta clase para proporcionar un comportamiento de marco a la `CMFCDropDownToolbar` y `CMFCDropDownToolbarButton` clases. Para obtener más información sobre estas clases, consulte [CMFCDropDownToolBar clase](../../mfc/reference/cmfcdropdowntoolbar-class.md) y [CMFCDropDownToolbarButton clase](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar un puntero a un `CMFCDropDownFrame` objeto desde un `CFrameWnd` clase y cómo establecer el elemento secundario de ventana de la barra de herramientas de lista desplegable para se destruyen automáticamente.  
  
 [!code-cpp[NVC_MFC_RibbonApp#36](../../mfc/reference/codesnippet/cpp/cmfcdropdownframe-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCDropDownFrame](../../mfc/reference/cmfcdropdownframe-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdropdowntoolbar.h  
  
##  <a name="create"></a>CMFCDropDownFrame::Create  
 Crea un objeto `CMFCDropDownFrame`.  
  
```  
virtual BOOL Create(
    CWnd* pWndParent,  
    int x,  
    int y,  
    CMFCDropDownToolBar* pWndOriginToolbar);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pWndParent`|La ventana principal del marco de lista desplegable.|  
|[in] `x`|La coordenada horizontal de pantalla para la ubicación del marco desplegable.|  
|[in] `y`|La coordenada vertical de pantalla para la ubicación del marco desplegable.|  
|[in] `pWndOriginToolbar`|La barra de herramientas que incluye los botones de lista desplegable que utiliza este método para rellenar el nuevo objeto de marco de la lista desplegable.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de la lista desplegable se creó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a la base de [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) método para crear la ventana de marco de la lista desplegable con los `WS_POPUP` estilo. Aparecerá la ventana de marco de la lista desplegable en las coordenadas de pantalla especificadas. Este método produce un error si la [CMiniFrameWnd::CreateEx](../../mfc/reference/cminiframewnd-class.md#createex) método `FALSE`.  
  
 El `CMFCDropDownFrame` clase crea una copia de proporcionado `CMFCDropDownToolBar` parámetro. Este método copia las imágenes de botón y los Estados de los botones de la `pWndOriginToolbar` parámetro para el `m_pWndOriginToolbar` miembro de datos.  
  
##  <a name="getparentmenubar"></a>CMFCDropDownFrame::GetParentMenuBar  
 Recupera la barra de menús principal del marco de lista desplegable.  
  
```  
CMFCMenuBar* GetParentMenuBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la barra de menús principal del marco de lista desplegable, o `NULL` si el marco no tiene ningún elemento primario.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera la barra de menús principal en el botón primario. Este método devuelve `NULL` si el marco de la lista desplegable no tiene ningún botón primario o el botón primario no tiene ninguna barra de menús principal.  
  
##  <a name="getparentpopupmenu"></a>CMFCDropDownFrame::GetParentPopupMenu  
 Recupera el menú emergente principal del marco de lista desplegable.  
  
```  
CMFCDropDownFrame* GetParentPopupMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al menú desplegable elemento primario del marco de lista desplegable, o `NULL` si el marco no tiene ningún elemento primario.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera del menú primario en el botón primario. Este método devuelve `NULL` si el marco de la lista desplegable no tiene ningún botón primario o el botón primario no tiene ningún menú primario.  
  
##  <a name="recalclayout"></a>CMFCDropDownFrame::RecalcLayout  
 Cambia de posición el marco de la lista desplegable.  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `bNotify`|Sin usar.|  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se crea el marco de la lista desplegable o se cambia el tamaño de la ventana primaria. Este método calcula la posición y el tamaño del marco de lista desplegable mediante el uso de la posición y el tamaño de la ventana primaria.  
  
##  <a name="setautodestroy"></a>CMFCDropDownFrame::SetAutoDestroy  
 Establece si la ventana de la barra de herramientas desplegable secundaria se destruye automáticamente.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAutoDestroy`  
 `TRUE`para destruir automáticamente la ventana de la barra de herramientas de lista desplegable asociada; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si `bAutoDestroy` es `TRUE`, la `CMFCDropDownFrame` destructor destruye la ventana de la barra de herramientas de lista desplegable asociada. El valor predeterminado es `TRUE`.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase de CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCDropDownToolbarButton (clase)](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)
