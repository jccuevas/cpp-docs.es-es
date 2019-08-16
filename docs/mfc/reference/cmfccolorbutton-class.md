---
title: Clase CMFCColorButton
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: ac49957f075f8798607535286d6c4518c0eeeeae
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505360"
---
# <a name="cmfccolorbutton-class"></a>Clase CMFCColorButton

Las `CMFCColorButton` clases de [clase y CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) se usan conjuntamente para implementar un control de selector de colores.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Construye un nuevo objeto `CMFCColorButton`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Habilita y deshabilita un botón "automático" situado encima de los botones de color normales. (El botón automático del sistema estándar se etiqueta **automáticamente**).|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Habilita y deshabilita un botón "otros" que está situado debajo de los botones de color normales. (El botón "otros" del sistema estándar tiene una etiqueta de **más colores**).|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Recupera el color automático actual.|
|[CMFCColorButton::GetColor](#getcolor)|Recupera el color de un botón.|
|[CMFCColorButton::SetColor](#setcolor)|Establece el color de un botón.|
|[CMFCColorButton::SetColorName](#setcolorname)|Establece un nombre de color.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Establece el número de columnas en el cuadro de diálogo Selector de colores.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Especifica una lista de colores específicos del documento que se muestran en el cuadro de diálogo Selector de colores.|
|[CMFCColorButton::SetPalette](#setpalette)|Especifica una paleta de colores para mostrar estándar.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Cambia el tamaño del control de botón, en función de su tamaño de imagen y texto.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Indica si el botón de color actual se muestra en el estilo visual de Windows XP.|
|[CMFCColorButton::OnDraw](#ondraw)|Lo llama el marco de trabajo para mostrar una imagen del botón.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Lo llama el marco de trabajo para mostrar el borde del botón.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Lo llama el marco de trabajo para mostrar un rectángulo de foco cuando el botón tiene un foco.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Lo llama el marco de trabajo cuando el cuadro de diálogo Selector de colores está a punto de mostrarse.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicializa el `m_pPalette` miembro de datos protegido en la paleta especificada o en la paleta predeterminada del sistema.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Lo llama el marco de trabajo cuando el usuario selecciona un color de la paleta del cuadro de diálogo Selector de colores.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`m_bAltColorDlg`|Un valor booleano. Si es TRUE, el marco de trabajo muestra el cuadro de diálogo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) color al hacer clic en el *otro* botón, o bien, si es false, el cuadro de diálogo color del sistema. El valor predeterminado es TRUE. Para obtener más información, vea [CMFCColorButton:: EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Un valor booleano. Si es TRUE, el marco de trabajo establece el foco en el menú de color cuando se muestra el menú, o bien, si es FALSE, no cambia el foco. El valor predeterminado es TRUE.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Indica si está habilitado el modo de personalización para el botón de color.|
|`m_Color`|Valor de [COLORREF](/windows/win32/gdi/colorref) . Contiene el color seleccionado actualmente.|
|`m_ColorAutomatic`|Valor de [COLORREF](/windows/win32/gdi/colorref) . Contiene el color predeterminado seleccionado actualmente.|
|`m_Colors`|[CArray](../../mfc/reference/carray-class.md) de valores [COLORREF](/windows/win32/gdi/colorref) . Contiene los colores disponibles actualmente.|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) de valores [COLORREF](/windows/win32/gdi/colorref) . Contiene los colores del documento actual.|
|`m_nColumns`|Entero. Contiene el número de columnas que se van a mostrar en la cuadrícula de colores de un menú de selección de color.|
|`m_pPalette`|Un puntero a un [CPalette](../../mfc/reference/cpalette-class.md). Contiene los colores que están disponibles en el menú de selección de color actual.|
|`m_pPopup`|Un puntero a un objeto de la [clase CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md) . El menú de selección de color que se muestra al hacer clic en el botón de color.|
|`m_strAutoColorText`|Una cadena. La etiqueta del botón "automático" en un menú de selección de color.|
|`m_strDocColorsText`|Una cadena. La etiqueta del botón en un menú de selección de color que muestra los colores del documento.|
|`m_strOtherText`|Una cadena. La etiqueta del botón "otros" en un menú de selección de color.|

## <a name="remarks"></a>Comentarios

De forma predeterminada, `CMFCColorButton` la clase se comporta como un botón de opción que abre un cuadro de diálogo Selector de colores. El cuadro de diálogo Selector de colores contiene una matriz de botones de color pequeños y un botón "otros" que muestra un selector de colores personalizado. (El botón "otros" del sistema estándar tiene una etiqueta de **más colores**). Cuando un usuario selecciona un nuevo color, el `CMFCColorButton` objeto refleja el cambio y muestra el color seleccionado.

Cree un control de botón de color directamente en el código o mediante la herramienta **ClassWizard** y una plantilla de cuadro de diálogo. Si crea un control de botón de color directamente, agregue `CMFCColorButton` una variable a la aplicación y, a continuación, llame `Create` al constructor y `CMFCColorButton` a los métodos del objeto. Si utiliza el **ClassWizard**, agregue una `CButton` variable a la aplicación y, a continuación, cambie el tipo de la variable de `CMFCColorButton` `CButton` a.

El método [CMFCColorButton:: OnShowColorPopup](#onshowcolorpopup) muestra el cuadro de diálogo Selector de colores ( [clase CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)) cuando el marco llama al controlador `OnLButtonDown` de eventos. El método [CMFCColorButton:: OnShowColorPopup](#onshowcolorpopup) se puede invalidar para admitir la selección de colores personalizada.

El `CMFCColorButton` objeto notifica a su elemento primario que un color está cambiando enviándole un WM_COMMAND | Notificación de BN_CLICKED. El elemento primario usa el método [CMFCColorButton:: GetColor](#getcolor) para recuperar el color actual.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar un botón de color mediante el uso de `CMFCColorButton` varios métodos en la clase. Los métodos establecen el color del botón de color y el número de columnas, y habilitan los botones automático y otros. Este ejemplo forma parte del ejemplo de demostración de la [barra de estado](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolorbutton. h

##  <a name="cmfccolorbutton"></a>  CMFCColorButton::CMFCColorButton

Construye un nuevo objeto `CMFCColorButton`.

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton

Habilitar o deshabilitar el botón "automático" de un control selector de colores y establecer el color automático (predeterminado).

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
de Especifica el texto del botón automático.

*colorAutomatic*<br/>
de Valor RGB que especifica el color predeterminado del botón automático.

*bEnable*<br/>
de Especifica si el botón automático está habilitado o deshabilitado.

### <a name="remarks"></a>Comentarios

##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton

Habilitar o deshabilitar el botón "otro", que aparece debajo de los botones de color normales.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
de Especifica el texto del botón.

*bAltColorDlg*<br/>
de Especifica si el cuadro de diálogo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) o el cuadro de diálogo color del sistema se abre cuando el usuario hace clic en el botón.

*bEnable*<br/>
de Especifica si el botón "otros" está habilitado o deshabilitado.

### <a name="remarks"></a>Comentarios

Haga clic en el botón "otro" para mostrar un cuadro de diálogo de color. Si el parámetro *bAltColorDlg* es true, se muestra la [clase CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) . de lo contrario, se muestra el cuadro de diálogo color del sistema.

##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor

Recupera el color automático actual (predeterminado).

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor RGB que representa el color automático actual.

### <a name="remarks"></a>Comentarios

El color automático actual se establece mediante el método [CMFCColorButton:: EnableAutomaticButton](#enableautomaticbutton) .

##  <a name="getcolor"></a>  CMFCColorButton::GetColor

Recupera el color seleccionado actualmente.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor RGB.

### <a name="remarks"></a>Comentarios

##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme

Indica si el botón de color actual se muestra en el estilo visual de Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se admiten los estilos visuales y el botón de color actual se muestra en el estilo visual de Windows XP; en caso contrario, FALSE.

##  <a name="m_benabledincustomizemode"></a>  CMFCColorButton::m_bEnabledInCustomizeMode

Establece un botón de color para el modo de personalización.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Comentarios

Si necesita agregar un botón de color a la página de un cuadro de diálogo de personalización (o permitir que el usuario realice otra selección de color durante la personalización), habilite `m_bEnabledInCustomizeMode` el botón estableciendo el miembro en true. De forma predeterminada, este miembro está establecido en FALSE.

##  <a name="ondraw"></a>  CMFCColorButton::OnDraw

Lo llama el marco de trabajo para presentar una imagen del botón.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Apunta al contexto del dispositivo que se usa para representar la imagen del botón.

*rect*<br/>
de Rectángulo que delimita el botón.

*uiState*<br/>
de Especifica el estado visual del botón.

### <a name="remarks"></a>Comentarios

Invalide este método para personalizar el proceso de representación.

##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder

Lo llama el marco de trabajo para mostrar el borde del botón.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Apunta al contexto del dispositivo que se usa para dibujar el borde.

*rectClient*<br/>
de Rectángulo en el contexto de dispositivo que se especifica mediante el parámetro de *pDC* que define los límites del botón que se va a dibujar.

*uiState*<br/>
de Especifica el estado visual del botón.

### <a name="remarks"></a>Comentarios

Invalide esta función para personalizar la apariencia del borde del botón de color.

##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect

Lo llama el marco de trabajo para mostrar un rectángulo de foco cuando el botón tiene el foco.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Apunta al contexto del dispositivo que se usa para dibujar el rectángulo de foco.

*rectClient*<br/>
de Rectángulo en el contexto de dispositivo especificado por el parámetro de *pDC* que define los límites del botón.

### <a name="remarks"></a>Comentarios

Invalide este método para personalizar la apariencia del rectángulo de foco.

##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup

Se llama antes de que se muestre la barra de colores emergente.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Comentarios

##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette

Inicializa el `m_pPalette` miembro de datos protegido en la paleta especificada o en la paleta predeterminada del sistema.

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*pPal*|de Puntero a una paleta lógica o NULL. Si es NULL, se utiliza la paleta predeterminada del sistema.|

##  <a name="setcolor"></a>  CMFCColorButton::SetColor

Especifica el color del botón.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
de Valor RGB.

### <a name="remarks"></a>Comentarios

##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName

Especifica el nombre de un color.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
de Valor RGB del color.

*strName*<br/>
de Nombre del color.

### <a name="remarks"></a>Comentarios

La lista de nombres de colores es global por aplicación. Por consiguiente, este método transfiere sus parámetros a [CMFCColorBar:: SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber

Define el número de columnas que se muestran en la tabla de colores que se presenta al usuario durante el proceso de selección del color del usuario.

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parámetros

*nColumns*<br/>
de Especifica el número de columnas.

### <a name="remarks"></a>Comentarios

El usuario puede seleccionar un color de una barra de colores emergente que muestra una tabla de colores predefinidos. Utilice este método para definir el número de columnas de la tabla.

##  <a name="setdocumentcolors"></a>  CMFCColorButton::SetDocumentColors

Especifica un conjunto de colores y el nombre del conjunto. El conjunto de colores se muestra mediante un objeto de la [clase CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) .

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
de Especifica la etiqueta que se va a mostrar con el conjunto de colores del documento.

*lstColors*<br/>
de Referencia a una lista de valores RGB.

### <a name="remarks"></a>Comentarios

Un `CMFCColorButton` objeto mantiene una lista de valores RGB que se transfieren a un objeto de la [clase CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) . Cuando se muestra la barra de colores, estos colores se muestran en una sección especial cuya etiqueta se especifica mediante el parámetro *lpszLabel* .

##  <a name="setpalette"></a>  CMFCColorButton::SetPalette

Especifica los colores estándar que se van a mostrar en la barra de colores emergente.

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parámetros

*pPalette*<br/>
de Puntero a una paleta de colores.

### <a name="remarks"></a>Comentarios

##  <a name="sizetocontent"></a>  CMFCColorButton::SizeToContent

Cambia el tamaño del control de botón para ajustarse a su texto e imagen.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parámetros

*bCalcOnly*<br/>
de Si es distinto de cero, se calcula el nuevo tamaño del control de botón, pero no se cambia el tamaño real.

### <a name="return-value"></a>Valor devuelto

`CSize` Objeto que especifica un nuevo tamaño del control de botón.

### <a name="remarks"></a>Comentarios

##  <a name="updatecolor"></a>  CMFCColorButton::UpdateColor

Lo llama el marco de trabajo cuando el usuario selecciona un color de la barra de colores que se muestra cuando el usuario hace clic en el botón de color.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
de Color seleccionado por el usuario.

### <a name="remarks"></a>Comentarios

La `UpdateColor` función cambia el color del botón seleccionado actualmente y notifica a su elemento primario mediante el envío de un mensaje WM_COMMAND con una notificación estándar de BN_CLICKED. Use el método [CMFCColorButton:: GetColor](#getcolor) para recuperar el color seleccionado.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton (clase)](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar (clase)](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette (clase)](../../mfc/reference/cpalette-class.md)<br/>
[CArray (clase)](../../mfc/reference/carray-class.md)<br/>
[CList (clase)](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
