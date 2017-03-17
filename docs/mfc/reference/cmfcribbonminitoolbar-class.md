---
title: Clase CMFCRibbonMiniToolBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsContextMenuMode
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::SetCommands
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::Show
- AFXRIBBONMINITOOLBAR/CMFCRibbonMiniToolBar::ShowWithContextMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonMiniToolBar class
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
caps.latest.revision: 24
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
ms.openlocfilehash: 7c69880578c0aba88a8463112f4d1e05f6032497
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonminitoolbar-class"></a>Clase CMFCRibbonMiniToolBar
Implementa una barra de herramientas emergente contextual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Constructor predeterminado.|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonMiniToolBar::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCRibbonMiniToolBar::IsContextMenuMode](#iscontextmenumode)||  
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](#isribbonminitoolbar)|(Invalida `CMFCPopupMenu::IsRibbonMiniToolBar`).|  
|[CMFCRibbonMiniToolBar::SetCommands](#setcommands)|Establece la lista de comandos que se mostrarán en la barra de herramientas.|  
|[CMFCRibbonMiniToolBar::Show](#show)|Muestra la minibarra de herramientas en las coordenadas de pantalla especificadas.|  
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](#showwithcontextmenu)|Muestra la minibarra de herramientas junto con un menú contextual.|  
  
## <a name="remarks"></a>Comentarios  
 La minibarra de herramientas se muestra normalmente cuando el usuario selecciona un objeto en un documento. Por ejemplo, cuando el usuario selecciona un bloque de texto en un procesador de textos, la aplicación muestra una minibarra de herramientas que contiene los comandos de formato de texto.  
  
 La minibarra de herramientas se hace transparente cuando el puntero del mouse está fuera de los límites de la minibarra.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 `CMFCRibbonPanelMenu`  
  
 [CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxRibbonMiniToolBar.h  
  
##  <a name="setcommands"></a>CMFCRibbonMiniToolBar::SetCommands  
 Establece la lista de comandos que se mostrarán en la barra de herramientas.  
  
```  
void SetCommands(
    CMFCRibbonBar* pRibbonBar,  
    const CList<UINT,UINT>& lstCommands);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRibbonBar`  
 La barra de cinta que se busca en los botones Mostrar la minibarra de herramientas.  
  
 [in] `lstCommands`  
 La lista de comandos que se mostrará en la minibarra de herramientas. Todas las categorías de la cinta de opciones se van a buscar los botones asociados.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para establecer la lista de comandos que se mostrará en la minibarra de herramientas.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetCommands` método de la `CMFCRibbonMiniToolBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de Microsoft Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo&#9;](../../mfc/reference/codesnippet/cpp/cmfcribbonminitoolbar-class_1.cpp)]  
  
##  <a name="show"></a>CMFCRibbonMiniToolBar::Show  
 Muestra la minibarra de herramientas en las coordenadas de pantalla especificadas.  
  
```  
BOOL Show(
    int x,  
    int y);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `x`  
 Especifica la posición horizontal de la minibarra de herramientas en coordenadas de pantalla.  
  
 [in] `y`  
 Especifica la posición vertical de la minibarra de herramientas en coordenadas de pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la minibarra de herramientas se mostró correctamente; de lo contrario, `FALSE`.  
  
##  <a name="showwithcontextmenu"></a>CMFCRibbonMiniToolBar::ShowWithContextMenu  
 Muestra la minibarra de herramientas junto con un menú contextual.  
  
```  
BOOL ShowWithContextMenu(
    int x,  
    int y,  
    UINT uiMenuResID,  
    CWnd* pWndOwner);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `x`  
 Especifica la posición horizontal del menú contextual en coordenadas de pantalla.  
  
 [in] `y`  
 Especifica la posición vertical del menú contextual en coordenadas de pantalla.  
  
 [in] `uiMenuResID`  
 Especifica el identificador de recurso del menú contextual para mostrar.  
  
 [in] `pWndOwner`  
 Identifica la ventana que recibe los mensajes en el menú contextual.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el menú contextual se mostró correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para mostrar una minibarra de herramientas que tiene un menú contextual. El menú contextual es 15 píxeles situados debajo de la minibarra de herramientas.  
  
##  <a name="iscontextmenumode"></a>CMFCRibbonMiniToolBar::IsContextMenuMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsContextMenuMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isribbonminitoolbar"></a>CMFCRibbonMiniToolBar::IsRibbonMiniToolBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsRibbonMiniToolBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

