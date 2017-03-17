---
title: Clase CMDITabInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo
- AFXMDICLIENTAREAWND/CMDITabInfo::Serialize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bAutoColor
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bDocumentMenu
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bEnableTabSwap
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bFlatFrame
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCloseButton
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabCustomTooltips
- AFXMDICLIENTAREAWND/CMDITabInfo::m_bTabIcons
- AFXMDICLIENTAREAWND/CMDITabInfo::m_nTabBorderSize
- AFXMDICLIENTAREAWND/CMDITabInfo::m_style
- AFXMDICLIENTAREAWND/CMDITabInfo::m_tabLocation
dev_langs:
- C++
helpviewer_keywords:
- CMDITabInfo class
- CMDITabInfo class, constructor
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
caps.latest.revision: 37
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: a45532c98d5da7d89d27e3d29d9b40075cf0376f
ms.lasthandoff: 02/24/2017

---
# <a name="cmditabinfo-class"></a>Clase CMDITabInfo
El `CMDITabInfo` clase se utiliza para pasar parámetros a [CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) método. Establezca miembros de esta clase para controlar el comportamiento de MDI con grupos con pestañas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMDITabInfo   
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMDITabInfo::CMDITabInfo`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDITabInfo::Serialize](#serialize)|Lee o escribe este objeto de o en un archivo.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Especifica si un **cerrar** botón se muestra en la etiqueta de la ficha activa.|  
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Especifica si las fichas MDI de color.|  
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Especifica si el grupo de ficha muestra un menú emergente que muestra una lista de los documentos abiertos o muestra los botones de desplazamiento.|  
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Especifica si el usuario puede intercambiar las posiciones de las fichas arrastrando.|  
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Especifica si las fichas tienen un marco sin formato.|  
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Especifica si cada etiqueta de ficha muestra un **cerrar** botón.|  
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Especifica si se habilita la información sobre herramientas personalizados.|  
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Especifica si se debe mostrar iconos en las fichas MDI.|  
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Especifica el tamaño del borde de cada ventana de ficha.|  
|[CMDITabInfo::m_style](#m_style)|Especifica el estilo de las etiquetas de la ficha.|  
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Especifica si las etiquetas de las fichas se encuentran en la parte superior o inferior de la página.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase especifica los parámetros de los grupos de ficha MDI que crea el marco de trabajo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer los valores de las variables de miembros distintos de `CMDITabInfo` clase.  
  
 [!code-cpp[1 NVC_MFC_MDITab](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmdiclientareawnd.h  
  
##  <a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;  
 Especifica si un **cerrar** botón se muestra en la etiqueta de la ficha activa.  
  
```  
BOOL m_bActiveTabCloseButton;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, se mostrará la etiqueta de la ficha activa una **cerrar** botón. El **cerrar** botón se quitará de la esquina superior derecha del área de ficha. De lo contrario, no se mostrará la etiqueta de la ficha activa una **cerrar** botón. El **cerrar** botón aparecerá en la esquina superior derecha del área de ficha.  
  
##  <a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor  
 Especifica si cada ficha MDI tiene su propio color.  
  
```  
BOOL m_bAutoColor;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, cada ficha tendrá su propio color. El conjunto de colores está administrado por la biblioteca MFC. De lo contrario, las fichas se muestran en blanco. El valor predeterminado es `FALSE`.  
  
##  <a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu  
 Especifica si cada pestaña muestra un menú emergente que muestra una lista de los documentos abiertos en el borde derecho del área de ficha.  
  
```  
BOOL m_bDocumentMenu;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, windows de cada ficha muestra un menú emergente que muestra una lista de los documentos abiertos en el borde derecho del área de ficha; De lo contrario, la ventana de pestaña muestra los botones de desplazamiento en el borde derecho del área de ficha. El valor predeterminado es `FALSE`.  
  
##  <a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap  
 Especifica si el usuario puede intercambiar las posiciones de las fichas arrastrando.  
  
```  
BOOL m_bEnableTabSwap;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, el usuario puede cambiar las posiciones de las fichas, arrastre las fichas. De lo contrario, el usuario no puede cambiar las posiciones de las fichas. El valor predeterminado es `TRUE`.  
  
##  <a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame  
 Especifica si cada ventana de la ficha tiene un marco sin formato.  
  
```  
BOOL m_bFlatFrame;  
```  
  
##  <a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton  
 Especifica si cada ventana de la ficha muestra un **cerrar** botón.  
  
```  
BOOL m_bTabCloseButton;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, cada ventana de pestaña muestra la **cerrar** botón en el borde derecho de la ficha. De lo contrario, el **cerrar** botón no aparece. El valor predeterminado es `TRUE`.  
  
##  <a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips  
 Especifica si las fichas mostrar información sobre herramientas.  
  
```  
BOOL m_bTabCustomTooltips;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, la aplicación envía una `AFX_WM_ON_GET_TAB_TOOLTIP` mensaje al marco principal. Este mensaje se puede controlar mediante el uso de la `ON_REGISTERED_MESSAGE` (macro).  
  
##  <a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons  
 Especifica si se debe mostrar iconos en las fichas MDI.  
  
```  
BOOL m_bTabIcons;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si `TRUE`, iconos se muestran en cada ficha MDI. De lo contrario, los iconos no se muestran en fichas. El valor predeterminado es `FALSE`.  
  
##  <a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize  
 Especifica el tamaño del borde, en píxeles, de cada ventana de la ficha.  
  
```  
int m_nTabBorderSize;  
```  
  
### <a name="remarks"></a>Comentarios  
 [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) devuelve el valor predeterminado.  
  
##  <a name="m_style"></a>CMDITabInfo::m_style  
 Especifica el estilo de las etiquetas de la ficha.  
  
```  
CMFCTabCtrl::Style m_style  
```  
  
### <a name="remarks"></a>Comentarios  
 Especifique uno de los siguientes estilos de las etiquetas de la ficha:  
  
 `STYLE_3D`  
 Estilo&3;D.  
  
 `STYLE_3D_ONENOTE`  
 Estilo de Microsoft OneNote.  
  
 `STYLE_3D_VS2005`  
 Estilo de Microsoft Visual Studio 2005.  
  
 `STYLE_3D_SCROLLED`  
 Estilo&3;D con etiquetas de la ficha de rectángulo.  
  
 `STYLE_FLAT_SHARED_HORZ_SCROLL`  
 Estilo plano con la barra de desplazamiento horizontal compartida.  
  
 `STYLE_3D_ROUNDED_SCROLL`  
 Estilo&3;D con etiquetas de la ficha redondeo.  
  
##  <a name="m_tablocation"></a>CMDITabInfo::m_tabLocation  
 Especifica si las etiquetas de las fichas se encuentran en la parte superior o inferior de la página.  
  
```  
CMFCTabCtrl::Location m_tabLocation;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se aplican a las fichas de uno de los siguientes indicadores de ubicación:  
  
-   LOCATION_BOTTOM: las etiquetas de las fichas se encuentran en la parte inferior de la página.  
  
-   LOCATION_TOP: las etiquetas de las fichas se encuentra en la parte superior de la página  
  
##  <a name="serialize"></a>CMDITabInfo::Serialize  
 Lee o escribe este objeto desde un archivo o a un archivo.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ar`  
 Un [CArchive (clase)](../../mfc/reference/carchive-class.md) objeto que se va a serializar.  
  
## <a name="see-also"></a>Vea también  
 [CMDIFrameWndEx Class](../../mfc/reference/cmdiframewndex-class.md)   
 [Grupos con pestañas MDI](../../mfc/mdi-tabbed-groups.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

