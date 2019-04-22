---
title: CMFCColorMenuButton (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
ms.openlocfilehash: 5fccfbca9fe8c31070f3eb9f208c09cb3722b9b9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780228"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton (clase)

La `CMFCColorMenuButton` clase admite un comando de menú o un botón de barra de herramientas que se inicia un cuadro de diálogo Selector de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Construye un objeto `CMFCColorMenuButton`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Habilita y deshabilita un botón "automático" que está situado encima de los botones de color normal. (El botón automático estándar del sistema tiene la etiqueta **automática**.)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Permite mostrar colores específica del documento en lugar de los colores del sistema.|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Habilita y deshabilita un botón "otro" que se coloca debajo de los botones de color normal. (El sistema estándar "other" botón se etiqueta como **más colores**.)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Permite la capacidad de arrancar un panel de color.|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Recupera el color automático actual.|
|[CMFCColorMenuButton::GetColor](#getcolor)|Recupera el color del botón actual.|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Recupera el color que se corresponde con un identificador de comando especificado.|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Lo llama el marco cuando cambia la ventana primaria.|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Abre un cuadro de diálogo de selección de color.|
|[CMFCColorMenuButton::SetColor](#setcolor)|Establece el color del botón de color actual.|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Establece el color del botón de menú de color especificado.|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Establece un nuevo nombre para el color especificado.|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Establece el número de columnas que se muestran mediante un `CMFCColorBar` objeto.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Copia otro botón de barra de herramientas en el botón actual.|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Crea un cuadro de diálogo Selector de color.|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Indica si se admiten menús vacíos.|
|[CMFCColorMenuButton::OnDraw](#ondraw)|Lo llama el marco de trabajo para mostrar una imagen en un botón.|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Lo llama el marco antes un `CMFCColorMenuButton` objeto se muestra en la lista de un cuadro de diálogo de personalización de barra de herramientas.|

## <a name="remarks"></a>Comentarios

Para reemplazar el botón de barra de herramientas o comandos de menú original con un `CMFCColorMenuButton` , cree el `CMFCColorMenuButton` objeto, establecer cualquier adecuado [CMFCColorBar (clase)](../../mfc/reference/cmfccolorbar-class.md) estilos y, a continuación, llame el `ReplaceButton` método de la [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md) clase. Si personaliza una barra de herramientas, llame a la [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) método.

El cuadro de diálogo Selector de color se crea durante el procesamiento de la [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) controlador de eventos. El controlador de eventos notifica al marco primario con un mensaje WM_COMMAND. La `CMFCColorMenuButton` objeto envía el identificador de control que se asigna en el botón de barra de herramientas o comandos de menú original.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear y configurar un botón de menú de color mediante distintos métodos en el `CMFCColorMenuButton` clase. En el ejemplo, un `CPalette` objeto se crea por primera vez y, a continuación, se usa para construir un objeto de la `CMFCColorMenuButton` clase. El `CMFCColorMenuButton` habilitar otros botones y sus automáticos y establecer su color y el número de columnas, a continuación, configura el objeto. Este código forma parte de la [ejemplo de WordPad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolormenubutton.h

##  <a name="cmfccolormenubutton"></a>  CMFCColorMenuButton::CMFCColorMenuButton

Construye un objeto `CMFCColorMenuButton`.

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parámetros

*uiCmdID*<br/>
[in] Un identificador de comando del botón.

*lpszText*<br/>
[in] El texto del botón.

*pPalette*<br/>
[in] Un puntero a la paleta de colores del botón.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

El primer constructor es el constructor predeterminado. El color del objeto actual y el color automático se inicializan en negro (RGB (0, 0, 0)).

El segundo constructor inicializa el botón para el color que se corresponde con el identificador de comando especificado.

##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom

Copia una [CMFCToolBarMenuButton (clase)](../../mfc/reference/cmfctoolbarmenubutton-class.md)-objeto derivado a otro.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[in] Botón de origen para copiar.

### <a name="remarks"></a>Comentarios

Invalide este método para copiar los objetos que se derivan los `CMFCColorMenuButton` objeto.

##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu

Crea un cuadro de diálogo Selector de color.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Valor devuelto

Un objeto que representa un cuadro de diálogo Selector de color.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando el usuario presiona un botón de menú de color.

##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton

Habilita y deshabilita un botón "automático" que está situado encima de los botones de color normal. (El botón automático estándar del sistema tiene la etiqueta **automática**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[in] Especifica el texto del botón que se muestra cuando el botón se convierte en automático.

*colorAutomatic*<br/>
[in] Especifica un nuevo color automático.

*bEnable*<br/>
[in] Especifica si el botón es automático o no.

### <a name="remarks"></a>Comentarios

El botón automático aplica el color predeterminado actual.

##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors

Permite mostrar colores específica del documento en lugar de los colores del sistema.

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[in] Especifica el texto del botón.

*bEnable*<br/>
[in] TRUE para mostrar colores específicos del documento o FALSE para mostrar los colores del sistema.

### <a name="remarks"></a>Comentarios

Utilice este método para mostrar los colores del documento actual o los colores de paleta del sistema cuando el usuario hace clic en un botón de menú de color.

##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton

Habilita y deshabilita un botón "otro" que se coloca debajo de los botones de color normal. (El sistema estándar "other" botón se etiqueta como **más colores**.)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[in] Especifica el texto del botón.

*bAltColorDlg*<br/>
[in] Especifique TRUE para mostrar el `CMFCColorDialog` cuadro de diálogo o FALSE para mostrar el cuadro de diálogo de colores estándar del sistema.

*bEnable*<br/>
[in] Especifique "true" para mostrar el botón "other"; en caso contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff

Permite la capacidad de arrancar un panel de color.

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[in] Especifica el identificador para el panel desplazable.

*nVertDockColumns*<br/>
[in] Especifica el número de columnas en el panel acoplado verticalmente color mientras esté en estado desplazable.

*nHorzDockRows*<br/>
[in] Especifica el número de filas del panel acoplado horizontalmente color mientras esté en estado desplazable.

### <a name="remarks"></a>Comentarios

Llame a este método para habilitar la característica "divisibles" para el panel de color que aparece cuando el `CMFCColorMenuButton` está presionado.

##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor

Recupera el color automático actual.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de color RGB que representa el color automático actual.

### <a name="remarks"></a>Comentarios

Llame a este método para obtener el color automático establecido por [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).

##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor

Recupera el color del botón actual.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color del botón.

### <a name="remarks"></a>Comentarios

##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID

Recupera el color que se corresponde con un identificador de comando especificado.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>Parámetros

*uiCmdID*<br/>
[in] Un identificador de comando.

### <a name="return-value"></a>Valor devuelto

El color que se corresponde con el identificador de comando especificado.

### <a name="remarks"></a>Comentarios

Utilice este método cuando haya varios botones de color en una aplicación. Cuando el usuario hace clic en un botón de color, el botón envía su identificador de comando en un mensaje WM_COMMAND a su elemento primario. El `GetColorByCmdID` método usa el identificador de comando para recuperar el color correspondiente.

##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed

Indica si se admiten menús vacíos.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se permiten los menús vacíos; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Se admiten los menús vacíos de forma predeterminada. Invalide este método para cambiar este comportamiento en una clase derivada.

##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd

Lo llama el marco cuando cambia la ventana primaria.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[in] Un puntero a la nueva ventana primaria.

### <a name="remarks"></a>Comentarios

##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw

Lo llama el marco de trabajo para mostrar una imagen en un botón.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz=TRUE,
    BOOL bCustomizeMode=FALSE,
    BOOL bHighlight=FALSE,
    BOOL bDrawBorder=TRUE,
    BOOL bGrayDisabledButtons=TRUE);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.

*rect*<br/>
[in] Un rectángulo que delimita el área que se vuelva a dibujar.

*pImages*<br/>
[in] Apunta a una lista de imágenes de barra de herramientas.

*bHorz*<br/>
[in] TRUE para especificar que la barra de herramientas está en un estado acoplado horizontal; en caso contrario, FALSE. El valor predeterminado es TRUE.

*bCustomizeMode*<br/>
[in] TRUE para especificar que la aplicación está en modo de personalización; en caso contrario, FALSE. El valor predeterminado es FALSE.

*bHighlight*<br/>
[in] TRUE para especificar que el botón está resaltado; en caso contrario, FALSE. El valor predeterminado es FALSE.

*bDrawBorder*<br/>
[in] TRUE para especificar que se muestra el borde del botón; en caso contrario, FALSE. El valor predeterminado es TRUE.

*bGrayDisabledButtons*<br/>
[in] TRUE para especificar que los botones deshabilitados están resaltados en gris (atenuado) en caso contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList

Lo llama el marco antes un `CMFCColorMenuButton` objeto se muestra en la lista de un cuadro de diálogo de personalización de barra de herramientas.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.

*rect*<br/>
[in] Un rectángulo que delimita el botón va a dibujar.

*bSelected*<br/>
[in] TRUE especifica que el botón está en estado seleccionado. en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

El ancho del botón.

### <a name="remarks"></a>Comentarios

Este método se llama el marco de trabajo cuando un `CMFCColorMenuButton` objeto se muestra en el cuadro de lista durante el proceso de personalización de la barra de herramientas.

##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog

Abre un cuadro de diálogo de selección de color.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parámetros

*colorDefault*<br/>
[in] El color predeterminado que está seleccionado en el cuadro de diálogo color.

*colorRes*<br/>
[out] Devuelve el color que el usuario selecciona en el cuadro de diálogo color.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario selecciona un nuevo color; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Cuando se hace clic en el botón de menú, llame a este método para abrir un cuadro de diálogo color. Si el valor devuelto es distinto de cero, el color que el usuario selecciona se almacena en el *colorRes* parámetro. Use la [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) método para cambiar entre el cuadro de diálogo de colores estándar y la [CMFCColorDialog (clase)](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo.

##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor

Establece el color del botón de color actual.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>Parámetros

*clr*<br/>
[in] Un valor de color RGB.

*bNotify*<br/>
[in] TRUE para aplicar el *clr* color de parámetro a cualquier botón de menú asociado o un botón de barra de herramientas; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a este método para cambiar el color del botón de color actual. Si el *bNotify* parámetro es distinto de cero, el color del botón correspondiente en cualquier menú emergente asociado o la barra de herramientas cambia el color especificado por el *clr* parámetro.

##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID

Establece el color del botón de menú de color especificado.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>Parámetros

*uiCmdID*<br/>
[in] El identificador de recurso de un botón de menú de color.

*color*<br/>
[in] Un valor de color RGB.

##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName

Establece un nuevo nombre para el color especificado.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
[in] El valor RGB del color cuyo nombre cambia.

*strName*<br/>
[in] El nuevo nombre del color.

### <a name="remarks"></a>Comentarios

##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber

Establece el número de columnas que desea mostrar en un control de selección de color ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) objeto).

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parámetros

*nColumns*<br/>
[in] El número de columnas para mostrar.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar (clase)](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog (clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton (clase)](../../mfc/reference/cmfccolorbutton-class.md)
