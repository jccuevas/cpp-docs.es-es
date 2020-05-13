---
title: CMFCRibbonColorButton (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 528b883d75889589c7021f462324dd9dcb71be25
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754845"
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton (clase)

La clase `CMFCRibbonColorButton` implementa un botón en color que puede agregar a una barra de la cinta. El botón de color de la cinta muestra un menú desplegable que contiene una o varias paletas de colores.

## <a name="syntax"></a>Sintaxis

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
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

## <a name="remarks"></a>Observaciones

El botón de color de la cinta muestra una barra de color cuando un usuario lo pulsa. De forma predeterminada, esta barra de colores contiene una paleta de selección de color denominada área de color normal. Si lo desea, la barra de colores puede mostrar un botón **Automático** , que permite al usuario seleccionar un color predeterminado, y un botón **Otros** , que muestra una paleta de colores emergente que contiene colores adicionales.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonColorButton` . En el ejemplo se muestra cómo construir un objeto `CMFCRibbonColorButton` , establecer la imagen de gran tamaño, habilitar el botón **Automático** , habilitar el botón **Otros** , establecer el número de columnas, establecer el tamaño de todos los elementos de color que aparecen en la barra de colores, agregar un grupo de colores al área de color normal y especificar una lista de los valores RGB para mostrar en el área de color del documento. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribboncolorbutton.h

## <a name="cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup

Agrega un grupo de colores al área de color normal.

```cpp
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
[en] El nombre del grupo.

*lstColors*<br/>
[en] La lista de colores.

*bContiguousColumns*<br/>
[en] Controla cómo se muestran los elementos de color en el grupo. Si es TRUE, los elementos de color se dibujan sin un espaciado vertical. Si FALSE, los elementos de color se dibujan con un espaciado vertical.

### <a name="remarks"></a>Observaciones

Utilice esta función para hacer que la ventana emergente de color muestre varios grupos de colores. Puede controlar cómo se muestran los colores en grupo.

## <a name="cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton

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

*nID*<br/>
[en] Especifica el identificador de comando del comando que se ejecutará cuando un usuario haga clic en el botón.

*lpszText*<br/>
[en] Especifica el texto que aparecerá en el botón.

*nSmallImageIndex*<br/>
[en] El índice de base cero de la imagen pequeña que aparecerá en el botón.

*Color*<br/>
[en] El color del botón (por defecto es negro).

*bSimpleButtonLook*<br/>
[en] Si es TRUE, el botón se dibuja como un rectángulo simple.

*nLargeImageIndex*<br/>
[en] El índice de base cero de la imagen grande que aparecerá en el botón.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton

Especifica si el botón **Automático** está habilitado.

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] La etiqueta del botón **Automático.**

*colorAutomático*<br/>
[en] Valor RGB que especifica el color predeterminado del botón **Automático.**

*bHabilitar*<br/>
[en] TRUESi el botón **Automático** está habilitado; FALSE si está deshabilitado.

*lpszToolTip*<br/>
[en] La información sobre herramientas del botón **Automático.**

*bOnTop*<br/>
[en] Especifica si el botón **Automático** está en la parte superior, antes de la paleta de colores.

*bDrawBorder*<br/>
[en] TRUESi la aplicación dibuja un borde alrededor de la barra de color en el botón de color de la cinta de opciones. La barra de color muestra el color seleccionado actualmente. FALSE si la aplicación no dibuja un borde

## <a name="cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton

Habilita el botón **Otros** .

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
La etiqueta del botón.

*lpszToolTip*<br/>
El texto de información sobre herramientas para el botón **Otro.**

### <a name="remarks"></a>Observaciones

El botón **Otro** es el botón que se muestra debajo del grupo de colores. Cuando el usuario hace clic en el botón **Otro,** muestra un cuadro de diálogo de color.

## <a name="cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor

Recupera el color actual del botón automático.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de color RGB que representa el color de botón automático actual.

### <a name="remarks"></a>Observaciones

El color del botón `colorAutomatic` automático se `CMFCRibbonColorButton::EnableAutomaticButton` establece mediante el parámetro pasado al método.

## <a name="cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a>CMFCRibbonColorButton::GetColor

Devuelve el color actualmente seleccionado.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color seleccionado haciendo clic en el botón.

## <a name="cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize

Devuelve el tamaño de los elementos de color que aparecen en la barra de colores.

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño de los botones de color en la paleta de colores desplegable.

## <a name="cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns

Obtiene el número de elementos de una fila de la visualización de la galería del botón de color de la cinta de opciones.

```
int GetColumns() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número de iconos de cada fila.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor

Devuelve el color del elemento seleccionado actualmente en la paleta de colores emergente.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color del elemento seleccionado actualmente en la paleta de colores emergente.

## <a name="cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups

Quita todos los grupos de colores del área de color normal.

```cpp
void RemoveAllColorGroups();
```

## <a name="cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCRibbonColorButton::SetColor

Selecciona un color del área de color normal.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] Un color para establecer.

## <a name="cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize

Establece el tamaño de los elementos de color que aparecen en la barra de colores.

```cpp
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>Parámetros

*sizeBox*<br/>
[en] El nuevo tamaño de los botones de color en la paleta de colores.

## <a name="cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName

Establece un nuevo nombre para un color especificado.

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] El valor RGB de un color.

*strName*<br/>
[en] El nuevo nombre para el color especificado.

### <a name="remarks"></a>Observaciones

Dado que `CMFCColorBar::SetColorName`llama a , este método cambia `CMFCColorBar` el nombre del color especificado en todos los objetos de la aplicación.

## <a name="cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns

Establece el número de columnas que se muestran en la tabla de colores que se presenta al usuario durante el proceso de selección de color del usuario.

```cpp
void SetColumns(int nColumns);
```

### <a name="parameters"></a>Parámetros

*nColumns*<br/>
[en] El número de iconos de color que se mostrarán en cada fila.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors

Especifica una lista de valores RGB para mostrar en el área de color del documento.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] El texto que se mostrará con los colores del documento.

*lstColors*<br/>
[en] Una referencia a una lista de valores RGB.

## <a name="cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCRibbonColorButton::SetPalette

Especifica los colores estándar que se mostrarán en la tabla de colores que muestra el botón de color.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parámetros

*pPalette*<br/>
[en] Puntero a una paleta de colores.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor

Llamado por el marco de trabajo cuando el usuario selecciona un color de la tabla de colores que se muestra cuando el usuario hace clic en el botón de color.

```cpp
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] Color seleccionado por el usuario.

### <a name="remarks"></a>Observaciones

El `CMFCRibbonColorButton::UpdateColor` método cambia el color del botón seleccionado actualmente y notifica a su elemento primario mediante el envío de un mensaje de WM_COMMAND con una notificación estándar BN_CLICKED. Utilice el [CMFCRibbonColorButton::GetColor](#getcolor) método para recuperar el color seleccionado.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery (Clase)](../../mfc/reference/cmfcribbongallery-class.md)
