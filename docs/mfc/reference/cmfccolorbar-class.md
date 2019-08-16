---
title: Clase CMFCColorBar
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: 25bfe3ef67fcca7708179d1a316af05b3ba49dda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505430"
---
# <a name="cmfccolorbar-class"></a>Clase CMFCColorBar

La `CMFCColorBar` clase representa una barra de control de acoplamiento que puede seleccionar colores en un documento o aplicación.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Construye un objeto `CMFCColorBar`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|Calcula los márgenes vertical y horizontal necesarios para contener los botones del control de barra de color y, a continuación, ajusta la ubicación de esos botones.|
|[CMFCColorBar::CreateControl](#createcontrol)|Crea una ventana de control de barra de colores, la adjunta `CMFCColorBar` al objeto y cambia el tamaño del control para que contenga la paleta de colores especificada.|
|[CMFCColorBar::Create](#create)|Crea una ventana de control de barra de colores y la `CMFCColorBar` adjunta al objeto.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Muestra u oculta el botón automático.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Habilita o deshabilita la presentación de un cuadro de diálogo que permite al usuario seleccionar más colores.|
|[CMFCColorBar::GetColor](#getcolor)|Recupera el color seleccionado actualmente.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Recupera el identificador de comando del control de barra de color actual.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Recupera el color que significa que un botón de color tiene el foco. es decir, el botón está *activo*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Recupera el margen horizontal, que es el espacio entre la celda de color izquierda o derecha y el límite del área cliente.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Recupera el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.|
|[CMFCColorBar::IsTearOff](#istearoff)|Indica si la barra de colores actual es acoplable.|
|[CMFCColorBar::SetColor](#setcolor)|Establece el color seleccionado actualmente.|
|[CMFCColorBar::SetColorName](#setcolorname)|Establece un nuevo nombre para el color especificado.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Establece un nuevo identificador de comando para un control de barra de colores.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Establece la lista de colores que se usan en el documento actual.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Establece el margen horizontal, que es el espacio entre la celda de color izquierda o derecha y el límite del área cliente.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Establece el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Ajusta las posiciones de los botones de color en el control de barra de colores.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Indica si la etiqueta de texto de los botones de color puede cambiar.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Indica si el objeto de control de barra de colores puede aparecer en una lista de la barra de herramientas durante el proceso de personalización.|
|[CMFCColorBar::CalcSize](#calcsize)|Lo llama el marco de trabajo como parte del proceso de cálculo del diseño.|
|[CMFCColorBar::CreatePalette](#createpalette)|Inicializa una paleta con los colores de una matriz de colores especificada.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Calcula el número de filas y columnas en la cuadrícula de un control de barra de colores.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Calcula el alto adicional que la barra de colores actual requiere para mostrar elementos de la interfaz de usuario varios, como el **otro** botón, los colores del documento, etc.|
|[CMFCColorBar::InitColors](#initcolors)|Inicializa una matriz de colores con los colores de una paleta especificada o la paleta predeterminada del sistema.|
|[CMFCColorBar::OnKey](#onkey)|Lo llama el marco de trabajo cuando un usuario presiona un botón del teclado.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Lo llama el marco de trabajo para cerrar una jerarquía de controles emergentes.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Lo llama el marco de trabajo para habilitar o deshabilitar un elemento de la interfaz de usuario de un control de barra de colores antes de que se muestre el elemento.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Abre un cuadro de diálogo de color.|
|[CMFCColorBar::Rebuild](#rebuild)|Vuelve a dibujar completamente el control de barra de color.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Establece la paleta lógica del contexto de dispositivo especificado en la paleta del botón primario del control de barra de color actual.|
|[CMFCColorBar::SetPropList](#setproplist)|Establece el `m_pWndPropList` miembro de datos protegido en el puntero especificado a un control de cuadrícula de propiedades.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Solicita a la ventana de marco que posee el control de barra de color que actualice la línea de mensaje en la barra de estado.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`m_bInternal`|Un campo booleano que determina si se procesan los eventos del mouse. Normalmente, los eventos del mouse se procesan cuando este campo es TRUE y el modo de personalización es FALSE.|
|`m_bIsEnabled`|Un valor booleano que indica si un control está habilitado.|
|`m_bIsTearOff`|Un valor booleano que indica si el control de barra de colores admite el acoplamiento.|
|`m_BoxSize`|Objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica el tamaño de una celda en una cuadrícula de barra de colores.|
|`m_bShowDocColorsWhenDocked`|Un valor booleano que indica si se deben mostrar los colores del documento cuando se acopla la barra de colores. Para obtener más información, vea [CMFCColorBar:: SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Un valor booleano que indica si se debe mostrar el cuadro de diálogo color estándar del sistema o el cuadro de diálogo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) . Para obtener más información, vea [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|[COLORREF](/windows/win32/gdi/colorref) que almacena el color automático actual. Para obtener más información, vea [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Objeto [CMAP](../../mfc/reference/cmap-class.md) que asocia un conjunto de colores RGB a sus nombres.|
|`m_colors`|[CArray](../../mfc/reference/carray-class.md) de valores [COLORREF](/windows/win32/gdi/colorref) que contiene los colores que se muestran en el control de barra de color.|
|`m_ColorSelected`|Un valor [COLORREF](/windows/win32/gdi/colorref) que es el color que el usuario ha seleccionado actualmente en el control de barra de colores.|
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) de valores [COLORREF](/windows/win32/gdi/colorref) que contiene los colores utilizados actualmente en un documento.|
|`m_nCommandID`|Entero sin signo que es el identificador de comando de un botón de color.|
|`m_nHorzMargin`|Un entero que es el margen horizontal entre los botones de color de una cuadrícula de colores.|
|`m_nHorzOffset`|Entero que es el desplazamiento horizontal al centro del botón de color. Este valor es significativo si el botón muestra texto o una imagen además de un color.|
|`m_nNumColumns`|Un entero que es el número de columnas de una cuadrícula de controles de barra de colores.|
|`m_nNumColumnsVert`|Entero que es el número de columnas de una cuadrícula de colores orientada verticalmente.|
|`m_nNumRowsHorz`|Entero que es el número de columnas de una cuadrícula de colores orientada horizontalmente.|
|`m_nRowHeight`|Un entero que es el alto de una fila de botones de color en una cuadrícula de colores.|
|`m_nVertMargin`|Un entero que es el margen vertical entre los botones de color de una cuadrícula de colores.|
|`m_nVertOffset`|Entero que es el desplazamiento vertical hasta el centro del botón de color. Este valor es significativo si el botón muestra texto o una imagen además de un color.|
|`m_Palette`|[CPalette](../../mfc/reference/cpalette-class.md) de los colores que se usan en el control de barra de color.|
|`m_pParentBtn`|Un puntero a un objeto [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) que es el elemento primario del botón actual. Este valor es significativo si el botón de color está en una jerarquía de controles de barra de herramientas o está en un control de cuadrícula de propiedades de color.|
|`m_pParentRibbonBtn`|Un puntero a un objeto [cmfcribboncolorbutton (](../../mfc/reference/cmfcribboncolorbutton-class.md) que se encuentra en la cinta de opciones y es el botón primario del botón actual. Este valor es significativo si el botón de color está en una jerarquía de controles de barra de herramientas o está en un control de cuadrícula de propiedades de color.|
|`m_pWndPropList`|Un puntero a un objeto [cmfcpropertygridctrl (](../../mfc/reference/cmfcpropertygridctrl-class.md) .|
|`m_strAutoColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el botón **automático** . Para obtener más información, vea [CMFCColorBar:: EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el botón colores del documento. Para obtener más información, vea [CMFCColorBar:: SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el botón *otros* . Para obtener más información, vea [CMFCColorBar:: EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Comentarios

Normalmente, no se crea un `CMFCColorBar` objeto directamente. En su lugar, la [clase CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (que se usa en los menús y las barras de herramientas) `CMFCColorBar` o la [clase CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) crea el objeto.

La `CMFCColorBar` clase proporciona la funcionalidad siguiente:

- Ajusta automáticamente la lista de colores del documento.

- Guarda y restaura su estado, junto con el estado del documento.

- Administra el botón "automático".

- Usa el control de [clase CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) para seleccionar un color personalizado.

- Admite un estado "recortar" (si se crea mediante la [clase CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)).

Para incorporar la `CMFCColorBar` funcionalidad a la aplicación:

1. Cree un botón de menú normal y asígnele un identificador, por ejemplo ID_CHAR_COLOR.

1. En la clase de ventana de marco, invalide el método [CFrameWndEx:: OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) y reemplace el botón de menú normal por un objeto de [clase CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (llamando a [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Establezca todos los estilos y habilite o deshabilite las características del `CMFCColorBar` objeto durante la creación de la [clase CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) . El `CMFCColorMenuButton` objeto crea dinámicamente el `CMFCColorBar` objeto después de que el marco `CreatePopupMenu` de trabajo llame al método.

Cuando el usuario hace clic en un botón de control de barra de colores, `ON_COMMAND` el marco de trabajo usa la macro para notificar al elemento primario del control de barra de color. En la macro, el parámetro de identificador de comando es el valor que asignó al botón de control de barra de color en el paso 1 (ID_CHAR_COLOR en este ejemplo). Para obtener más información, vea la clase [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md), la clase [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md), la clase [CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md), la clase [CFrameWndEx](../../mfc/reference/cframewndex-class.md)y las clases de [clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar una barra de colores mediante el uso de `CMFCColorBar` varios métodos en la clase. Los métodos establecen los márgenes horizontal y vertical, habilitan el otro botón, crean una ventana de control de barra de colores y establecen el color seleccionado actualmente. Este ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcolorbar. h

##  <a name="adjustlocations"></a>CMFCColorBar::AdjustLocations

Ajusta las posiciones de los botones de color en el control de barra de colores.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método durante el procesamiento del mensaje de WM_SIZE.

##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels

Indica si la etiqueta de texto de los botones de color puede cambiar.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre es FALSE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método siempre devuelve FALSE, lo que significa que no se pueden modificar las etiquetas de texto. Invalide este método para habilitar la modificación de etiquetas de texto.

##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList

Indica si el objeto de control de barra de colores puede aparecer en una lista de la barra de herramientas durante el proceso de personalización.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre es TRUE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método siempre devuelve TRUE, lo que significa que el marco de trabajo puede mostrar el control de barra de color durante el proceso de personalización. Invalide este método para implementar un comportamiento diferente.

##  <a name="calcsize"></a>  CMFCColorBar::CalcSize

Lo llama el marco de trabajo como parte del proceso de cálculo del diseño.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parámetros

*bVertDock*<br/>
de TRUE para especificar que el control de barra de color está acoplado verticalmente. FALSE para especificar que el control de barra de color está acoplado horizontalmente.

### <a name="return-value"></a>Valor devuelto

Tamaño de la matriz de botones de color de un control de barra de colores.

##  <a name="cmfccolorbar"></a>  CMFCColorBar::CMFCColorBar

Construye un objeto `CMFCColorBar`.

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>Parámetros

*colors*<br/>
de Matriz de colores que el marco muestra en el control de barra de colores.

*color*<br/>
de El color seleccionado inicialmente.

*lpszAutoColor*<br/>
de La etiqueta de texto del botón de color *automático* (predeterminado) o null.

La etiqueta estándar del botón automático es **automática**.

*lpszOtherColor*<br/>
de La etiqueta de texto del botón *otros* , que muestra más opciones de color o null.

La etiqueta estándar para el otro botón es **más colores..** ..

*lpszDocColors*<br/>
de La etiqueta de texto del botón colores del documento. La paleta colores del documento muestra todos los colores que el documento utiliza actualmente.

*lstDocColors*<br/>
de Una lista de colores que el documento utiliza actualmente.

*nColumns*<br/>
de El número de columnas que tiene la matriz de colores.

*nRowsDockHorz*<br/>
de Número de filas que tiene la barra de colores cuando está acoplada horizontalmente.

*nColDockVert*<br/>
de El número de columnas que tiene la barra de colores cuando está acoplada verticalmente.

*colorAutomatic*<br/>
de El color predeterminado que el marco de trabajo aplica al hacer clic en el botón automático.

*nCommandID*<br/>
de IDENTIFICADOR del comando de control de barra de color.

*pParentBtn*<br/>
de Un puntero a un botón primario.

*src*<br/>
de Objeto existente `CMFCColorBar` que se va a copiar en el `CMFCColorBar` nuevo objeto.

*uiCommandID*<br/>
de IDENTIFICADOR del comando.

##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize

Calcula los márgenes vertical y horizontal necesarios para contener los botones del control de barra de color y ajusta la ubicación de esos botones.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*bSquareButtons*|de TRUE para especificar que la forma de los botones en un control de barra de color es cuadrada; en caso contrario, FALSE. El valor predeterminado es TRUE.|
|*bCenterButtons*|de TRUE para especificar que el contenido de la superficie de un botón de control de barra de colores está centrado; en caso contrario, FALSE. El valor predeterminado es TRUE.|

### <a name="remarks"></a>Comentarios

##  <a name="create"></a>  CMFCColorBar::Create

Crea una ventana de control de barra de colores y la `CMFCColorBar` adjunta al objeto.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
de Puntero a la ventana primaria.

*dwStyle*<br/>
de Combinación bit a bit (o) de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
de IDENTIFICADOR del comando.

*pPalette*<br/>
de Puntero a una paleta de colores. El valor predeterminado es NULL.

*nColumns*<br/>
de El número de columnas del control de barra de color. El valor predeterminado es 0.

*nRowsDockHorz*<br/>
de Número de filas del control de barra de color cuando se acopla horizontalmente. El valor predeterminado es 0.

*nColDockVert*<br/>
de El número de columnas del control de barra de color cuando está acoplada verticalmente. El valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para construir un `CMFCColorBar` objeto, llame al constructor de clase y, a continuación, a este método. El `Create` método crea el control de Windows e inicializa una lista de colores.

##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl

Crea una ventana de control de barra de colores, la adjunta `CMFCColorBar` al objeto y cambia el tamaño de la ventana del control para que contenga la paleta de colores especificada.

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
de Puntero a la ventana primaria. No puede ser nulo.

*rect*<br/>
de Rectángulo delimitador que especifica dónde se debe dibujar el control de barra de color.

*nID*<br/>
de IDENTIFICADOR del control.

*nColumns*<br/>
de Número ideal de columnas en el control de barra de color. Este método modifica ese número para ajustarse a la paleta de colores especificada. El valor predeterminado es-1, lo que significa que no se especifica este parámetro.

*pPalette*<br/>
de Puntero a una paleta de colores o NULL. Si este parámetro es NULL, este método calcula el tamaño del control de barra de color como si se hubieran 20 colores especificados. El valor predeterminado es NULL.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se ejecuta correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método usa los parámetros *Rect*, *nColumns*y *pPalette* para calcular el número o las filas y columnas adecuados en el control de barra de color y, a continuación, llama al método [CMFCColorBar:: Create](#create) .

##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette

Inicializa una paleta con los colores de una matriz de colores especificada.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*arColors*|de Matriz de colores.|
|*palette*|de Una paleta de colores.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton

Muestra u oculta el botón automático.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
de La etiqueta de texto del botón de color *automático* (predeterminado) o null.

La etiqueta estándar del botón automático es **automática**.

*colorAutomatic*<br/>
de El color predeterminado que el marco de trabajo aplica al hacer clic en el botón automático.

*bEnable*<br/>
de TRUE para habilitar el botón automático; FALSE para deshabilitar el botón automático. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

Si el parámetro *lpszLabel* es null o el parámetro *bEnable* es false, se elimina la etiqueta de texto del botón automático.

##  <a name="enableotherbutton"></a>  CMFCColorBar::EnableOtherButton

Habilita o deshabilita la presentación de un cuadro de diálogo que permite al usuario seleccionar más colores.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
de La etiqueta de texto del botón *otros* , que muestra más opciones de color o null.

La etiqueta estándar para este botón es **más colores..** ..

*bAltColorDlg*<br/>
de TRUE para mostrar el cuadro de diálogo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ; FALSE para mostrar el cuadro de diálogo [CColorDialog](../../mfc/reference/ccolordialog-class.md) estándar. El valor predeterminado es TRUE.

*bEnable*<br/>
de TRUE para habilitar el botón; FALSE para deshabilitar el botón. El valor predeterminado es TRUE.

##  <a name="getcolor"></a>  CMFCColorBar::GetColor

Recupera el color seleccionado actualmente.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color seleccionado actualmente.

##  <a name="getcolorgridsize"></a>  CMFCColorBar::GetColorGridSize

Calcula el número de filas y columnas en la cuadrícula de un control de barra de colores.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*bVertDock*|de TRUE para realizar el cálculo de un control de barra de colores acoplado verticalmente. de lo contrario, realice el cálculo para un control acoplado horizontalmente.|

### <a name="return-value"></a>Valor devuelto

Un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) cuyo `cx` componente contiene el número de columnas y cuyo `cy` componente contiene el número de filas.

##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID

Recupera el identificador de comando del control de barra de color actual.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR de comando.

### <a name="remarks"></a>Comentarios

Cuando el usuario selecciona un nuevo color, el marco de trabajo envía el identificador de comando en un mensaje WM_COMMAND para notificar `CMFCColorBar` al elemento primario del objeto.

##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight

Calcula el alto adicional que la barra de colores actual requiere para mostrar los elementos de la interfaz de usuario varios, como los **demás** colores del botón o del documento.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*nNumColumns*|de Si el control de barra de colores contiene los colores del documento, el número de columnas que se mostrarán en la cuadrícula de los colores del documento. De lo contrario, este valor no se utiliza.|

### <a name="return-value"></a>Valor devuelto

Alto adicional calculado que se requiere.

##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor

Recupera el color que significa que un botón de color tiene el foco. es decir, el botón está *activo*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Valor devuelto

Valor RGB.

### <a name="remarks"></a>Comentarios

##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin

Recupera el margen horizontal, que es el espacio entre la celda de color izquierda o derecha y el límite del área cliente.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Valor devuelto

Margen horizontal.

##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin

Recupera el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Valor devuelto

Margen vertical.

##  <a name="initcolors"></a>  CMFCColorBar::InitColors

Inicializa una matriz de colores con los colores de una paleta especificada o con la paleta predeterminada del sistema.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*pPalette*|de Un puntero a un objeto Palette o NULL. Si este parámetro es NULL, este método utiliza la paleta predeterminada del sistema operativo.|
|*arColors*|de Matriz de colores.|

### <a name="return-value"></a>Valor devuelto

Número de elementos de la matriz de colores.

##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff

Indica si la barra de colores actual es acoplable.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el control de la barra de color actual es acoplable; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si el control de barra de color es acoplable, se puede desacoplar de una barra de controles y acoplarlo en otra ubicación.

##  <a name="onkey"></a>  CMFCColorBar::OnKey

Lo llama el marco de trabajo cuando un usuario presiona un botón del teclado.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parámetros

*nChar*<br/>
de Código de tecla virtual de la tecla que un usuario presionó.

### <a name="return-value"></a>Valor devuelto

TRUE si este método procesa la clave especificada; en caso contrario, FALSE.

##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand

Lo llama el marco de trabajo para cerrar una jerarquía de controles emergentes.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*pButton*|de Puntero a un control que reside en una barra de herramientas.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI

Lo llama el marco de trabajo para habilitar o deshabilitar un elemento de la interfaz de usuario de un control de barra de colores antes de que se muestre el elemento.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
de Puntero a una ventana que contiene un elemento de la interfaz de usuario que se va a actualizar.

*bDisableIfNoHndler*<br/>
de TRUE para deshabilitar el elemento de la interfaz de usuario si no hay ningún controlador definido en un mapa de mensajes; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Cuando un usuario de la aplicación hace clic en un elemento de la interfaz de usuario, el elemento debe saber si debe mostrarse como habilitado o deshabilitado. El destino del mensaje de comando proporciona esta información implementando un controlador de comandos ON_UPDATE_COMMAND_UI. Utilice este método para ayudar a procesar el comando. Para obtener más información, vea [CCmdUI (clase](../../mfc/reference/ccmdui-class.md)).

##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog

Abre un cuadro de diálogo de color.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parámetros

*colorDefault*<br/>
de Color que está seleccionado de forma predeterminada cuando se abre el cuadro de diálogo color.

*colorRes*<br/>
enuncia Color seleccionado por el usuario.

### <a name="return-value"></a>Valor devuelto

TRUE si el usuario seleccionó un color; FALSE si el usuario canceló el cuadro de diálogo de color.

### <a name="remarks"></a>Comentarios

##  <a name="rebuild"></a>  CMFCColorBar::Rebuild

Vuelve a dibujar completamente el control de barra de color.

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette

Establece la paleta lógica del contexto de dispositivo especificado en la paleta del botón primario del control de barra de color actual.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*pDC*|de Puntero al contexto de dispositivo del botón primario del control de barra de color actual.|

### <a name="return-value"></a>Valor devuelto

Puntero a la paleta que se reemplaza por la paleta del botón primario del control de barra de color actual.

##  <a name="setcolor"></a>  CMFCColorBar::SetColor

Establece el color seleccionado actualmente.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
de Valor de color RGB.

##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName

Establece un nuevo nombre para el color especificado.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
de Valor RGB de un color.

*strName*<br/>
de Nuevo nombre para el color especificado.

### <a name="remarks"></a>Comentarios

Este método cambia el nombre del color especificado en todos los `CMFCColorBar` objetos de la aplicación.

##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID

Establece un nuevo identificador de comando para un control de barra de colores.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parámetros

*nCommandID*<br/>
de IDENTIFICADOR de comando.

### <a name="remarks"></a>Comentarios

Llame a este método para modificar el identificador de comando de un control de barra de color y para notificar a la ventana primaria del control que el identificador ha cambiado.

##  <a name="setdocumentcolors"></a>  CMFCColorBar::SetDocumentColors

Establece la lista de colores que se usan en el documento actual.

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszCaption*<br/>
de Título que se muestra cuando el control de barra de color no está acoplado.

*lstDocColors*<br/>
de Una lista de colores que reemplaza los colores del documento actual.

*bShowWhenDocked*<br/>
de TRUE para mostrar los colores del documento cuando el control de barra de color está acoplado; en caso contrario, FALSE. El valor predeterminado es FALSE.

### <a name="remarks"></a>Comentarios

Los *colores del documento* son los colores que se usan actualmente en un documento. El marco de trabajo mantiene automáticamente una lista de colores del documento, pero puede usar este método para modificar la lista.

##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin

Establece el margen horizontal, que es el espacio entre la celda de color izquierda o derecha y el límite del área cliente.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parámetros

*nHorzMargin*<br/>
de Margen horizontal, en píxeles.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el constructor [CMFCColorBar:: CMFCColorBar](#cmfccolorbar) establece el margen horizontal en 4 píxeles.

##  <a name="setproplist"></a>  CMFCColorBar::SetPropList

Establece el `m_pWndPropList` miembro de datos protegido en el puntero especificado a un control de cuadrícula de propiedades.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*pWndList*|de Puntero al objeto de control de cuadrícula de propiedades.|

##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin

Establece el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parámetros

*nVertMargin*<br/>
de Margen vertical, en píxeles.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el constructor [CMFCColorBar:: CMFCColorBar](#cmfccolorbar) establece el margen vertical en 4 píxeles.

##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString

Solicita a la ventana de marco que posee el control de barra de color que actualice la línea de mensaje en la barra de estado.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parámetros

*uiCmdId*<br/>
de IDENTIFICADOR de comando. (Este parámetro se pasa por alto).

### <a name="remarks"></a>Comentarios

Este método envía el mensaje WM_SETMESSAGESTRING al propietario del control de barra de color.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
