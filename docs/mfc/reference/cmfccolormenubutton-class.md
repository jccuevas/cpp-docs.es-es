---
title: CMFCColorMenuButton (Clase)
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
ms.openlocfilehash: 22208aec505033d372f5a80ba2a9641b1bd15874
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367697"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton (Clase)

La `CMFCColorMenuButton` clase admite un comando de menú o un botón de barra de herramientas que inicia un cuadro de diálogo de selector de color.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|Construye un objeto `CMFCColorMenuButton`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|Activa y desactiva un botón "automático" que se coloca encima de los botones de color normales. (El botón automático estándar del sistema está etiquetado como **Automático**.)|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|Permite la visualización de colores específicos del documento en lugar de colores del sistema.|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|Habilita y deshabilita un botón "otros" que se coloca debajo de los botones de color normales. (El botón estándar del sistema "otros" está etiquetado como **Más Colores**.)|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|Permite arrancar un panel de color.|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|Recupera el color automático actual.|
|[CMFCColorMenuButton::GetColor](#getcolor)|Recupera el color del botón actual.|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|Recupera el color que corresponde a un identificador de comando especificado.|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Llamado por el marco de trabajo cuando cambia la ventana primaria.|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|Abre un cuadro de diálogo de selección de color.|
|[CMFCColorMenuButton::SetColor](#setcolor)|Establece el color del botón de color actual.|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|Establece el color del botón de menú de color especificado.|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|Establece un nuevo nombre para el color especificado.|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|Establece el número de columnas que `CMFCColorBar` muestra un objeto.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|Copia otro botón de la barra de herramientas en el botón actual.|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|Crea un cuadro de diálogo de selector de color.|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Indica si se admiten menús vacíos.|
|[CMFCColorMenuButton::OnDraw](#ondraw)|Llamado por el marco de trabajo para mostrar una imagen en un botón.|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Llamado por el `CMFCColorMenuButton` marco de trabajo antes de que un objeto se muestre en la lista de un cuadro de diálogo de personalización de la barra de herramientas.|

## <a name="remarks"></a>Observaciones

Para reemplazar el comando de menú `CMFCColorMenuButton` original o `CMFCColorMenuButton` el botón de barra de herramientas con `ReplaceButton` un objeto, cree el objeto, establezca los estilos de [clase CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) adecuados y, a continuación, llame al método de la clase [CMFCToolBar .](../../mfc/reference/cmfctoolbar-class.md) Si personaliza una barra de herramientas, llame a la [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton) método.

El cuadro de diálogo del selector de color se crea durante el procesamiento de la [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu) controlador de eventos. El controlador de eventos notifica el marco primario con un mensaje WM_COMMAND. El `CMFCColorMenuButton` objeto envía el identificador de control asignado al comando de menú original o al botón de la barra de herramientas.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear y configurar `CMFCColorMenuButton` un botón de menú de color mediante varios métodos de la clase. En el ejemplo, primero se crea un `CPalette` objeto y, a continuación, se utiliza para construir un objeto de la `CMFCColorMenuButton` clase. A `CMFCColorMenuButton` continuación, el objeto se configura habilitando sus botones automáticos y otros, y estableciendo su color y el número de columnas. Este código forma parte del [ejemplo de Word Pad.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolormenubutton.h

## <a name="cmfccolormenubuttoncmfccolormenubutton"></a><a name="cmfccolormenubutton"></a>CMFCColorMenuButton::CMFCColorMenuButton

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
[en] Un identificador de comando de botón.

*lpszText*<br/>
[en] El texto del botón.

*pPalette*<br/>
[en] Un puntero a la paleta de colores del botón.

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

El primer constructor es el constructor predeterminado. El color actual del objeto y el color automático se inicializan en negro (RGB(0, 0, 0)).

El segundo constructor inicializa el botón en el color que corresponde al identificador de comando especificado.

## <a name="cmfccolormenubuttoncopyfrom"></a><a name="copyfrom"></a>CMFCColorMenuButton::CopyFrom

Copia un [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md)-objeto derivado a otro.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[en] Botón de origen para copiar.

### <a name="remarks"></a>Observaciones

Invalide este método para copiar objetos derivados del `CMFCColorMenuButton` objeto.

## <a name="cmfccolormenubuttoncreatepopupmenu"></a><a name="createpopupmenu"></a>CMFCColorMenuButton::CreatePopupMenu

Crea un cuadro de diálogo de selector de color.

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>Valor devuelto

Objeto que representa un cuadro de diálogo de selector de color.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando el usuario presiona un botón de menú de color.

## <a name="cmfccolormenubuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorMenuButton::EnableAutomaticButton

Activa y desactiva un botón "automático" que se coloca encima de los botones de color normales. (El botón automático estándar del sistema está etiquetado como **Automático**.)

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] Especifica el texto del botón que se muestra cuando el botón se convierte en automático.

*colorAutomático*<br/>
[en] Especifica un nuevo color automático.

*bHabilitar*<br/>
[en] Especifica si el botón es automático o no.

### <a name="remarks"></a>Observaciones

El botón automático aplica el color predeterminado actual.

## <a name="cmfccolormenubuttonenabledocumentcolors"></a><a name="enabledocumentcolors"></a>CMFCColorMenuButton::EnableDocumentColors

Permite la visualización de colores específicos del documento en lugar de colores del sistema.

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] Especifica el texto del botón.

*bHabilitar*<br/>
[en] TRUE para mostrar colores específicos del documento o FALSE para mostrar los colores del sistema.

### <a name="remarks"></a>Observaciones

Utilice este método para mostrar los colores de documento actuales o los colores de la paleta del sistema cuando el usuario haga clic en un botón de menú de color.

## <a name="cmfccolormenubuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorMenuButton::EnableOtherButton

Habilita y deshabilita un botón "otros" que se coloca debajo de los botones de color normales. (El botón estándar del sistema "otros" está etiquetado como **Más Colores**.)

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] Especifica el texto del botón.

*bAltColorDlg*<br/>
[en] Especifique TRUE para `CMFCColorDialog` mostrar el cuadro de diálogo o FALSE para mostrar el cuadro de diálogo de color del sistema estándar.

*bHabilitar*<br/>
[en] Especifique TRUE para mostrar el botón "otros"; de lo contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolormenubuttonenabletearoff"></a><a name="enabletearoff"></a>CMFCColorMenuButton::EnableTearOff

Permite arrancar un panel de color.

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[en] Especifica el identificador del panel de desmontaje.

*nVertDockColumns*<br/>
[en] Especifica el número de columnas en el panel de color acoplado verticalmente mientras está en estado de desmontaje.

*nHorzDockRows*<br/>
[en] Especifica el número de filas para el panel de color acoplado horizontalmente mientras está en estado de desmontaje.

### <a name="remarks"></a>Observaciones

Llame a este método para habilitar la característica "tear-off" `CMFCColorMenuButton` para el panel de color que aparece cuando se presiona el botón.

## <a name="cmfccolormenubuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCColorMenuButton::GetAutomaticColor

Recupera el color automático actual.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de color RGB que representa el color automático actual.

### <a name="remarks"></a>Observaciones

Llame a este método para obtener el color automático establecido por [CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton).

## <a name="cmfccolormenubuttongetcolor"></a><a name="getcolor"></a>CMFCColorMenuButton::GetColor

Recupera el color del botón actual.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color del botón.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolormenubuttongetcolorbycmdid"></a><a name="getcolorbycmdid"></a>CMFCColorMenuButton::GetColorByCmdID

Recupera el color que corresponde a un identificador de comando especificado.

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>Parámetros

*uiCmdID*<br/>
[en] Un identificador de comando.

### <a name="return-value"></a>Valor devuelto

El color que corresponde al identificador de comando especificado.

### <a name="remarks"></a>Observaciones

Utilice este método cuando tenga varios botones de color en una aplicación. Cuando el usuario hace clic en un botón de color, el botón envía su identificador de comando en un mensaje de WM_COMMAND a su elemento primario. El `GetColorByCmdID` método utiliza el identificador de comando para recuperar el color correspondiente.

## <a name="cmfccolormenubuttonisemptymenuallowed"></a><a name="isemptymenuallowed"></a>CMFCColorMenuButton::IsEmptyMenuAllowed

Indica si se admiten menús vacíos.

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se permiten menús vacíos; de lo contrario, cero.

### <a name="remarks"></a>Observaciones

Los menús vacíos son compatibles de forma predeterminada. Invalide este método para cambiar este comportamiento en la clase derivada.

## <a name="cmfccolormenubuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCColorMenuButton::OnChangeParentWnd

Llamado por el marco de trabajo cuando cambia la ventana primaria.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Un puntero a la nueva ventana primaria.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolormenubuttonondraw"></a><a name="ondraw"></a>CMFCColorMenuButton::OnDraw

Llamado por el marco de trabajo para mostrar una imagen en un botón.

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
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] Rectángulo que limita el área que se va a volver a dibujar.

