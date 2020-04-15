---
title: CMFCColorBar Clase
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
ms.openlocfilehash: 7b63fb66b800bd758c7f4c89c553e857ad9bbfbc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367770"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar Clase

La `CMFCColorBar` clase representa una barra de control de acoplamiento que puede seleccionar colores en un documento o aplicación.

## <a name="syntax"></a>Sintaxis

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorBar::CMFCColorBar](#cmfccolorbar)|Construye un objeto `CMFCColorBar`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorBar::ContextToSize](#contexttosize)|Calcula los márgenes verticales y horizontales necesarios para contener los botones del control de barra de color y, a continuación, ajusta la ubicación de esos botones.|
|[CMFCColorBar::CreateControl](#createcontrol)|Crea una ventana de control de `CMFCColorBar` barra de color, la asocia al objeto y cambia el tamaño del control para que contenga la paleta de colores especificada.|
|[CMFCColorBar::Crear](#create)|Crea una ventana de control de `CMFCColorBar` barra de color y la adjunta al objeto.|
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Muestra u oculta el botón automático.|
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Habilita o deshabilita la visualización de un cuadro de diálogo que permite al usuario seleccionar más colores.|
|[CMFCColorBar::GetColor](#getcolor)|Recupera el color seleccionado actualmente.|
|[CMFCColorBar::GetCommandID](#getcommandid)|Recupera el identificador de comando del control de barra de color actual.|
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Recupera el color que significa que un botón de color tiene el foco; es decir, el botón está *caliente.*|
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Recupera el margen horizontal, que es el espacio entre la celda de color izquierda o derecha y el límite del área de cliente.|
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Recupera el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área de cliente.|
|[CMFCColorBar::IsTearOff](#istearoff)|Indica si la barra de color actual es acoplable.|
|[CMFCColorBar::SetColor](#setcolor)|Establece el color que está seleccionado actualmente.|
|[CMFCColorBar::SetColorName](#setcolorname)|Establece un nuevo nombre para un color especificado.|
|[CMFCColorBar::SetCommandID](#setcommandid)|Establece un nuevo identificador de comando para un control de barra de color.|
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Establece la lista de colores que se utilizan en el documento actual.|
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Establece el margen horizontal, que es el espacio entre la celda de color izquierda o derecha y el límite del área cliente.|
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Establece el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Ajusta las posiciones de los botones de color en el control de barra de color.|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Indica si la etiqueta de texto de los botones de color puede cambiar.|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Indica si el objeto de control de barra de color puede aparecer en una lista de barra de herramientas durante el proceso de personalización.|
|[CMFCColorBar::CalcSize](#calcsize)|Llamado por el marco de trabajo como parte del proceso de cálculo de diseño.|
|[CMFCColorBar::CreatePalette](#createpalette)|Inicializa una paleta con los colores de una matriz de colores especificada.|
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Calcula el número de filas y columnas en la cuadrícula de un control de barra de color.|
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Calcula la altura adicional que la barra de color actual requiere para mostrar varios elementos de la interfaz de usuario, como el botón **Otro,** los colores del documento, etc.|
|[CMFCColorBar::InitColors](#initcolors)|Inicializa una matriz de colores con los colores de una paleta especificada o de la paleta predeterminada del sistema.|
|[CMFCColorBar::OnKey](#onkey)|Llamado por el marco de trabajo cuando un usuario presiona un botón de teclado.|
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Llamado por el marco de trabajo para cerrar una jerarquía de controles emergentes.|
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Llamado por el marco de trabajo para habilitar o deshabilitar un elemento de interfaz de usuario de un control de barra de color antes de que se muestre el elemento.|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Abre un cuadro de diálogo de color.|
|[CMFCColorBar::Reconstruir](#rebuild)|Redibuja completamente el control de barra de color.|
|[CMFCColorBar::SelectPalette](#selectpalette)|Establece la paleta lógica del contexto de dispositivo especificado en la paleta del botón primario del control de barra de color actual.|
|[CMFCColorBar::SetPropList](#setproplist)|Establece `m_pWndPropList` el miembro de datos protegido en el puntero especificado a un control de cuadrícula de propiedades.|
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Solicita la ventana de marco propietaria del control de barra de color para actualizar la línea de mensaje en la barra de estado.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|`m_bInternal`|Un campo booleano que determina si se procesan los eventos del mouse. Normalmente, los eventos del mouse se procesan cuando este campo es TRUE y el modo de personalización es FALSE.|
|`m_bIsEnabled`|Un valor booleano que indica si un control está habilitado.|
|`m_bIsTearOff`|Un valor booleano que indica si el control de barra de color admite el acoplamiento.|
|`m_BoxSize`|Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica el tamaño de una celda en una cuadrícula de barra de color.|
|`m_bShowDocColorsWhenDocked`|Un valor booleano que indica si se deben mostrar los colores del documento cuando se acopla la barra de color. Para obtener más información, vea [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_bStdColorDlg`|Un valor booleano que indica si se debe mostrar el cuadro de diálogo de color del sistema estándar o el cuadro de diálogo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) . Para obtener más información, vea [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorAutomatic`|[ColorREF](/windows/win32/gdi/colorref) que almacena el color automático actual. Para obtener más información, vea [CMFCColorBar::EnableOtherButton](#enableotherbutton).|
|`m_ColorNames`|Un [objeto CMap](../../mfc/reference/cmap-class.md) que asocia un conjunto de colores RGB con sus nombres.|
|`m_colors`|Un [CArray](../../mfc/reference/carray-class.md) de [COLORREF](/windows/win32/gdi/colorref) valores que contiene los colores que se muestran en el control de barra de color.|
|`m_ColorSelected`|Un valor [COLORREF](/windows/win32/gdi/colorref) que es el color que el usuario ha seleccionado actualmente en el control de barra de color.|
|`m_lstDocColors`|Un [CList](../../mfc/reference/clist-class.md) de [COLORREF](/windows/win32/gdi/colorref) valores que contiene los colores que se utilizan actualmente en un documento.|
|`m_nCommandID`|Un entero sin signo que es el identificador de comando de un botón de color.|
|`m_nHorzMargin`|Entero que es el margen horizontal entre los botones de color de una cuadrícula de colores.|
|`m_nHorzOffset`|Entero que es el desplazamiento horizontal al centro del botón de color. Este valor es significativo si el botón muestra texto o una imagen además de un color.|
|`m_nNumColumns`|Entero que es el número de columnas de una cuadrícula de colores de control de barra de color.|
|`m_nNumColumnsVert`|Entero que es el número de columnas de una cuadrícula de colores orientada verticalmente.|
|`m_nNumRowsHorz`|Entero que es el número de columnas de una cuadrícula de colores orientada horizontalmente.|
|`m_nRowHeight`|Entero que es el alto de una fila de botones de color en una cuadrícula de colores.|
|`m_nVertMargin`|Entero que es el margen vertical entre los botones de color de una cuadrícula de colores.|
|`m_nVertOffset`|Entero que es el desplazamiento vertical al centro del botón de color. Este valor es significativo si el botón muestra texto o una imagen además de un color.|
|`m_Palette`|Una [CPalette](../../mfc/reference/cpalette-class.md) de los colores que se utilizan en el control de barra de color.|
|`m_pParentBtn`|Un puntero a un [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) objeto que es el elemento primario del botón actual. Este valor es significativo si el botón de color está en una jerarquía de controles de barra de herramientas o está en un control de cuadrícula de propiedades de color.|
|`m_pParentRibbonBtn`|Un puntero a un [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) objeto que se encuentra en la cinta de opciones y es el botón primario del botón actual. Este valor es significativo si el botón de color está en una jerarquía de controles de barra de herramientas o está en un control de cuadrícula de propiedades de color.|
|`m_pWndPropList`|Un puntero a un [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) objeto.|
|`m_strAutoColor`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el **automático** botón. Para obtener más información, vea [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|
|`m_strDocColors`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el botón de colores del documento. Para obtener más información, vea [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|
|`m_strOtherColor`|Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el *otro* botón. Para obtener más información, vea [CMFCColorBar::EnableOtherButton](#enableotherbutton).|

## <a name="remarks"></a>Observaciones

Normalmente, no se `CMFCColorBar` crea un objeto directamente. En su lugar, la [clase CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md) (utilizada en menús y `CMFCColorBar` barras de herramientas) o la clase [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) crea el objeto.

La `CMFCColorBar` clase proporciona la siguiente funcionalidad:

- Ajusta automáticamente la lista de colores del documento.

- Guarda y restaura su estado, junto con el estado del documento.

- Administra el botón "automático".

- Utiliza el [CMFCColorPickerCtrl (clase)](../../mfc/reference/cmfccolorpickerctrl-class.md) control para seleccionar un color personalizado.

- Admite un estado "tear-off" (si se crea mediante la [clase CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)).

Para incorporar `CMFCColorBar` la funcionalidad en la aplicación:

1. Cree un botón de menú normal y asígnele un ID, por ejemplo, ID_CHAR_COLOR.

1. En la clase de ventana de marco, reemplace el método [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) y reemplace el botón de menú normal con un objeto [CMFCColorMenuButton (clase)](../../mfc/reference/cmfccolormenubutton-class.md) (llamando a [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).

1. Establecer todos los estilos y habilitar `CMFCColorBar` o deshabilitar las características del objeto durante la creación de [CMFCColorMenuButton clase.](../../mfc/reference/cmfccolormenubutton-class.md) El `CMFCColorMenuButton` objeto crea dinámicamente el `CMFCColorBar` objeto `CreatePopupMenu` después de que el marco de trabajo llama al método.

Cuando el usuario hace clic en un botón de control de barra de color, el marco de trabajo utiliza la `ON_COMMAND` macro para notificar al elemento primario del control de barra de color. En la macro, el parámetro ID de comando es el valor que asignó al botón de control de barra de color en el paso 1 (ID_CHAR_COLOR en este ejemplo). Para obtener más información, vea las clases [CMFCColorMenuButton (Clase)](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton (Clase)](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl (Clase)](../../mfc/reference/cmfccolorpickerctrl-class.md)y [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) [(Clase).](../../mfc/reference/cframewndex-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar una `CMFCColorBar` barra de colores mediante varios métodos de la clase. Los métodos establecen los márgenes horizontal y vertical, habilitan el otro botón, crean una ventana de control de barra de color y establecen el color seleccionado actualmente. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

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

## <a name="cmfccolorbaradjustlocations"></a><a name="adjustlocations"></a>CMFCColorBar::AdjustLocations

Ajusta las posiciones de los botones de color en el control de barra de color.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método durante WM_SIZE procesamiento de mensajes.

## <a name="cmfccolorbarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels

Indica si la etiqueta de texto de los botones de color puede cambiar.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre FALSE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método siempre devuelve FALSE, lo que significa que las etiquetas de texto no se pueden modificar. Invalide este método para habilitar la modificación de etiquetas de texto.

## <a name="cmfccolorbarallowshowonlist"></a><a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList

Indica si el objeto de control de barra de color puede aparecer en una lista de barra de herramientas durante el proceso de personalización.

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre TRUE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método siempre devuelve TRUE, lo que significa que el marco de trabajo puede mostrar el control de barra de color durante el proceso de personalización. Invalide este método para implementar un comportamiento diferente.

## <a name="cmfccolorbarcalcsize"></a><a name="calcsize"></a>CMFCColorBar::CalcSize

Llamado por el marco de trabajo como parte del proceso de cálculo de diseño.

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>Parámetros

*bVertDock*<br/>
[en] TRUE para especificar que el control de barra de color se acopla verticalmente; FALSE para especificar que el control de barra de color se acopla horizontalmente.

### <a name="return-value"></a>Valor devuelto

El tamaño de la matriz de botones de color en un control de barra de color.

## <a name="cmfccolorbarcmfccolorbar"></a><a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar

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

*Colores*<br/>
[en] Matriz de colores que el marco de trabajo muestra en el control de barra de color.

*color*<br/>
[en] El color seleccionado inicialmente.

*lpszAutoColor*<br/>
[en] La etiqueta de texto del botón de color *automático* (predeterminado) o NULL.

La etiqueta estándar para el botón automático es **Automático**.

*lpszOtherColor*<br/>
[en] La etiqueta de texto del *otro* botón, que muestra más opciones de color, o NULL.

La etiqueta estándar para el otro botón es **Más colores...**.

*lpszDocColors*<br/>
[en] La etiqueta de texto del botón de colores del documento. La paleta de colores del documento muestra todos los colores que utiliza actualmente el documento.

*lstDocColors*<br/>
[en] Una lista de colores que el documento utiliza actualmente.

*nColumns*<br/>
[en] El número de columnas que tiene la matriz de colores.

*nRowsDockHorz*<br/>
[en] El número de filas que tiene la barra de color cuando se acopla horizontalmente.

*nColDockVert*<br/>
[en] El número de columnas que tiene la barra de color cuando se acopla verticalmente.

*colorAutomático*<br/>
[en] El color predeterminado que se aplica al hacer clic en el botón automático.

*nCommandID*<br/>
[en] El ID del comando de control de barra de color.

*pParentBtn*<br/>
[en] Un puntero a un botón primario.

*src*<br/>
[en] Objeto `CMFCColorBar` existente que se va `CMFCColorBar` a copiar en el nuevo objeto.

*uiCommandID*<br/>
[en] El id de comando.

## <a name="cmfccolorbarcontexttosize"></a><a name="contexttosize"></a>CMFCColorBar::ContextToSize

Calcula los márgenes verticales y horizontales necesarios para contener los botones del control de barra de color y ajusta la ubicación de esos botones.

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*bSquareButtons*|[en] TRUE para especificar que la forma de los botones de un control de barra de color es cuadrada; de lo contrario, FALSE. El valor predeterminado es TRUE.|
|*bCenterButtons*|[en] TRUE para especificar que el contenido de la cara de un botón de control de barra de color está centrado; de lo contrario, FALSE. El valor predeterminado es TRUE.|

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbarcreate"></a><a name="create"></a>CMFCColorBar::Crear

Crea una ventana de control de `CMFCColorBar` barra de color y la adjunta al objeto.

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
[en] Puntero a la ventana primaria.

*dwStyle*<br/>
[en] Una combinación bit a bit (OR) de estilos de [ventana.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

*nID*<br/>
[en] El id de comando.

*pPalette*<br/>
[en] Puntero a una paleta de colores. El valor predeterminado es NULL.

*nColumns*<br/>
[en] El número de columnas en el control de barra de color. El valor predeterminado es 0.

*nRowsDockHorz*<br/>
[en] El número de filas en el control de barra de color cuando se acopla horizontalmente. El valor predeterminado es 0.

*nColDockVert*<br/>
[en] El número de columnas en el control de barra de color cuando se acopla verticalmente. El valor predeterminado es 0.

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Para construir `CMFCColorBar` un objeto, llame al constructor de clase y, a continuación, a este método. El `Create` método crea el control de Windows e inicializa una lista de colores.

## <a name="cmfccolorbarcreatecontrol"></a><a name="createcontrol"></a>CMFCColorBar::CreateControl

Crea una ventana de control de `CMFCColorBar` barra de color, la adjunta al objeto y cambia el tamaño de la ventana de control para que contenga la paleta de colores especificada.

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
[en] Puntero a la ventana primaria. No puede ser NULL.

*Rect*<br/>
[en] Rectángulo delimitador que especifica dónde dibujar el control de barra de color.

*nID*<br/>
[en] El identificador de control.

*nColumns*<br/>
[en] El número ideal de columnas en el control de barra de color. Este método modifica ese número para que se ajuste a la paleta de colores especificada. El valor predeterminado es -1, lo que significa que no se especifica este parámetro.

*pPalette*<br/>
[en] Puntero a una paleta de colores o NULL. Si este parámetro es NULL, este método calcula el tamaño del control de barra de color como si se especificaran 20 colores. El valor predeterminado es NULL.

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método utiliza los parámetros *rect*, *nColumns*y *pPalette* para calcular el número o filas y columnas adecuados en el control de barra de color y, a continuación, llama al método [CMFCColorBar::Create.](#create)

## <a name="cmfccolorbarcreatepalette"></a><a name="createpalette"></a>CMFCColorBar::CreatePalette

Inicializa una paleta con los colores de una matriz de colores especificada.

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*arColors*|[en] Una matriz de colores.|
|*paleta*|[en] Una paleta de colores.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

## <a name="cmfccolorbarenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton

Muestra u oculta el botón automático.

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] La etiqueta de texto del botón de color *automático* (predeterminado) o NULL.

La etiqueta estándar para el botón automático es **Automático**.

*colorAutomático*<br/>
[en] El color predeterminado que se aplica al hacer clic en el botón automático.

*bHabilitar*<br/>
[en] TRUE para habilitar el botón automático; FALSE para desactivar el botón automático. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

La etiqueta de texto del botón automático se elimina si el parámetro *lpszLabel* es NULL o el parámetro *bEnable* es FALSE.

## <a name="cmfccolorbarenableotherbutton"></a><a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton

Habilita o deshabilita la visualización de un cuadro de diálogo que permite al usuario seleccionar más colores.

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszLabel*<br/>
[en] La etiqueta de texto del *otro* botón, que muestra más opciones de color, o NULL.

La etiqueta estándar para este botón es **Más colores...**.

*bAltColorDlg*<br/>
[en] TRUE para mostrar el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo; FALSE para mostrar el cuadro de diálogo [estándar CColorDialog.](../../mfc/reference/ccolordialog-class.md) El valor predeterminado es TRUE.

*bHabilitar*<br/>
[en] TRUE para habilitar el botón; FALSE para deshabilitar el botón. El valor predeterminado es TRUE.

## <a name="cmfccolorbargetcolor"></a><a name="getcolor"></a>CMFCColorBar::GetColor

Recupera el color seleccionado actualmente.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Valor devuelto

El color seleccionado actualmente.

## <a name="cmfccolorbargetcolorgridsize"></a><a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize

Calcula el número de filas y columnas en la cuadrícula de un control de barra de color.

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*bVertDock*|[en] TRUE para realizar el cálculo de un control de barra de color acoplado verticalmente; de lo contrario, realice el cálculo de un control acoplado horizontalmente.|

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) `cx` objeto cuyo componente contiene `cy` el número de columnas y cuyo componente contiene el número de filas.

## <a name="cmfccolorbargetcommandid"></a><a name="getcommandid"></a>CMFCColorBar::GetCommandID

Recupera el identificador de comando del control de barra de color actual.

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador de comando.

### <a name="remarks"></a>Observaciones

Cuando el usuario selecciona un nuevo color, el marco de trabajo envía `CMFCColorBar` el identificador de comando en un mensaje de WM_COMMAND para notificar al elemento primario del objeto.

## <a name="cmfccolorbargetextraheight"></a><a name="getextraheight"></a>CMFCColorBar::GetExtraHeight

Calcula la altura adicional que la barra de color actual requiere para mostrar varios elementos de la interfaz de usuario, como el botón **Otros** o los colores del documento.

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*nNumColumns*|[en] Si el control de barra de color contiene colores de documento, el número de columnas que se mostrarán en la cuadrícula de colores del documento. De lo contrario, este valor no se utiliza.|

### <a name="return-value"></a>Valor devuelto

La altura adicional calculada que se requiere.

## <a name="cmfccolorbargethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor

Recupera el color que significa que un botón de color tiene el foco; es decir, el botón está *caliente.*

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbargethorzmargin"></a><a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin

Recupera el margen horizontal, que es el espacio entre la celda de color izquierda o derecha y el límite del área de cliente.

```
int GetHorzMargin();
```

### <a name="return-value"></a>Valor devuelto

El margen horizontal.

## <a name="cmfccolorbargetvertmargin"></a><a name="getvertmargin"></a>CMFCColorBar::GetVertMargin

Recupera el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área de cliente.

```
int GetVertMargin() const;
```

### <a name="return-value"></a>Valor devuelto

El margen vertical.

## <a name="cmfccolorbarinitcolors"></a><a name="initcolors"></a>CMFCColorBar::InitColors

Inicializa una matriz de colores con los colores de una paleta especificada o con la paleta predeterminada del sistema.

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pPalette*|[en] Puntero a un objeto de paleta o NULL. Si este parámetro es NULL, este método utiliza la paleta predeterminada del sistema operativo.|
|*arColors*|[en] Una matriz de colores.|

### <a name="return-value"></a>Valor devuelto

El número de elementos de la matriz de colores.

## <a name="cmfccolorbaristearoff"></a><a name="istearoff"></a>CMFCColorBar::IsTearOff

Indica si la barra de color actual es acoplable.

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el control de barra de color actual es acoplable; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el control de barra de color es acoplable, se puede arrancar de una barra de control y acoplarse en otra ubicación.

## <a name="cmfccolorbaronkey"></a><a name="onkey"></a>CMFCColorBar::OnKey

Llamado por el marco de trabajo cuando un usuario presiona un botón de teclado.

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>Parámetros

*Nchar*<br/>
[en] El código de tecla virtual de la tecla que presionó un usuario.

### <a name="return-value"></a>Valor devuelto

TRUESi este método procesa la clave especificada; de lo contrario, FALSE.

## <a name="cmfccolorbaronsendcommand"></a><a name="onsendcommand"></a>CMFCColorBar::OnSendCommand

Llamado por el marco de trabajo para cerrar una jerarquía de controles emergentes.

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pButton*|[en] Puntero a un control que reside en una barra de herramientas.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

## <a name="cmfccolorbaronupdatecmdui"></a><a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI

Llamado por el marco de trabajo para habilitar o deshabilitar un elemento de interfaz de usuario de un control de barra de color antes de que se muestre el elemento.

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Parámetros

*pTarget*<br/>
[en] Puntero a una ventana que contiene un elemento de interfaz de usuario para actualizar.

*bDisableIfNoHndler*<br/>
[en] TRUE para deshabilitar el elemento de interfaz de usuario si no se define ningún controlador en un mapa de mensajes; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cuando un usuario de la aplicación hace clic en un elemento de interfaz de usuario, el elemento debe saber si debe mostrarse como habilitado o deshabilitado. El destino del mensaje de comando proporciona esta información mediante la implementación de un controlador de comandos ON_UPDATE_COMMAND_UI. Utilice este método para ayudar a procesar el comando. Para obtener más información, vea [CCmdUI (Clase)](../../mfc/reference/ccmdui-class.md).

## <a name="cmfccolorbaropencolordialog"></a><a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog

Abre un cuadro de diálogo de color.

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>Parámetros

*colorPredeterminado*<br/>
[en] El color seleccionado de forma predeterminada cuando se abre el cuadro de diálogo de color.

*colorRes*<br/>
[fuera] El color seleccionado por un usuario.

### <a name="return-value"></a>Valor devuelto

TRUESi el usuario seleccionó un color; FALSE si el usuario canceló el cuadro de diálogo de color.

### <a name="remarks"></a>Observaciones

## <a name="cmfccolorbarrebuild"></a><a name="rebuild"></a>CMFCColorBar::Reconstruir

Redibuja completamente el control de barra de color.

```
virtual void Rebuild();
```

## <a name="cmfccolorbarselectpalette"></a><a name="selectpalette"></a>CMFCColorBar::SelectPalette

Establece la paleta lógica del contexto de dispositivo especificado en la paleta del botón primario del control de barra de color actual.

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pDC*|[en] Puntero al contexto del dispositivo del botón primario del control de barra de color actual.|

### <a name="return-value"></a>Valor devuelto

Puntero a la paleta que se sustituye por la paleta del botón primario del control de barra de color actual.

## <a name="cmfccolorbarsetcolor"></a><a name="setcolor"></a>CMFCColorBar::SetColor

Establece el color que está seleccionado actualmente.

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
[en] Un valor de color RGB.

## <a name="cmfccolorbarsetcolorname"></a><a name="setcolorname"></a>CMFCColorBar::SetColorName

Establece un nuevo nombre para un color especificado.

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parámetros

*color*<br/>
[en] El valor RGB de un color.

*strName*<br/>
[en] El nuevo nombre para el color especificado.

### <a name="remarks"></a>Observaciones

Este método cambia el nombre del `CMFCColorBar` color especificado en todos los objetos de la aplicación.

## <a name="cmfccolorbarsetcommandid"></a><a name="setcommandid"></a>CMFCColorBar::SetCommandID

Establece un nuevo identificador de comando para un control de barra de color.

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>Parámetros

*nCommandID*<br/>
[en] Un identificador de comando.

### <a name="remarks"></a>Observaciones

Llame a este método para modificar el identificador de comando de un control de barra de color y para notificar a la ventana primaria del control que el identificador ha cambiado.

## <a name="cmfccolorbarsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors

Establece la lista de colores que se utilizan en el documento actual.

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>Parámetros

*lpszCaption*<br/>
[en] Un título que se muestra cuando el control de barra de color no está acoplado.

*lstDocColors*<br/>
[en] Una lista de colores que reemplaza los colores actuales del documento.

*bShowWhenDocked*<br/>
[en] TRUE para mostrar los colores del documento cuando se acopla el control de barra de color; de lo contrario, FALSE. El valor predeterminado es FALSE.

### <a name="remarks"></a>Observaciones

*Los colores* del documento son los colores que se utilizan actualmente en un documento. El marco de trabajo mantiene automáticamente una lista de colores de documento, pero puede usar este método para modificar la lista.

## <a name="cmfccolorbarsethorzmargin"></a><a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin

Establece el margen horizontal, que es el espacio entre la celda de color izquierda o derecha y el límite del área de cliente.

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>Parámetros

*nHorzMargin*<br/>
[en] El margen horizontal, en píxeles.

### <a name="remarks"></a>Observaciones

De forma predeterminada, el [CMFCColorBar::CMFCColorBar](#cmfccolorbar) constructor establece el margen horizontal en 4 píxeles.

## <a name="cmfccolorbarsetproplist"></a><a name="setproplist"></a>CMFCColorBar::SetPropList

Establece `m_pWndPropList` el miembro de datos protegido en el puntero especificado a un control de cuadrícula de propiedades.

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pWndList*|[en] Puntero al objeto de control de cuadrícula de propiedades.|

## <a name="cmfccolorbarsetvertmargin"></a><a name="setvertmargin"></a>CMFCColorBar::SetVertMargin

Establece el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>Parámetros

*nVertMargin*<br/>
[en] El margen vertical, en píxeles.

### <a name="remarks"></a>Observaciones

De forma predeterminada, el [CMFCColorBar::CMFCColorBar](#cmfccolorbar) constructor establece el margen vertical en 4 píxeles.

## <a name="cmfccolorbarshowcommandmessagestring"></a><a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString

Solicita la ventana de marco propietaria del control de barra de color para actualizar la línea de mensaje en la barra de estado.

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>Parámetros

*uiCmdId*<br/>
[en] Un identificador de comando. (Este parámetro se omite.)

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de WM_SETMESSAGESTRING al propietario del control de barra de color.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
