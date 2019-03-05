---
title: CMFCColorBar (clase)
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
ms.openlocfilehash: f1f7610fc315da65145798058fdcf9752e7873d0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283259"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar (clase)

La `CMFCColorBar` clase representa una barra de control de acoplamiento que puede seleccionar los colores en un documento o aplicación.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Construye un objeto `CMFCColorBar`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|Calcula los márgenes horizontales y verticales que son necesarias para contener los botones del control de barra de colores y, a continuación, ajusta la ubicación de estos botones.|
|[CMFCColorBar::CreateControl](#createcontrol)|Crea una ventana de control de barra de colores, que se conecta a la `CMFCColorBar` de objetos y cambia el tamaño del control para que contenga la paleta de colores especificada.|
|[CMFCColorBar::Create](#create)|Crea una ventana de control de barra de colores y la conecta a la `CMFCColorBar` objeto.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Muestra u oculta el botón automático.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Habilita o deshabilita la presentación de un cuadro de diálogo que permite al usuario seleccionar más colores.|
|[CMFCColorBar::GetColor](#getcolor)|Recupera el color seleccionado actualmente.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Recupera el identificador de comando del control de barra de color actual.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Recupera el color que indica que un botón en color tiene el foco; es decir, el botón *hot*.|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Recupera el margen horizontal, que es el espacio entre la izquierda o celda de color a la derecha y el límite del área cliente.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Recupera el margen vertical, que es el espacio entre la parte superior o celda de color de la parte inferior y el límite del área cliente.|
|[CMFCColorBar::IsTearOff](#istearoff)|Indica si la barra de colores actual es acoplable.|
|[CMFCColorBar::SetColor](#setcolor)|Establece el color que está seleccionado actualmente.|
|[CMFCColorBar::SetColorName](#setcolorname)|Establece un nuevo nombre para un color especificado.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Establece un nuevo identificador de comando para un control de barra de color.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Establece la lista de colores que se usan en el documento actual.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Establece el margen horizontal, que es el espacio entre la izquierda o celda de color a la derecha y el límite del área cliente.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Establece el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Ajusta las posiciones de los botones de color en el control de barra de color.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Indica si se puede cambiar la etiqueta de texto de los botones de color.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Indica si el objeto de control de barra de colores puede aparecer en una lista de la barra de herramientas durante el proceso de personalización.|
|[CMFCColorBar::CalcSize](#calcsize)|Lo llama el marco de trabajo como parte del proceso de cálculo de diseño.|
|[CMFCColorBar::CreatePalette](#createpalette)|Inicializa una paleta con los colores de una matriz de colores especificada.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Calcula el número de filas y columnas en la cuadrícula de un control de barra de colores.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Calcula el alto adicional que requiere la barra de colores actual para mostrar los elementos de la interfaz de usuario, como el **otros** botón, los colores del documento y así sucesivamente.|
|[CMFCColorBar::InitColors](#initcolors)|Inicializa una matriz de colores con los colores de una paleta especificada o la paleta predeterminada del sistema.|
|[CMFCColorBar::OnKey](#onkey)|Lo llama el marco cuando el usuario presiona un botón de teclado.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Lo llama el marco de trabajo para cerrar una jerarquía de controles de menú emergente.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Lo llama el marco de trabajo para habilitar o deshabilitar un elemento de interfaz de usuario de un control de barra de colores antes de que se muestra el elemento.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Se abre un cuadro de diálogo color.|
|[CMFCColorBar::Rebuild](#rebuild)|Completamente vuelve a dibujar el control de barra de color.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Establece la paleta lógica del contexto de dispositivo especificado en la paleta del botón primario del control de barra de color actual.|
|[CMFCColorBar::SetPropList](#setproplist)|Establece el `m_pWndPropList` protegido el puntero especificado a un control de cuadrícula de propiedades de miembro de datos.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Solicitudes de la ventana de marco que posee el control de barra de colores para actualizar la línea del mensaje en la barra de estado.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|`m_bInternal`|Un campo booleano que determina si se procesan los eventos del mouse. Normalmente, se procesan los eventos del mouse cuando este campo es TRUE y el modo de personalización es FALSE.|
|`m_bIsEnabled`|Un valor booleano que indica si un control está habilitado.|
|`m_bIsTearOff`|Un valor booleano que indica si el control de barra de color admite el acoplamiento.|
|`m_BoxSize`|Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica el tamaño de una celda en una cuadrícula de la barra de colores.|
|`m_bShowDocColorsWhenDocked`|Un valor booleano que indica si se muestran los colores del documento cuando se acopla la barra de colores. Para obtener más información, consulte [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Un valor booleano que indica si se debe mostrar el cuadro de diálogo de colores estándar del sistema o el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo. Para obtener más información, consulte [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|Un [COLORREF](/windows/desktop/gdi/colorref) que almacena el color automático actual. Para obtener más información, consulte [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Un [CMap](../../mfc/reference/cmap-class.md) los colores con sus nombres de objeto que se asocia un conjunto de RGB.|
|`m_colors`|Un [CArray](../../mfc/reference/carray-class.md) de [COLORREF](/windows/desktop/gdi/colorref) valores que contiene los colores que se muestran en el control de barra de color.|
|`m_ColorSelected`|Un [COLORREF](/windows/desktop/gdi/colorref) valor que es el color que el usuario ha seleccionado actualmente en el control de barra de color.|
|`m_lstDocColors`|Un [CList](../../mfc/reference/clist-class.md) de [COLORREF](/windows/desktop/gdi/colorref) valores que contiene los colores que se usan actualmente en un documento.|
|`m_nCommandID`|Entero sin signo que es el identificador de comando de un botón de color.|
|`m_nHorzMargin`|Un entero que es el margen horizontal entre los botones de color en una cuadrícula de colores.|
|`m_nHorzOffset`|Un entero que es el desplazamiento horizontal en el centro del botón de color. Este valor es significativo si el botón muestra texto o una imagen, además de un color.|
|`m_nNumColumns`|Un entero que es el número de columnas en una cuadrícula de control de barra de colores de colores.|
|`m_nNumColumnsVert`|Un entero que es el número de columnas en una cuadrícula de orientación vertical de colores.|
|`m_nNumRowsHorz`|Un entero que es el número de columnas en una cuadrícula horizontal de colores.|
|`m_nRowHeight`|Un entero que es el alto de una fila de botones de color en una cuadrícula de colores.|
|`m_nVertMargin`|Un entero que es el margen vertical entre los botones de color en una cuadrícula de colores.|
|`m_nVertOffset`|Un entero que es el desplazamiento vertical en el centro del botón de color. Este valor es significativo si el botón muestra texto o una imagen, además de un color.|
|`m_Palette`|Un [CPalette](../../mfc/reference/cpalette-class.md) de los colores que se usan en el control de barra de color.|
|`m_pParentBtn`|Un puntero a un [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) objeto que es el elemento primario del botón actual. Este valor es significativo si el botón de color está en una jerarquía de controles de barra de herramientas o está en un control de cuadrícula de propiedad de color.|
|`m_pParentRibbonBtn`|Un puntero a un [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) objeto que está en la cinta de opciones y el botón primario del botón actual. Este valor es significativo si el botón de color está en una jerarquía de controles de barra de herramientas o está en un control de cuadrícula de propiedad de color.|
|`m_pWndPropList`|Un puntero a un [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) objeto.|
|`m_strAutoColor`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el **automática** botón. Para obtener más información, consulte [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el botón de colores del documento. Para obtener más información, consulte [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el *otros* botón. Para obtener más información, consulte [CMFCColorBar::EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Comentarios

Por lo general, no cree un `CMFCColorBar` objeto directamente. En su lugar, el [CMFCColorMenuButton (clase)](../../mfc/reference/cmfccolormenubutton-class.md) (usado en menús y barras de herramientas) o el [CMFCColorButton (clase)](../../mfc/reference/cmfccolorbutton-class.md) crea el `CMFCColorBar` objeto.

La `CMFCColorBar` clase proporciona la funcionalidad siguiente:

- La lista de colores del documento se ajusta automáticamente.

- Guarda y restaura su estado, junto con el estado del documento.

- Administra el botón "automático".

- Usa el [CMFCColorPickerCtrl (clase)](../../mfc/reference/cmfccolorpickerctrl-class.md) control para seleccionar un color personalizado.

- Es compatible con un estado "divisibles" (si se ha creado mediante el uso de la [CMFCColorMenuButton (clase)](../../mfc/reference/cmfccolormenubutton-class.md)).

Para incorporar la `CMFCColorBar` funcionalidad en la aplicación:

1. Crea un botón de menú regular y la asigna un identificador, por ejemplo ID_CHAR_COLOR.

1. En la clase de ventana de marco, invalidar el [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) método y reemplace el menú habitual de botón con un [CMFCColorMenuButton (clase)](../../mfc/reference/cmfccolormenubutton-class.md) objeto (mediante una llamada a [CMFCToolBar: : ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Establecer todos los estilos y habilitar o deshabilitar las características de la `CMFCColorBar` objeto durante [CMFCColorMenuButton (clase)](../../mfc/reference/cmfccolormenubutton-class.md) creación. El `CMFCColorMenuButton` objeto crea dinámicamente la `CMFCColorBar` objeto después de las llamadas de framework la `CreatePopupMenu` método.

Cuando el usuario hace clic en un botón de control de barra de color, el marco de trabajo usa el `ON_COMMAND` macro para notificar el elemento primario del control de barra de colores. En la macro, el parámetro de identificador de comando es el valor que asigna al botón de control de barra de colores en el paso 1 (ID_CHAR_COLOR en este ejemplo). Para obtener más información, consulte el [CMFCColorMenuButton (clase)](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton (clase)](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl (clase)](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx(clase)](../../mfc/reference/cframewndex-class.md), y [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md) clases.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar una barra de colores mediante distintos métodos en el `CMFCColorBar` clase. Los métodos de establecer los márgenes horizontales y verticales, habilitar el botón otro, creación una ventana de control de barra de colores y establece el color seleccionado actualmente. Este ejemplo forma parte de la [ejemplo de controles nuevos](../../visual-cpp-samples.md).

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

**Encabezado:** afxcolorbar.h

##  <a name="adjustlocations"></a>  CMFCColorBar::AdjustLocations

Ajusta las posiciones de los botones de color en el control de barra de color.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Comentarios

Este método se llama el marco de trabajo durante el procesamiento del mensaje WM_SIZE.

##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels

Indica si se puede cambiar la etiqueta de texto de los botones de color.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre es FALSE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método siempre devuelve FALSE, lo que significa que no se puede modificar las etiquetas de texto. Invalide este método para habilitar la modificación de las etiquetas de texto.

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

Lo llama el marco de trabajo como parte del proceso de cálculo de diseño.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parámetros

*bVertDock*<br/>
[in] TRUE para especificar que está acoplado el control de barra de colores verticalmente; FALSE para especificar que el control de barra de color está acoplado horizontalmente.

### <a name="return-value"></a>Valor devuelto

El tamaño de la matriz de botones de color en un control de barra de colores.

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
[in] Una matriz de colores que el marco de trabajo se muestra en el control de barra de colores.

*color*<br/>
[in] El color seleccionado inicialmente.

*lpszAutoColor*<br/>
[in] La etiqueta de texto de la *automática* botón de color (valor predeterminado), o NULL.

La etiqueta para el botón automático estándar es **automática**.

*lpszOtherColor*<br/>
[in] La etiqueta de texto de la *otros* botón que muestra más las opciones de color, o NULL.

La etiqueta para el botón otro estándar es **más colores...** .

*lpszDocColors*<br/>
[in] La etiqueta de texto del botón de colores del documento. La paleta de colores del documento enumera todos los colores que utiliza actualmente el documento.

*lstDocColors*<br/>
[in] Una lista de colores que usa actualmente el documento.

*nColumns*<br/>
[in] El número de columnas que tiene la matriz de colores.

*nRowsDockHorz*<br/>
[in] El número de filas que tiene la barra de color cuando está acoplado horizontalmente.

*nColDockVert*<br/>
[in] El número de columnas que tiene la barra de color cuando se acopla verticalmente.

*colorAutomatic*<br/>
[in] El color predeterminado que se aplica el marco de trabajo al hacer clic en el botón automático.

*nCommandID*<br/>
[in] Identificador de comando de control de barra de colores.

*pParentBtn*<br/>
[in] Un puntero a un botón primario.

*src*<br/>
[in] Existente `CMFCColorBar` objeto que se copiará en el nuevo `CMFCColorBar` objeto.

*uiCommandID*<br/>
[in] El identificador de comando.

##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize

Calcula los márgenes horizontales y verticales que son necesarias para contener los botones del control de barra de colores y ajusta la ubicación de esos botones.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*bSquareButtons*|[in] TRUE para especificar que la forma de los botones en un control de barra de color cuadrado; en caso contrario, FALSE. El valor predeterminado es TRUE.|
|*bCenterButtons*|[in] TRUE para especificar que se centra el contenido en un botón de control de barra de colores; en caso contrario, FALSE. El valor predeterminado es TRUE.|

### <a name="remarks"></a>Comentarios

##  <a name="create"></a>  CMFCColorBar::Create

Crea una ventana de control de barra de colores y la conecta a la `CMFCColorBar` objeto.

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
[in] Puntero a la ventana primaria.

*dwStyle*<br/>
[in] Una combinación bit a bit (OR) de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*nID*<br/>
[in] El identificador de comando.

*pPalette*<br/>
[in] Puntero a una paleta de colores. El valor predeterminado es NULL.

*nColumns*<br/>
[in] El número de columnas en el control de barra de colores. El valor predeterminado es 0.

*nRowsDockHorz*<br/>
[in] El número de filas del control de barra de colores cuando se acopla horizontalmente. El valor predeterminado es 0.

*nColDockVert*<br/>
[in] El número de columnas en el control de barra de colores cuando se acopla verticalmente. El valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Para construir un `CMFCColorBar` de objeto, llame al constructor de clase, a continuación, este método. El `Create` método crea el control de Windows e inicializa una lista de colores.

##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl

Crea una ventana de control de barra de colores, que se conecta a la `CMFCColorBar` de objetos y cambia el tamaño de la ventana de control para que contenga la paleta de colores especificada.

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
[in] Puntero a la ventana primaria. No puede ser nulo.

*rect*<br/>
[in] Un rectángulo delimitador que especifica dónde se va a dibujar el control de barra de color.

*nID*<br/>
[in] El identificador de control.

*nColumns*<br/>
[in] El número ideal de las columnas del control de barra de colores. Este método modifica ese número para ajustarse a la paleta de colores especificada. El valor predeterminado es -1, lo que significa que no se especifica este parámetro.

*pPalette*<br/>
[in] Puntero a una paleta de colores, o NULL. Si este parámetro es NULL, este método calcula el tamaño del control de barra de colores como si se especificaron 20 colores. El valor predeterminado es NULL.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método usa la *rect*, *nColumns*, y *pPalette* parámetros para calcular el número apropiado o filas y columnas en el control de barra de colores y, a continuación, llama a la [CMFCColorBar::Create](#create) método.

##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette

Inicializa una paleta con los colores de una matriz de colores especificada.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*arColors*|[in] Una matriz de colores.|
|*palette*|[in] Una paleta de colores.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton

Muestra u oculta el botón automático.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[in] La etiqueta de texto de la *automática* botón de color (valor predeterminado), o NULL.

La etiqueta para el botón automático estándar es **automática**.

*colorAutomatic*<br/>
[in] El color predeterminado que se aplica el marco de trabajo al hacer clic en el botón automático.

*bEnable*<br/>
[in] TRUE para habilitar el botón automático; FALSE para deshabilitar el botón automático. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

La etiqueta de texto del botón automático se elimina si el *lpszLabel* parámetro es NULL o *bHabilitar el* parámetro es FALSE.

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
[in] La etiqueta de texto de la *otros* botón que muestra más las opciones de color, o NULL.

La etiqueta estándar para este botón es **más colores...** .

*bAltColorDlg*<br/>
[in] True para mostrar el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo; FALSE para mostrar el estándar [CColorDialog](../../mfc/reference/ccolordialog-class.md) cuadro de diálogo. El valor predeterminado es TRUE.

*bEnable*<br/>
[in] TRUE para habilitar el botón; FALSE para deshabilitar el botón. El valor predeterminado es TRUE.

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

|Parámetro|Descripción|
|---------------|-----------------|
|*bVertDock*|[in] TRUE para realizar el cálculo de un control de barra de color acoplado verticalmente; en caso contrario, puede realizar el cálculo de un control acoplado horizontalmente.|

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) cuyo `cx` componente contiene el número de columnas y cuyo `cy` componente contiene el número de filas.

##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID

Recupera el identificador de comando del control de barra de color actual.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador de comando.

### <a name="remarks"></a>Comentarios

Cuando el usuario selecciona un nuevo color, el marco de trabajo envía el identificador de comando en un mensaje WM_COMMAND para notificar el elemento primario de la `CMFCColorBar` objeto.

##  <a name="getextraheight"></a>  CMFCColorBar::GetExtraHeight

Calcula el alto adicional que requiere la barra de colores actual para mostrar los elementos de la interfaz de usuario, como el **otros** colores de botón o un documento.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*nNumColumns*|[in] Si el control de barra de colores contiene colores del documento, el número de columnas que se muestran en la cuadrícula de colores del documento. En caso contrario, no se utiliza este valor.|

### <a name="return-value"></a>Valor devuelto

El alto adicional calculado que se necesita.

##  <a name="gethighlightedcolor"></a>  CMFCColorBar::GetHighlightedColor

Recupera el color que indica que un botón en color tiene el foco; es decir, el botón *hot*.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor RGB.

### <a name="remarks"></a>Comentarios

##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin

Recupera el margen horizontal, que es el espacio entre la izquierda o celda de color a la derecha y el límite del área cliente.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Valor devuelto

El margen horizontal.

##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin

Recupera el margen vertical, que es el espacio entre la parte superior o celda de color de la parte inferior y el límite del área cliente.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Valor devuelto

El margen vertical.

##  <a name="initcolors"></a>  CMFCColorBar::InitColors

Inicializa una matriz de colores con los colores de una paleta especificado, o con la paleta predeterminada del sistema.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pPalette*|[in] Un puntero a un objeto de la paleta, o NULL. Si este parámetro es NULL, este método usa la paleta predeterminada del sistema operativo.|
|*arColors*|[in] Una matriz de colores.|

### <a name="return-value"></a>Valor devuelto

El número de elementos de la matriz de colores.

##  <a name="istearoff"></a>  CMFCColorBar::IsTearOff

Indica si la barra de colores actual es acoplable.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el control de barra de colores actual es acoplable; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si el control de barra de color es acoplable, puede arrancado una barra de controles y acoplar en otra ubicación.

##  <a name="onkey"></a>  CMFCColorBar::OnKey

Lo llama el marco cuando el usuario presiona un botón de teclado.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parámetros

*nChar*<br/>
[in] El código de tecla virtual de la clave que un usuario ha presionado.

### <a name="return-value"></a>Valor devuelto

TRUE si este método procesa la clave especificada; en caso contrario, FALSE.

##  <a name="onsendcommand"></a>  CMFCColorBar::OnSendCommand

Lo llama el marco de trabajo para cerrar una jerarquía de controles de elementos emergentes.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pButton*|[in] Puntero a un control que se encuentra en una barra de herramientas.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

##  <a name="onupdatecmdui"></a>  CMFCColorBar::OnUpdateCmdUI

Lo llama el marco de trabajo para habilitar o deshabilitar un elemento de interfaz de usuario de un control de barra de colores antes de que se muestra el elemento.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
[in] Puntero a una ventana que contiene un elemento de interfaz de usuario para la actualización.

*bDisableIfNoHndler*<br/>
[in] TRUE para deshabilitar el elemento de interfaz de usuario si no se define ningún controlador en un mapa de mensajes; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Cuando un usuario de la aplicación hace clic en un elemento de interfaz de usuario, el elemento debe saber si debe mostrarse como habilitado o deshabilitado. El destino del mensaje comando proporciona esta información mediante la implementación de un controlador de comandos ON_UPDATE_COMMAND_UI. Use este método para procesar el comando. Para obtener más información, consulte [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md).

##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog

Se abre un cuadro de diálogo color.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parámetros

*colorDefault*<br/>
[in] El color que está seleccionado de forma predeterminada cuando se abre el cuadro de diálogo color.

*colorRes*<br/>
[out] El color que el usuario seleccionado.

### <a name="return-value"></a>Valor devuelto

TRUE si el usuario selecciona un color; FALSE si el usuario canceló el cuadro de diálogo color.

### <a name="remarks"></a>Comentarios

##  <a name="rebuild"></a>  CMFCColorBar::Rebuild

Completamente vuelve a dibujar el control de barra de color.

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette

Establece la paleta lógica del contexto de dispositivo especificado en la paleta del botón primario del control de barra de color actual.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pDC*|[in] Puntero al contexto de dispositivo del botón primario del control de barra de color actual.|

### <a name="return-value"></a>Valor devuelto

Puntero a la paleta que se ha reemplazado por la paleta del botón primario del control de barra de color actual.

##  <a name="setcolor"></a>  CMFCColorBar::SetColor

Establece el color que está seleccionado actualmente.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
[in] Un valor de color RGB.

##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName

Establece un nuevo nombre para un color especificado.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
[in] El valor RGB de un color.

*strName*<br/>
[in] El nuevo nombre para el color especificado.

### <a name="remarks"></a>Comentarios

Este método cambia el nombre del color especificado en todos los `CMFCColorBar` objetos en la aplicación.

##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID

Establece un nuevo identificador de comando para un control de barra de color.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parámetros

*nCommandID*<br/>
[in] Un identificador de comando.

### <a name="remarks"></a>Comentarios

Llame a este método para modificar el identificador de comando de un control de barra de colores y para notificar a la ventana primaria del control que ha cambiado el identificador.

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
[in] Un título que se muestra cuando no está acoplado el control de barra de colores.

*lstDocColors*<br/>
[in] Una lista de colores que reemplaza los colores del documento actual.

*bShowWhenDocked*<br/>
[in] TRUE para mostrar los colores del documento cuando se acopla el control de barra de color; en caso contrario, FALSE. El valor predeterminado es FALSE.

### <a name="remarks"></a>Comentarios

*Colores de documento* son los colores que se usan actualmente en un documento. El marco de trabajo mantiene automáticamente una lista de colores del documento, pero puede usar este método para modificar la lista.

##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin

Establece el margen horizontal, que es el espacio entre la izquierda o celda de color a la derecha y el límite del área de cliente.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parámetros

*nHorzMargin*<br/>
[in] El margen horizontal, en píxeles.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el [CMFCColorBar::CMFCColorBar](#cmfccolorbar) constructor establece el margen horizontal hasta 4 píxeles.

##  <a name="setproplist"></a>  CMFCColorBar::SetPropList

Establece el `m_pWndPropList` protegido el puntero especificado a un control de cuadrícula de propiedades de miembro de datos.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pWndList*|[in] Puntero al objeto de control de cuadrícula de propiedad.|

##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin

Establece el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parámetros

*nVertMargin*<br/>
[in] El margen vertical, en píxeles.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el [CMFCColorBar::CMFCColorBar](#cmfccolorbar) constructor establece el margen vertical en 4 píxeles.

##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString

Solicitudes de la ventana de marco que posee el control de barra de colores para actualizar la línea del mensaje en la barra de estado.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parámetros

*uiCmdId*<br/>
[in] Un identificador de comando. (Este parámetro se omite).

### <a name="remarks"></a>Comentarios

Este método envía el mensaje WM_SETMESSAGESTRING al propietario del control de barra de colores.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