*pImages*<br/>
[en] Apunta a una lista de imágenes de la barra de herramientas.

*bHorz*<br/>
[en] TRUE para especificar que la barra de herramientas está en un estado acoplado horizontal; de lo contrario, FALSE. El valor predeterminado es TRUE.

*bCustomizeMode*<br/>
[en] TRUE para especificar que la aplicación está en modo de personalización; de lo contrario, FALSE. El valor predeterminado es FALSE.

*bResaltar*<br/>
[en] TRUE para especificar que el botón está resaltado; de lo contrario, FALSE. El valor predeterminado es FALSE.

*bDrawBorder*<br/>
[en] TRUE para especificar que se muestra el borde del botón; de lo contrario, FALSE. El valor predeterminado es TRUE.

*bGrayDisabledButtons*<br/>
[en] TRUE para especificar que los botones deshabilitados están atenuados (atenuados) hacia fuera; de lo contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolormenubuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCColorMenuButton::OnDrawOnCustomizeList

Llamado por el `CMFCColorMenuButton` marco de trabajo antes de que un objeto se muestre en la lista de un cuadro de diálogo de personalización de la barra de herramientas.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] Rectángulo que limita el botón que se va a dibujar.

*bSeleccionado*<br/>
[en] TRUE especifica que el botón está en estado seleccionado; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

