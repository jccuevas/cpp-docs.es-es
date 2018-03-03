---
title: Clase CMFCRibbonColorButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b8da5a7a05f1765fea840c579c91ddd9b3ef672b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton (clase)
La clase `CMFCRibbonColorButton` implementa un botón en color que puede agregar a una barra de la cinta. El botón de color de la cinta muestra un menú desplegable que contiene una o varias paletas de colores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCRibbonColorButton : public CMFCRibbonGallery  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Agrega un grupo de colores al área de color normal.|  
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Especifica si el botón **Automático** está habilitado.|  
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Habilita el botón **Otros** .|  
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||  
|[CMFCRibbonColorButton::GetColor](#getcolor)|Devuelve el color actualmente seleccionado.|  
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Devuelve el tamaño de los elementos de color que aparecen en la barra de colores.|  
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||  
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Devuelve el color del elemento actualmente seleccionado en la paleta de colores emergente.|  
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Quita todos los grupos de colores del área de color normal.|  
|[CMFCRibbonColorButton::SetColor](#setcolor)|Selecciona un color del área de color normal.|  
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Establece el tamaño de los elementos de color que aparecen en la barra de colores.|  
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||  
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||  
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Especifica una lista de valores RGB para mostrar en el área de color del documento.|  
|[CMFCRibbonColorButton::SetPalette](#setpalette)||  
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||  
  
## <a name="remarks"></a>Comentarios  
 El botón de color de la cinta muestra una barra de color cuando un usuario lo pulsa. De forma predeterminada, esta barra de colores contiene una paleta de selección de color denominada área de color normal. Si lo desea, la barra de colores puede mostrar un botón **Automático** , que permite al usuario seleccionar un color predeterminado, y un botón **Otros** , que muestra una paleta de colores emergente que contiene colores adicionales.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonColorButton` . En el ejemplo se muestra cómo construir un objeto `CMFCRibbonColorButton` , establecer la imagen de gran tamaño, habilitar el botón **Automático** , habilitar el botón **Otros** , establecer el número de columnas, establecer el tamaño de todos los elementos de color que aparecen en la barra de colores, agregar un grupo de colores al área de color normal y especificar una lista de los valores RGB para mostrar en el área de color del documento. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxribboncolorbutton.h  
  
##  <a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup  
 Agrega un grupo de colores al área de color normal.  
  
```  
void AddColorsGroup(
    LPCTSTR lpszName,  
    const CList<COLORREF,COLORREF>& lstColors,  
    BOOL bContiguousColumns=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszName`  
 El nombre del grupo.  
  
 [in] `lstColors`  
 La lista de colores.  
  
 [in] `bContiguousColumns`  
 Controla cómo se muestran los elementos de color en el grupo. Si `TRUE`, los elementos de color se dibujan sin un espaciado vertical. Si `FALSE`, los elementos de color se dibujan con un espaciado vertical.  
  
### <a name="remarks"></a>Comentarios  
 Use esta función para hacer que el color emergente Mostrar varios grupos de colores. Puede controlar cómo se muestran los colores de grupo.  
  
##  <a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton  
 Construye un objeto `CMFCRibbonColorButton`.  
  
```  
CMFCRibbonColorButton();

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    int nSmallImageIndex,  
    COLORREF color = RGB(0, 0, 0));

 
CMFCRibbonColorButton(
    UINT nID,  
    LPCTSTR lpszText,  
    BOOL bSimpleButtonLook,  
    int nSmallImageIndex,  
    int nLargeImageIndex,  
    COLORREF color = RGB(0, 0, 0));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Especifica el identificador de comando del comando que se ejecutará cuando un usuario hace clic en el botón.  
  
 [in] `lpszText`  
 Especifica el texto para que aparezca en el botón.  
  
 [in] `nSmallImageIndex`  
 Índice de base cero de la imagen pequeña que aparece en el botón.  
  
 [in] `color`  
 El color del botón (el valor predeterminado es negro).  
  
 [in] `bSimpleButtonLook`  
 Si `TRUE`, el botón se dibuja como un simple rectángulo.  
  
 [in] `nLargeImageIndex`  
 Índice de base cero de la imagen que aparecerá en el botón grande.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton  
 Especifica si el botón **Automático** está habilitado.  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE,  
    LPCTSTR lpszToolTip=NULL,  
    BOOL bOnTop=TRUE,  
    BOOL bDrawBorder=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 La etiqueta de la **automática** botón.  
  
 [in] `colorAutomatic`  
 Un valor RGB que especifica la **automática** color predeterminado de un botón.  
  
 [in] `bEnable`  
 `TRUE`Si el **automática** botón está habilitado; `FALSE` si está deshabilitado.  
  
 [in] `lpszToolTip`  
 La información sobre herramientas de la **automática** botón.  
  
 [in] `bOnTop`  
 Especifica si el **automática** botón está en la parte superior, antes de la paleta de colores.  
  
 [in] `bDrawBorder`  
 `TRUE`Si la aplicación dibuja un borde alrededor de la barra de colores en el botón de color de la cinta de opciones. Barra de colores muestra el color seleccionado actualmente. `FALSE`Si la aplicación no dibuja un borde  
  
##  <a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton  
 Habilita el botón **Otros** .  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    LPCTSTR lpszToolTip=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszLabel`  
 La etiqueta del botón.  
  
 `lpszToolTip`  
 El texto de información sobre herramientas para el **otros** botón.  
  
### <a name="remarks"></a>Comentarios  
 El **otros** botón es el que se muestra debajo del grupo de colores. Cuando el usuario hace clic en el **otros** botón, muestra un cuadro de diálogo color.  
  
##  <a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor  
 Recupera el color del botón automático actual.  
  
```  
COLORREF GetAutomaticColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de color RGB que representa el color del botón automático actual.  
  
### <a name="remarks"></a>Comentarios  
 Establece el color del botón automático el `colorAutomatic` parámetro pasado a la `CMFCRibbonColorButton::EnableAutomaticButton` método.  
  
##  <a name="getcolor"></a>CMFCRibbonColorButton::GetColor  
 Devuelve el color actualmente seleccionado.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color seleccionado, haga clic en el botón.  
  
##  <a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize  
 Devuelve el tamaño de los elementos de color que aparecen en la barra de colores.  
  
```  
CSize GetColorBoxSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de los botones de color en la paleta de colores de la lista desplegable.  
  
##  <a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns  
 Obtiene el número de elementos en una fila de la presentación de la Galería del botón de color de la cinta de opciones.  
  
```  
int GetColumns() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de iconos de cada fila.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor  
 Devuelve el color del elemento actualmente seleccionado en la paleta de colores emergente.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color del elemento actualmente seleccionado en la paleta de colores emergente.  
  
##  <a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups  
 Quita todos los grupos de colores del área de color normal.  
  
```  
void RemoveAllColorGroups();
```  
  
##  <a name="setcolor"></a>CMFCRibbonColorButton::SetColor  
 Selecciona un color del área de color normal.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un color para establecer.  
  
##  <a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize  
 Establece el tamaño de los elementos de color que aparecen en la barra de colores.  
  
```  
void SetColorBoxSize(CSize sizeBox);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `sizeBox`  
 El nuevo tamaño de los botones de color en la paleta de colores.  
  
##  <a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName  
 Establece un nuevo nombre para un color especificado.  
  
```  
static void __stdcall SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 El valor RGB de un color.  
  
 [in] `strName`  
 El nuevo nombre para el color especificado.  
  
### <a name="remarks"></a>Comentarios  
 Dado que llama `CMFCColorBar::SetColorName`, este método cambia el nombre del color especificado en todos los `CMFCColorBar` objetos de la aplicación.  
  
##  <a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns  
 Establece el número de columnas que se muestran en la tabla de colores que se presenta al usuario durante el proceso de selección de color del usuario.  
  
```  
void SetColumns(int nColumns);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nColumns`  
 El número de iconos de colores para mostrar en cada fila.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors  
 Especifica una lista de valores RGB para mostrar en el área de color del documento.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszLabel,  
    CList<COLORREF,COLORREF>& lstColors);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 El texto que se mostrará con los colores del documento.  
  
 [in] `lstColors`  
 Una referencia a una lista de los valores RGB.  
  
##  <a name="setpalette"></a>CMFCRibbonColorButton::SetPalette  
 Especifica los colores estándares para mostrar en la tabla de colores que muestra el botón de color.  
  
```  
void SetPalette(CPalette* pPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPalette`  
 Un puntero a una paleta de colores.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor  
 Lo llama el marco cuando el usuario selecciona un color de la tabla de color que se muestra cuando el usuario hace clic en el botón de color.  
  
```  
void UpdateColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un color seleccionado por el usuario.  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCRibbonColorButton::UpdateColor` método cambia el color del botón seleccionado actualmente y notifica a su elemento primario mediante el envío de un `WM_COMMAND` de mensajes con un `BN_CLICKED` notificación estándar. Use la [CMFCRibbonColorButton::GetColor](#getcolor) método para recuperar el color seleccionado.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery (clase)](../../mfc/reference/cmfcribbongallery-class.md)
