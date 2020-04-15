---
title: CMDITabInfo (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 0d230d2a3401ab556adc1183f4c4210ec6ff3c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370035"
---
# <a name="cmditabinfo-class"></a>CMDITabInfo (clase)

La `CMDITabInfo` clase se utiliza para pasar parámetros a [CMDIFrameWndEx::EnableMDITabbedGroups](../../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups) método. Establezca miembros de esta clase para controlar el comportamiento de MDI con grupos con pestañas.

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
|[CMDITabInfo::m_bActiveTabCloseButton;](#m_bactivetabclosebutton_)|Especifica si se muestra un botón **Cerrar** en la etiqueta de la ficha activa.|
|[CMDITabInfo::m_bAutoColor](#m_bautocolor)|Especifica si se deben colorear las fichas MDI.|
|[CMDITabInfo::m_bDocumentMenu](#m_bdocumentmenu)|Especifica si el grupo de fichas muestra un menú emergente que muestra una lista de documentos abiertos o botones de desplazamiento.|
|[CMDITabInfo::m_bEnableTabSwap](#m_benabletabswap)|Especifica si el usuario puede intercambiar las posiciones de las pestañas arrastrando.|
|[CMDITabInfo::m_bFlatFrame](#m_bflatframe)|Especifica si las fichas tienen un marco plano.|
|[CMDITabInfo::m_bTabCloseButton](#m_btabclosebutton)|Especifica si cada etiqueta de ficha muestra un botón **Cerrar.**|
|[CMDITabInfo::m_bTabCustomTooltips](#m_btabcustomtooltips)|Especifica si la información sobre herramientas personalizada está habilitada.|
|[CMDITabInfo::m_bTabIcons](#m_btabicons)|Especifica si se mostrarán iconos en las fichas MDI.|
|[CMDITabInfo::m_nTabBorderSize](#m_ntabbordersize)|Especifica el tamaño del borde de cada ventana de ficha.|
|[CMDITabInfo::m_style](#m_style)|Especifica el estilo de las etiquetas de tabulación.|
|[CMDITabInfo::m_tabLocation](#m_tablocation)|Especifica si las etiquetas de las pestañas se encuentran en la parte superior o inferior de la página.|

## <a name="remarks"></a>Observaciones

Esta clase especifica los parámetros de los grupos de pestañas MDI que crea el marco de trabajo.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer los `CMDITabInfo` valores de las distintas variables miembro en la clase.

[!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/cpp/cmditabinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmdiclientareawnd.h

## <a name="cmditabinfom_bactivetabclosebutton"></a><a name="m_bactivetabclosebutton_"></a>CMDITabInfo::m_bActiveTabCloseButton;

Especifica si se muestra un botón **Cerrar** en la etiqueta de la ficha activa.

```
BOOL m_bActiveTabCloseButton;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, la etiqueta de la pestaña activa mostrará un botón **Cerrar.** El botón **Cerrar** se eliminará de la esquina superior derecha del área de pestañas. De lo contrario, la etiqueta de la pestaña activa no mostrará un botón **Cerrar.** El botón **Cerrar** aparecerá en la esquina superior derecha del área de la pestaña.

## <a name="cmditabinfom_bautocolor"></a><a name="m_bautocolor"></a>CMDITabInfo::m_bAutoColor

Especifica si cada ficha MDI tiene su propio color.

```
BOOL m_bAutoColor;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, cada pestaña tendrá su propio color. La biblioteca MFC administra el conjunto de colores. De lo contrario, las pestañas se muestran en blanco. El valor predeterminado es FALSE.

## <a name="cmditabinfom_bdocumentmenu"></a><a name="m_bdocumentmenu"></a>CMDITabInfo::m_bDocumentMenu

Especifica si cada ficha muestra un menú emergente que muestra una lista de documentos abiertos en el borde derecho del área de ficha.

```
BOOL m_bDocumentMenu;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, cada ventana muestra un menú emergente que muestra una lista de documentos abiertos en el borde derecho del área de ficha; De lo contrario, la ventana de pestañas muestra los botones de desplazamiento en el borde derecho del área de ficha. El valor predeterminado es FALSE.

## <a name="cmditabinfom_benabletabswap"></a><a name="m_benabletabswap"></a>CMDITabInfo::m_bEnableTabSwap

Especifica si el usuario puede intercambiar las posiciones de las pestañas arrastrando.

```
BOOL m_bEnableTabSwap;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, el usuario puede cambiar las posiciones de las pestañas arrastrando las pestañas. De lo contrario, el usuario no puede cambiar las posiciones de las pestañas. El valor predeterminado es TRUE.

## <a name="cmditabinfom_bflatframe"></a><a name="m_bflatframe"></a>CMDITabInfo::m_bFlatFrame

Especifica si cada ventana de ficha tiene un marco plano.

```
BOOL m_bFlatFrame;
```

## <a name="cmditabinfom_btabclosebutton"></a><a name="m_btabclosebutton"></a>CMDITabInfo::m_bTabCloseButton

Especifica si cada ventana de ficha muestra un botón **Cerrar.**

```
BOOL m_bTabCloseButton;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, cada ventana de ficha muestra el botón **Close** **Cerrar** en el borde derecho de la ficha. El valor predeterminado es TRUE.

## <a name="cmditabinfom_btabcustomtooltips"></a><a name="m_btabcustomtooltips"></a>CMDITabInfo::m_bTabCustomTooltips

Especifica si las fichas muestran información sobre herramientas.

```
BOOL m_bTabCustomTooltips;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, la aplicación envía un mensaje de AFX_WM_ON_GET_TAB_TOOLTIP al marco principal. Puede controlar este mensaje mediante la macro ON_REGISTERED_MESSAGE.

## <a name="cmditabinfom_btabicons"></a><a name="m_btabicons"></a>CMDITabInfo::m_bTabIcons

Especifica si se mostrarán iconos en las fichas MDI.

```
BOOL m_bTabIcons;
```

### <a name="remarks"></a>Observaciones

Si es TRUE, los iconos se muestran en cada ficha MDI. De lo contrario, los iconos no se muestran en las pestañas. El valor predeterminado es FALSE.

## <a name="cmditabinfom_ntabbordersize"></a><a name="m_ntabbordersize"></a>CMDITabInfo::m_nTabBorderSize

Especifica el tamaño del borde, en píxeles, de cada ventana de ficha.

```
int m_nTabBorderSize;
```

### <a name="remarks"></a>Observaciones

[CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize) devuelve el valor predeterminado.

## <a name="cmditabinfom_style"></a><a name="m_style"></a>CMDITabInfo::m_style

Especifica el estilo de las etiquetas de tabulación.

```
CMFCTabCtrl::Style m_style
```

### <a name="remarks"></a>Observaciones

Especifique uno de los siguientes estilos para las etiquetas de tabulación:

|||
|-|-|
|STYLE_3D|Estilo 3D.  |
|STYLE_3D_ONENOTE|Estilo Microsoft OneNote.  |
|STYLE_3D_VS2005|Estilo de Microsoft Visual Studio 2005.  |
|STYLE_3D_SCROLLED|Estilo 3D con etiquetas de pestaña rectangulares.  |
|STYLE_FLAT_SHARED_HORZ_SCROLL|Estilo plano con barra de desplazamiento horizontal compartida.  |
|STYLE_3D_ROUNDED_SCROLL|Estilo 3D con etiquetas de pestaña redondas.  |

## <a name="cmditabinfom_tablocation"></a><a name="m_tablocation"></a>CMDITabInfo::m_tabLocation

Especifica si las etiquetas de las pestañas se encuentran en la parte superior o inferior de la página.

```
CMFCTabCtrl::Location m_tabLocation;
```

### <a name="remarks"></a>Observaciones

Aplique a las pestañas uno de los siguientes indicadores de ubicación:

- LOCATION_BOTTOM: las etiquetas de las pestañas se encuentran en la parte inferior de la página.

- LOCATION_TOP: las etiquetas de las pestañas se encuentran en la parte superior de la página

## <a name="cmditabinfoserialize"></a><a name="serialize"></a>CMDITabInfo::Serialize

Lee o escribe este objeto desde un archivo o en un archivo.

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
[en] Un [CArchive clase](../../mfc/reference/carchive-class.md) objeto para serializar.

## <a name="see-also"></a>Consulte también

[CMDIFrameWndEx Clase](../../mfc/reference/cmdiframewndex-class.md)<br/>
[Grupos con pestañas MDI](../../mfc/mdi-tabbed-groups.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
