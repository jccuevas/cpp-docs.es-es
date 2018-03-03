---
title: Clase CMFCColorPopupMenu | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CMFCColorPopupMenu
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::CreateTearOffBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::GetMenuBar
- AFXCOLORPOPUPMENU/CMFCColorPopupMenu::SetPropList
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorPopupMenu [MFC], CMFCColorPopupMenu
- CMFCColorPopupMenu [MFC], CreateTearOffBar
- CMFCColorPopupMenu [MFC], GetMenuBar
- CMFCColorPopupMenu [MFC], SetPropList
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f91c8a6929ada133b3c2ab9f6fc26e9477a88d6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccolorpopupmenu-class"></a>Clase CMFCColorPopupMenu
Representa un menú emergente que los usuarios usan para seleccionar los colores en un documento o aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](#cmfccolorpopupmenu)|Construye un objeto `CMFCColorPopupMenu`.|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCColorPopupMenu::CreateTearOffBar](#createtearoffbar)|Crea una barra de colores acoplable desplazable. (Invalida [CMFCPopupMenu::CreateTearOffBar](../../mfc/reference/cmfcpopupmenu-class.md#createtearoffbar).)|  
|[CMFCColorPopupMenu::GetMenuBar](#getmenubar)|Devuelve el [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) que está incrustado en el menú emergente. (Invalida [CMFCPopupMenu::GetMenuBar](../../mfc/reference/cmfcpopupmenu-class.md#getmenubar).)|  
|`CMFCColorPopupMenu::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCColorPopupMenu::SetPropList](#setproplist)|Establece el objeto de control de cuadrícula de propiedad de los datos incrustados `CMFCColorBar` objeto.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|nombre|Descripción|  
|`m_bEnabledInCustomizeMode`|Un valor booleano que determina si se debe mostrar la barra de colores.|  
|`m_wndColorBar`|La `CMFCColorBar` objeto que proporciona la selección de color.|  
  
### <a name="remarks"></a>Comentarios  
 Esta clase hereda la funcionalidad del menú emergente de la `CMFCPopupMenu` clase y administra un `CMFCColorBar` objeto que proporciona la selección de color. Cuando el marco de trabajo de la barra de herramientas está en modo de personalización y `m_bEnabledInCustomizeMode` miembro está establecido en `FALSE`, no se muestra el objeto de barra de colores. Para obtener más información acerca del modo de personalización, consulte [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)  
  
 Para obtener más información acerca de `CMFCColorBar`, consulte [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcolorpopupmenu.h  
  
##  <a name="cmfccolorpopupmenu"></a>CMFCColorPopupMenu::CMFCColorPopupMenu  
 Construye un objeto `CMFCColorPopupMenu`.  
  
```  
CMFCColorPopupMenu(
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    int nHorzDockRows,  
    int nVertDockColumns,  
    COLORREF colorAutomatic,  
    UINT uiCommandID,  
    BOOL bStdColorDlg = FALSE);

 
CMFCColorPopupMenu(
    CMFCColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic);

 
CMFCColorPopupMenu(
    CMFCRibbonColorButton* pParentBtn,  
    const CArray<COLORREF, COLORREF>& colors,  
    COLORREF color,  
    LPCTSTR lpszAutoColor,  
    LPCTSTR lpszOtherColor,  
    LPCTSTR lpszDocColors, CList<COLORREF, COLORREF>& lstDocColors,  
    int nColumns,  
    COLORREF colorAutomatic,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `colors`  
 Una matriz de colores que el marco de trabajo se muestra en el menú emergente.  
  
 [in] `color`  
 El color seleccionado de forma predeterminada.  
  
 [in] `lpszAutoColor`  
 La etiqueta de texto de la *automática* botón de color (valor predeterminado), o `NULL`.  
  
 La etiqueta para el botón automático estándar es **automática**.  
  
 [in] `lpszOtherColor`  
 La etiqueta de texto de la *otros* botón, que se presenta más opciones de color, o `NULL`.  
  
 La etiqueta estándar para el otro botón es **más colores...** .  
  
 [in] `lpszDocColors`  
 La etiqueta de texto del botón de colores del documento. La paleta de colores del documento enumera todos los colores que utiliza actualmente el documento.  
  
 [in] `lstDocColors`  
 Una lista de colores que usa actualmente el documento.  
  
 [in] `nColumns`  
 El número de columnas que tiene la matriz de colores.  
  
 [in] `nHorzDockRows`  
 El número de filas que tiene la barra de color cuando está acoplado horizontalmente.  
  
 [in] `nVertDockColumns`  
 El número de columnas que tiene la barra de color cuando se acopla verticalmente.  
  
 [in] `colorAutomatic`  
 El color predeterminado que se aplica el marco de trabajo al hacer clic en el botón automático.  
  
 [in] `uiCommandID`  
 Identificador de comando de control de barra de colores.  
  
 [in] `bStdColorDlg`  
 Un valor booleano que indica si se debe mostrar el cuadro de diálogo de color estándar del sistema o el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo.  
  
 [in] `pParentBtn`  
 Un puntero a un botón primario.  
  
 [in] `nID`  
 Identificador del comando.  
  
### <a name="remarks"></a>Comentarios  
 Cada sobrecarga de constructor establece la `m_bEnabledInCustomizeMode` miembro `FALSE`.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un `CMFCColorPopupMenu` objeto.  
  
 [!code-cpp[NVC_MFC_RibbonApp#34](../../mfc/reference/codesnippet/cpp/cmfccolorpopupmenu-class_1.cpp)]  
  
##  <a name="createtearoffbar"></a>CMFCColorPopupMenu::CreateTearOffBar  
 Crea una barra de colores acoplable desplazable.  
  
```  
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,  
    UINT uiID,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pWndMain`|Puntero a la ventana primaria de la barra desplazable.|  
|[in] `uiID`|El identificador de comando de la barra desplazable.|  
|[in] `lpszName`|El texto de la ventana de la barra desplazable.|  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al nuevo objeto de barra de control desplazable.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) objeto y lo convierte a un [clase CPane](../../mfc/reference/cpane-class.md) puntero. Puede convertir este valor a un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) puntero mediante una de las macros de conversión que se describe en [tipo de conversión de objetos de clase MFC](../../mfc/reference/type-casting-of-mfc-class-objects.md).  
  
##  <a name="getmenubar"></a>CMFCColorPopupMenu::GetMenuBar  
 Devuelve el [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) que está incrustado en el menú emergente.  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a los datos incrustados `CMFCPopupMenuBar`.  
  
### <a name="remarks"></a>Comentarios  
 El menú emergente color tiene incrustada [CMFCPopupMenuBar (clase)](../../mfc/reference/cmfcpopupmenubar-class.md) objeto. Invalide este método en una clase derivada si la aplicación utiliza un tipo incrustado diferente.  
  
##  <a name="setproplist"></a>CMFCColorPopupMenu::SetPropList  
 Establece el objeto de control de cuadrícula de propiedad de los datos incrustados `CMFCColorBar` objeto.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndList`  
 Puntero a un objeto de control de cuadrícula de propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
