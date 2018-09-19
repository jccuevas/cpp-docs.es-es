---
title: CMDITabInfo (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CMDITabInfo [MFC], Serialize
- CMDITabInfo [MFC], m_bAutoColor
- CMDITabInfo [MFC], m_bDocumentMenu
- CMDITabInfo [MFC], m_bEnableTabSwap
- CMDITabInfo [MFC], m_bFlatFrame
- CMDITabInfo [MFC], m_bTabCloseButton
- CMDITabInfo [MFC], m_bTabCustomTooltips
- CMDITabInfo [MFC], m_bTabIcons
- CMDITabInfo [MFC], m_nTabBorderSize
- CMDITabInfo [MFC], m_style
- CMDITabInfo [MFC], m_tabLocation
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7cd0355c4d0ce203617729142e03860e9960190a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726614"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo (clase)
El `CMDITabInfo` clase se utiliza para pasar parámetros al [CMDIFrameWndEx:: Enablemditabbedgroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) método. Establezca miembros de esta clase para controlar el comportamiento de MDI con grupos con pestañas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMDITabInfo   
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMDITabInfo::CMDITabInfo`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDITabInfo::Serialize](#serialize)|Lee o escribe este objeto de o en un archivo.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Especifica si un **cerrar** botón se muestra en la etiqueta de la pestaña activa.|  
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Especifica si las pestañas MDI de color.|  
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Especifica si el grupo de pestañas que muestra un menú emergente que muestra una lista de los documentos abiertos o muestra los botones de desplazamiento.|  
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Especifica si el usuario puede intercambiar las posiciones de las pestañas arrastrando.|  
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Especifica si las fichas tienen un marco sin formato.|  
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Especifica si se muestra cada etiqueta de ficha un **cerrar** botón.|  
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Especifica si se habilita la información sobre herramientas personalizada.|  
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Especifica si se debe mostrar iconos en pestañas MDI.|  
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Especifica el tamaño del borde de cada pestaña de ventana.|  
|[CMDITabInfo::m_style](#m_style)|Especifica el estilo de las etiquetas de pestaña.|  
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Especifica si las etiquetas de las pestañas se encuentran en la parte superior o inferior de la página.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase especifica los parámetros de los grupos de pestañas MDI que crea el marco de trabajo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer los valores de las variables de miembro distintos de `CMDITabInfo` clase.  
  
 [!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmdiclientareawnd.h  
  
##  <a name="m_bactivetabclosebutton_"></a>  CMDITabInfo::m_bActiveTabCloseButton;  
 Especifica si un **cerrar** botón se muestra en la etiqueta de la pestaña activa.  
  
```  
BOOL m_bActiveTabCloseButton;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si es TRUE, se mostrará la etiqueta de la pestaña activa un **cerrar** botón. El **cerrar** botón se quitará de la esquina superior derecha del área de ficha. En caso contrario, no se mostrará la etiqueta de la pestaña activa un **cerrar** botón. El **cerrar** botón aparecerá en la esquina superior derecha del área de ficha.  
  
##  <a name="m_bautocolor"></a>  CMDITabInfo::m_bAutoColor  
 Especifica si cada ficha MDI tiene su propio color.  
  
```  
BOOL m_bAutoColor;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si es TRUE, cada ficha tendrá su propio color. El conjunto de colores se administra mediante la biblioteca MFC. En caso contrario, las fichas se muestran en blanco. El valor predeterminado es FALSE.  
  
##  <a name="m_bdocumentmenu"></a>  CMDITabInfo::m_bDocumentMenu  
 Especifica si cada pestaña muestra un menú emergente que muestra una lista de los documentos abiertos en el borde derecho del área de ficha.  
  
```  
BOOL m_bDocumentMenu;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si es TRUE, windows de cada pestaña muestra un menú emergente que muestra una lista de los documentos abiertos en el borde derecho del área de pestaña; En caso contrario, la ventana de la pestaña muestra los botones de desplazamiento en el borde derecho del área de ficha. El valor predeterminado es FALSE.  
  
##  <a name="m_benabletabswap"></a>  CMDITabInfo::m_bEnableTabSwap  
 Especifica si el usuario puede intercambiar las posiciones de las pestañas arrastrando.  
  
```  
BOOL m_bEnableTabSwap;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si es TRUE, el usuario puede cambiar las posiciones de las pestañas arrastrando las fichas. En caso contrario, el usuario no puede cambiar las posiciones de las pestañas. El valor predeterminado es TRUE.  
  
##  <a name="m_bflatframe"></a>  CMDITabInfo::m_bFlatFrame  
 Especifica si cada pestaña de ventana tiene un marco sin formato.  
  
```  
BOOL m_bFlatFrame;  
```  
  
##  <a name="m_btabclosebutton"></a>  CMDITabInfo::m_bTabCloseButton  
 Especifica si se muestra cada pestaña de ventana un **cerrar** botón.  
  
```  
BOOL m_bTabCloseButton;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si es TRUE, cada pestaña de ventana muestra el **cerrar** botón en el borde derecho de la pestaña. En caso contrario, el **cerrar** no se muestra el botón. El valor predeterminado es TRUE.  
  
##  <a name="m_btabcustomtooltips"></a>  CMDITabInfo::m_bTabCustomTooltips  
 Especifica si las pestañas muestran información sobre herramientas.  
  
```  
BOOL m_bTabCustomTooltips;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si es TRUE, la aplicación envía un mensaje AFX_WM_ON_GET_TAB_TOOLTIP al marco principal. Puede controlar este mensaje con el ON_REGISTERED_MESSAGE (macro).  
  
##  <a name="m_btabicons"></a>  CMDITabInfo::m_bTabIcons  
 Especifica si se debe mostrar iconos en pestañas MDI.  
  
```  
BOOL m_bTabIcons;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si es TRUE, los iconos se muestran en cada ficha MDI. En caso contrario, no se muestran iconos en pestañas. El valor predeterminado es FALSE.  
  
##  <a name="m_ntabbordersize"></a>  CMDITabInfo::m_nTabBorderSize  
 Especifica el tamaño del borde, en píxeles, de cada pestaña de ventana.  
  
```  
int m_nTabBorderSize;  
```  
  
### <a name="remarks"></a>Comentarios  
 [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) devuelve el valor predeterminado.  
  
##  <a name="m_style"></a>  CMDITabInfo::m_style  
 Especifica el estilo de las etiquetas de pestaña.  
  
```  
CMFCTabCtrl::Style m_style  
```  
  
### <a name="remarks"></a>Comentarios  
 Especifique uno de los siguientes estilos de las etiquetas de pestaña:  
  
 STYLE_3D  
 Estilo 3D.  
  
 STYLE_3D_ONENOTE  
 Estilo de Microsoft OneNote.  
  
 STYLE_3D_VS2005  
 Estilo de Microsoft Visual Studio 2005.  
  
 STYLE_3D_SCROLLED  
 Estilo 3D con etiquetas de pestaña de rectángulo.  
  
 STYLE_FLAT_SHARED_HORZ_SCROLL  
 Estilo plano con la barra de desplazamiento horizontal compartida.  
  
 STYLE_3D_ROUNDED_SCROLL  
 Estilo 3D con etiquetas de pestaña redondear.  
  
##  <a name="m_tablocation"></a>  CMDITabInfo::m_tabLocation  
 Especifica si las etiquetas de las pestañas se encuentran en la parte superior o inferior de la página.  
  
```  
CMFCTabCtrl::Location m_tabLocation;  
```  
  
### <a name="remarks"></a>Comentarios  
 Se aplican a las pestañas de uno de los siguientes indicadores de ubicación:  
  
-   LOCATION_BOTTOM: las etiquetas de las pestañas se encuentran en la parte inferior de la página.  
  
-   LOCATION_TOP: las etiquetas de las pestañas se encuentra en la parte superior de la página  
  
##  <a name="serialize"></a>  CMDITabInfo::Serialize  
 Lee o escribe este objeto desde un archivo o en un archivo.  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
*cuentas por cobrar*<br/>
[in] Un [CArchive (clase)](../../mfc/reference/carchive-class.md) objeto que se va a serializar.  
  
## <a name="see-also"></a>Vea también  
 [CMDIFrameWndEx (clase)](../../mfc/reference/cmdiframewndex-class.md)   
 [Grupos con pestañas MDI](../../mfc/mdi-tabbed-groups.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