El ancho del botón.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama `CMFCColorMenuButton` a este método cuando se muestra un objeto en el cuadro de lista durante el proceso de personalización de la barra de herramientas.

## <a name="cmfccolormenubuttonopencolordialog"></a><a name="opencolordialog"></a>CMFCColorMenuButton::OpenColorDialog

Abre un cuadro de diálogo de selección de color.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parámetros

*colorPredeterminado*<br/>
[en] El color predeterminado seleccionado en el cuadro de diálogo de color.

*colorRes*<br/>
[fuera] Devuelve el color que el usuario selecciona en el cuadro de diálogo de color.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario selecciona un nuevo color; de lo contrario, cero.

### <a name="remarks"></a>Observaciones

Cuando se hace clic en el botón de menú, llame a este método para abrir un cuadro de diálogo de color. Si el valor devuelto es distinto de cero, el color que el usuario selecciona se almacena en el parámetro *colorRes.* Utilice el [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton) método para cambiar entre el cuadro de diálogo de color estándar y el [CMFCColorDialog cuadro](../../mfc/reference/cmfccolordialog-class.md) de diálogo.

## <a name="cmfccolormenubuttonsetcolor"></a><a name="setcolor"></a>CMFCColorMenuButton::SetColor

Establece el color del botón de color actual.

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>Parámetros

*Clr*<br/>
[en] Un valor de color RGB.

*bNotificar*<br/>
[en] TRUE para aplicar el color del parámetro *clr* a cualquier botón de menú o botón de barra de herramientas asociado; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Llame a este método para cambiar el color del botón de color actual. Si el *bNotify* parámetro es distinto de cero, el color del botón correspondiente en cualquier menú emergente asociado o barra de herramientas se cambia al color especificado por *el* clr parámetro.

## <a name="cmfccolormenubuttonsetcolorbycmdid"></a><a name="setcolorbycmdid"></a>CMFCColorMenuButton::SetColorByCmdID

Establece el color del botón de menú de color especificado.

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>Parámetros

*uiCmdID*<br/>
[en] El identificador de recurso de un botón de menú de color.

*color*<br/>
[en] Un valor de color RGB.

## <a name="cmfccolormenubuttonsetcolorname"></a><a name="setcolorname"></a>CMFCColorMenuButton::SetColorName

Establece un nuevo nombre para el color especificado.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
[en] El valor RGB del color cuyo nombre cambia.

*strName*<br/>
[en] El nuevo nombre del color.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolormenubuttonsetcolumnsnumber"></a><a name="setcolumnsnumber"></a>CMFCColorMenuButton::SetColumnsNumber

Establece el número de columnas que se mostrarán en un control de selección de color [(cMFCColorBar](../../mfc/reference/cmfccolorbar-class.md) objeto).

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>Parámetros

*nColumns*<br/>
[en] El número de columnas que se van a mostrar.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar Clase](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar (Clase)](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog (Clase)](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton (Clase)](../../mfc/reference/cmfccolorbutton-class.md)
