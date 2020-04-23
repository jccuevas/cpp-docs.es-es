---
title: CMFCColorButton (Clase)
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
ms.openlocfilehash: cf24c162d0eda272f73c69c434589ae6ef3332a4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752564"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton (Clase)

Las `CMFCColorButton` clases [y CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) se usan juntas para implementar un control de selector de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorButton::CMFCColorButton](#cmfccolorbutton)|Construye un nuevo objeto `CMFCColorButton`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|Activa y desactiva un botón "automático" que se coloca encima de los botones de color normales. (El botón automático estándar del sistema está etiquetado como **Automático**.)|
|[CMFCColorButton::EnableOtherButton](#enableotherbutton)|Habilita y deshabilita un botón "otros" que se coloca debajo de los botones de color normales. (El botón estándar del sistema "otros" está etiquetado como **Más Colores**.)|
|[CMFCColorButton::GetAutomaticColor](#getautomaticcolor)|Recupera el color automático actual.|
|[CMFCColorButton::GetColor](#getcolor)|Recupera el color de un botón.|
|[CMFCColorButton::SetColor](#setcolor)|Establece el color de un botón.|
|[CMFCColorButton::SetColorName](#setcolorname)|Establece un nombre de color.|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|Establece el número de columnas en el cuadro de diálogo del selector de color.|
|[CMFCColorButton::SetDocumentColors](#setdocumentcolors)|Especifica una lista de colores específicos del documento que se muestran en el cuadro de diálogo del selector de color.|
|[CMFCColorButton::SetPalette](#setpalette)|Especifica una paleta de colores de visualización estándar.|
|[CMFCColorButton::SizeToContent](#sizetocontent)|Cambia el tamaño del control de botón, dependiendo de su texto y tamaño de imagen.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorButton::IsDrawXPTheme](#isdrawxptheme)|Indica si el botón de color actual se muestra en el estilo visual de Windows XP.|
|[CMFCColorButton::OnDraw](#ondraw)|Llamado por el marco de trabajo para mostrar una imagen del botón.|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|Llamado por el marco de trabajo para mostrar el borde del botón.|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|Llamado por el marco de trabajo para mostrar un rectángulo de foco cuando el botón tiene un foco.|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|Llamado por el marco de trabajo cuando el cuadro de diálogo del selector de color está a punto de mostrarse.|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|Inicializa el `m_pPalette` miembro de datos protegidos en la paleta especificada o en la paleta del sistema predeterminada.|
|[CMFCColorButton::UpdateColor](#updatecolor)|Llamado por el marco de trabajo cuando el usuario selecciona un color de la paleta del cuadro de diálogo del selector de color.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|`m_bAltColorDlg`|Un valor booleano. Si es TRUE, el marco de trabajo muestra el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo de color cuando se hace clic en el *otro* botón, o si FALSE, el cuadro de diálogo de color del sistema. El valor predeterminado es TRUE. Para obtener más información, vea [CMFCColorButton::EnableOtherButton](#enableotherbutton).|
|`m_bAutoSetFocus`|Un valor booleano. Si es TRUE, el marco de trabajo establece el foco en el menú de color cuando se muestra el menú, o si FALSE, no cambia el foco. El valor predeterminado es TRUE.|
|[CMFCColorButton::m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|Indica si el modo de personalización está habilitado para el botón de color.|
|`m_Color`|Un valor [COLORREF.](/windows/win32/gdi/colorref) Contiene el color seleccionado actualmente.|
|`m_ColorAutomatic`|Un valor [COLORREF.](/windows/win32/gdi/colorref) Contiene el color predeterminado seleccionado actualmente.|
|`m_Colors`|Un [CArray](../../mfc/reference/carray-class.md) de [COLORREF](/windows/win32/gdi/colorref) valores. Contiene los colores disponibles actualmente.|
|`m_lstDocColors`|Una [Lista C](../../mfc/reference/clist-class.md) list de [colorref](/windows/win32/gdi/colorref) valores. Contiene los colores actuales del documento.|
|`m_nColumns`|Un entero. Contiene el número de columnas que se mostrarán en la cuadrícula de colores en un menú de selección de colores.|
|`m_pPalette`|Un puntero a un [CPalette](../../mfc/reference/cpalette-class.md). Contiene los colores disponibles en el menú de selección de color actual.|
|`m_pPopup`|Un puntero a un [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md) clase objeto. El menú de selección de color que se muestra al hacer clic en el botón de color.|
|`m_strAutoColorText`|Una cadena. La etiqueta del botón "automático" en un menú de selección de color.|
|`m_strDocColorsText`|Una cadena. La etiqueta del botón en un menú de selección de color que muestra los colores del documento.|
|`m_strOtherText`|Una cadena. La etiqueta del botón "otros" en un menú de selección de color.|

## <a name="remarks"></a>Observaciones

De forma `CMFCColorButton` predeterminada, la clase se comporta como un botón pulsador que abre un cuadro de diálogo de selector de color. El cuadro de diálogo del selector de color contiene una matriz de pequeños botones de color y un botón "otros" que muestra un selector de color personalizado. (El botón estándar del sistema "otros" está etiquetado como **Más Colores**.) Cuando un usuario selecciona un `CMFCColorButton` color nuevo, el objeto refleja el cambio y muestra el color seleccionado.

Cree un control de botón de color directamente en el código o mediante la herramienta **ClassWizard** y una plantilla de cuadro de diálogo. Si crea un control de botón de color directamente, agregue una `CMFCColorButton` variable a la aplicación y, a continuación, llame al constructor y `Create` los métodos del `CMFCColorButton` objeto. Si utiliza **ClassWizard**, `CButton` agregue una variable a la aplicación y, `CButton` `CMFCColorButton`a continuación, cambie el tipo de la variable de a .

El cuadro de diálogo del selector de color ( [CMFCColorBar (Clase)](../../mfc/reference/cmfccolorbar-class.md)se muestra mediante el `OnLButtonDown` [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) método cuando el marco de trabajo llama al controlador de eventos. El [CMFCColorButton::OnShowColorPopup](#onshowcolorpopup) método se puede invalidar para admitir la selección de color personalizada.

El `CMFCColorButton` objeto notifica a su elemento primario que un color está cambiando enviándole un WM_COMMAND BN_CLICKED notificación. El elemento primario utiliza el [CMFCColorButton::GetColor](#getcolor) método para recuperar el color actual.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar un `CMFCColorButton` botón de color mediante varios métodos de la clase. Los métodos establecen el color del botón de color y su número de columnas, y habilitan el automático y los otros botones. Este ejemplo forma parte del [ejemplo Demostración](../../overview/visual-cpp-samples.md)de barra de estado.

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolorbutton.h

## <a name="cmfccolorbuttoncmfccolorbutton"></a><a name="cmfccolorbutton"></a>CMFCColorButton::CMFCColorButton

Construye un nuevo objeto `CMFCColorButton`.

```
CMFCColorButton();
```

## <a name="cmfccolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorButton::EnableAutomaticButton

Active o desactive el botón "automático" de un control de selector de color y establezca el color automático (predeterminado).

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] Especifica el texto del botón automático.

*colorAutomático*<br/>
[en] Valor RGB que especifica el color predeterminado del botón automático.

*bHabilitar*<br/>
[en] Especifica si el botón automático está habilitado o deshabilitado.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorButton::EnableOtherButton

Active o desactive el botón "otros", que aparece debajo de los botones de color normales.

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] Especifica el texto del botón.

*bAltColorDlg*<br/>
[en] Especifica si el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo o el cuadro de diálogo de color del sistema se abre cuando el usuario hace clic en el botón.

*bHabilitar*<br/>
[en] Especifica si el botón "otros" está habilitado o deshabilitado.

### <a name="remarks"></a>Observaciones

Haga clic en el botón "otros" para mostrar un cuadro de diálogo de color. Si el *bAltColorDlg* parámetro es TRUE, el [CMFCColorDialog se](../../mfc/reference/cmfccolordialog-class.md) muestra la clase; de lo contrario, se muestra el cuadro de diálogo de color del sistema.

## <a name="cmfccolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorButton::GetAutomaticColor

Recupera el color automático (predeterminado) actual.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor RGB que representa el color automático actual.

### <a name="remarks"></a>Observaciones

El color automático actual se establece mediante el [CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton) método.

## <a name="cmfccolorbuttongetcolor"></a><a name="getcolor"></a>CMFCColorButton::GetColor

Recupera el color seleccionado actualmente.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbuttonisdrawxptheme"></a><a name="isdrawxptheme"></a>CMFCColorButton::IsDrawXPTheme

Indica si el botón de color actual se muestra en el estilo visual de Windows XP.

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se admiten estilos visuales y el botón de color actual se muestra en el estilo visual de Windows XP; de lo contrario, FALSE.

## <a name="cmfccolorbuttonm_benabledincustomizemode"></a><a name="m_benabledincustomizemode"></a>CMFCColorButton::m_bEnabledInCustomizeMode

Establece un botón de color en modo de personalización.

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Observaciones

Si necesita agregar un botón de color a la página de un cuadro de diálogo de personalización (o permitir que el usuario realice otra selección de color durante la personalización), habilite el botón estableciendo el `m_bEnabledInCustomizeMode` miembro en TRUE. De forma predeterminada, este miembro se establece en FALSE.

## <a name="cmfccolorbuttonondraw"></a><a name="ondraw"></a>CMFCColorButton::OnDraw

Llamado por el marco de trabajo para representar una imagen del botón.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Señala el contexto del dispositivo que se utiliza para representar la imagen del botón.

*Rect*<br/>
[en] Rectángulo que limita el botón.

*uiState*<br/>
[en] Especifica el estado visual del botón.

### <a name="remarks"></a>Observaciones

Invalide este método para personalizar el proceso de representación.

## <a name="cmfccolorbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCColorButton::OnDrawBorder

Llamado por el marco de trabajo para mostrar el borde del botón.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Señala el contexto del dispositivo utilizado para dibujar el borde.

*rectClient*<br/>
[en] Rectángulo en el contexto del dispositivo especificado por el parámetro *pDC* que define los límites del botón que se va a dibujar.

*uiState*<br/>
[en] Especifica el estado visual del botón.

### <a name="remarks"></a>Observaciones

Reemplace esta función para personalizar la apariencia del borde del botón de color.

## <a name="cmfccolorbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCColorButton::OnDrawFocusRect

Llamado por el marco de trabajo para mostrar un rectángulo de foco cuando el botón tiene el foco.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Apunta al contexto del dispositivo utilizado para dibujar el rectángulo de enfoque.

*rectClient*<br/>
[en] Rectángulo en el contexto del dispositivo especificado por el parámetro *pDC* que define los límites del botón.

### <a name="remarks"></a>Observaciones

Invalide este método para personalizar la apariencia del rectángulo de foco.

## <a name="cmfccolorbuttononshowcolorpopup"></a><a name="onshowcolorpopup"></a>CMFCColorButton::OnShowColorPopup

Se llama antes de que se muestre la barra de color emergente.

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbuttonrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorButton::RebuildPalette

Inicializa el `m_pPalette` miembro de datos protegidos en la paleta especificada o en la paleta del sistema predeterminada.

```cpp
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Ppal*|[en] Puntero a una paleta lógica o NULL. Si ES NULL, se utiliza la paleta del sistema predeterminada.|

## <a name="cmfccolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCColorButton::SetColor

Especifica el color del botón.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] Un valor RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorButton::SetColorName

Especifica el nombre de un color.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] Valor RGB del color.

*strName*<br/>
[en] El nombre del color.

### <a name="remarks"></a>Observaciones

La lista de nombres de color es global por aplicación. Por consiguiente, este método transfiere sus parámetros a [CMFCColorBar::SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname).

## <a name="cmfccolorbuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorButton::SetColumnsNumber

Define el número de columnas que se muestran en la tabla de colores que se presenta al usuario durante el proceso de selección de color del usuario.

```cpp
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parámetros

*nColumns*<br/>
[en] Especifica el número de columnas.

### <a name="remarks"></a>Observaciones

El usuario puede seleccionar un color de una barra de color espopup que muestra una tabla de colores predefinidos. Utilice este método para definir el número de columnas de la tabla.

## <a name="cmfccolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorButton::SetDocumentColors

Especifica un conjunto de colores y el nombre del conjunto. El conjunto de colores se muestra mediante un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) objeto.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] Especifica la etiqueta que se mostrará con el conjunto de colores del documento.

*lstColors*<br/>
[en] Una referencia a una lista de valores RGB.

### <a name="remarks"></a>Observaciones

Un `CMFCColorButton` objeto mantiene una lista de valores RGB que se transfieren a un [CMFCColorBar clase](../../mfc/reference/cmfccolorbar-class.md) objeto. Cuando se muestra la barra de colores, estos colores se muestran en una sección especial cuya etiqueta se especifica mediante el parámetro *lpszLabel.*

## <a name="cmfccolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCColorButton::SetPalette

Especifica los colores estándar que se mostrarán en la barra de colores emergente.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parámetros

*pPalette*<br/>
[en] Puntero a una paleta de colores.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCColorButton::SizeToContent

Cambia el tamaño del control de botón para que se ajuste a su texto e imagen.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parámetros

*bCalcOnly*<br/>
[en] Si es distinto de cero, se calcula el nuevo tamaño del control de botón, pero no se cambia el tamaño real.

### <a name="return-value"></a>Valor devuelto

Objeto `CSize` que especifica un nuevo tamaño de control de botón.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCColorButton::UpdateColor

Llamado por el marco de trabajo cuando el usuario selecciona un color de la barra de color que se muestra cuando el usuario hace clic en el botón de color.

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*Color*<br/>
[en] Color seleccionado por el usuario.

### <a name="remarks"></a>Observaciones

La `UpdateColor` función cambia el color del botón seleccionado actualmente y notifica a su elemento primario mediante el envío de un mensaje de WM_COMMAND con una notificación estándar BN_CLICKED. Utilice el [CMFCColorButton::GetColor](#getcolor) método para recuperar el color seleccionado.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton (Clase)](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar Clase](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Clase CPalette](../../mfc/reference/cpalette-class.md)<br/>
[CArray (clase)](../../mfc/reference/carray-class.md)<br/>
[Clase CList](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
