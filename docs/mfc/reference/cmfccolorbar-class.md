---
title: Clase CMFCColorBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 04dcf7628e45d4c43ffbd5bbcd85132092ca04a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccolorbar-class"></a>Clase CMFCColorBar
La `CMFCColorBar` clase representa una barra de controles de acoplamiento que puede seleccionar los colores en un documento o aplicación.  
  
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
|[CMFCColorBar::ContextToSize](#contexttosize)|Calcula los márgenes horizontales y verticales que son necesarios para contener los botones en el control de barra de colores y, a continuación, ajusta la ubicación de estos botones.|  
|[CMFCColorBar::CreateControl](#createcontrol)|Crea una ventana de control de barra de colores, que se conecta a la `CMFCColorBar` de objetos y cambia el tamaño del control para que contenga la paleta de colores especificada.|  
|[CMFCColorBar::Create](#create)|Crea una ventana de control de barra de colores y lo adjunta a la `CMFCColorBar` objeto.|  
|[CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton)|Muestra u oculta el botón automático.|  
|[CMFCColorBar::EnableOtherButton](#enableotherbutton)|Habilita o deshabilita la presentación de un cuadro de diálogo que permite al usuario seleccionar más colores.|  
|[CMFCColorBar::GetColor](#getcolor)|Recupera el color seleccionado actualmente.|  
|[CMFCColorBar::GetCommandID](#getcommandid)|Recupera el identificador de comando del control de barra de color actual.|  
|[CMFCColorBar::GetHighlightedColor](#gethighlightedcolor)|Recupera el color que indica que un botón en color tiene el foco; es decir, el botón *activa*.|  
|[CMFCColorBar::GetHorzMargin](#gethorzmargin)|Recupera el margen horizontal, que es el espacio entre la izquierda o la celda de color a la derecha y el límite del área cliente.|  
|[CMFCColorBar::GetVertMargin](#getvertmargin)|Recupera el margen vertical, que es el espacio entre la parte superior o celda de color de la parte inferior y el límite del área cliente.|  
|[CMFCColorBar::IsTearOff](#istearoff)|Indica si la barra de colores actual es acoplable.|  
|[CMFCColorBar::SetColor](#setcolor)|Establece el color que está seleccionado actualmente.|  
|[CMFCColorBar::SetColorName](#setcolorname)|Establece un nuevo nombre para un color especificado.|  
|[CMFCColorBar::SetCommandID](#setcommandid)|Establece un nuevo identificador de comando para un control de barra de color.|  
|[CMFCColorBar::SetDocumentColors](#setdocumentcolors)|Establece la lista de colores que se utilizan en el documento actual.|  
|[CMFCColorBar::SetHorzMargin](#sethorzmargin)|Establece el margen horizontal, que es el espacio entre la izquierda o la celda de color a la derecha y el límite del área cliente.|  
|[CMFCColorBar::SetVertMargin](#setvertmargin)|Establece el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorBar::AdjustLocations](#adjustlocations)|Ajusta las posiciones de los botones de color en el control de barra de color.|  
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|Indica si se puede cambiar la etiqueta de texto de los botones de color.|  
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|Indica si el objeto de control de barra de colores puede aparecer en una lista de la barra de herramientas durante el proceso de personalización.|  
|[CMFCColorBar::CalcSize](#calcsize)|Lo llama el marco como parte del proceso de cálculo de diseño.|  
|[CMFCColorBar::CreatePalette](#createpalette)|Inicializa una paleta con los colores de una matriz de colores especificada.|  
|[CMFCColorBar::GetColorGridSize](#getcolorgridsize)|Calcula el número de filas y columnas en la cuadrícula de un control de barra de colores.|  
|[CMFCColorBar::GetExtraHeight](#getextraheight)|Calcula el alto adicional que requiera la barra de colores actual para mostrar los elementos de la interfaz de usuario varios, como el **otros** botón, colores de documento y así sucesivamente.|  
|[CMFCColorBar::InitColors](#initcolors)|Inicializa una matriz de colores con los colores de una paleta especificada o la paleta predeterminada del sistema.|  
|[CMFCColorBar::OnKey](#onkey)|Lo llama el marco cuando el usuario presiona un botón de teclado.|  
|[CMFCColorBar::OnSendCommand](#onsendcommand)|Lo llama el marco de trabajo para cerrar una jerarquía de controles de menú emergente.|  
|[CMFCColorBar::OnUpdateCmdUI](#onupdatecmdui)|Lo llama el marco para habilitar o deshabilitar un elemento de interfaz de usuario de un control de barra de color antes de que se muestre el elemento.|  
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|Abre un cuadro de diálogo color.|  
|[CMFCColorBar::Rebuild](#rebuild)|Completamente vuelve a dibujarse el control de barra de color.|  
|[CMFCColorBar::SelectPalette](#selectpalette)|Establece la paleta lógica del contexto de dispositivo especificado en la paleta del botón primario del control de barra de color actual.|  
|[CMFCColorBar::SetPropList](#setproplist)|Establece el `m_pWndPropList` protegido el puntero especificado a un control de cuadrícula de propiedades de miembro de datos.|  
|[CMFCColorBar::ShowCommandMessageString](#showcommandmessagestring)|Las solicitudes de la ventana de marco que posee el control de barra de color para actualizar la línea del mensaje en la barra de estado.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|nombre|Descripción|  
|----------|-----------------|  
|`m_bInternal`|Un campo booleano que determina si se procesan los eventos del mouse. Normalmente, se procesan los eventos del mouse cuando este campo es `TRUE` y modo de personalización es `FALSE`.|  
|`m_bIsEnabled`|Un valor booleano que indica si un control está habilitado.|  
|`m_bIsTearOff`|Un valor booleano que indica si el control de barra de color es compatible con el acoplamiento.|  
|`m_BoxSize`|A [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que especifica el tamaño de una celda en una cuadrícula de la barra de colores.|  
|`m_bShowDocColorsWhenDocked`|Un valor booleano que indica si se muestran los colores del documento cuando se acopla la barra de colores. Para obtener más información, consulte [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|  
|`m_bStdColorDlg`|Un valor booleano que indica si se debe mostrar el cuadro de diálogo de color estándar del sistema o el [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo. Para obtener más información, consulte [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
|`m_ColorAutomatic`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) que almacena el color automático actual. Para obtener más información, consulte [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
|`m_ColorNames`|Un [CMap](../../mfc/reference/cmap-class.md) colores del objeto que se asocia un conjunto de RGB con sus nombres.|  
|`m_colors`|A [CArray](../../mfc/reference/carray-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valores que contiene los colores que se muestran en el control de barra de color.|  
|`m_ColorSelected`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que es el color que el usuario ha seleccionado actualmente en el control de barra de color.|  
|`m_lstDocColors`|A [CList](../../mfc/reference/clist-class.md) de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valores que contiene los colores que se utilizan actualmente en un documento.|  
|`m_nCommandID`|Un entero sin signo que es el identificador de comando de un botón de color.|  
|`m_nHorzMargin`|Un entero que es el margen horizontal entre los botones de color en una cuadrícula de colores.|  
|`m_nHorzOffset`|Un entero que es el desplazamiento horizontal en el centro del botón de color. Este valor es importante si el botón muestra el texto o una imagen además de un color.|  
|`m_nNumColumns`|Un entero que es el número de columnas en una cuadrícula de control de barra de colores de colores.|  
|`m_nNumColumnsVert`|Un entero que es el número de columnas en una cuadrícula de una orientación vertical de colores.|  
|`m_nNumRowsHorz`|Un entero que es el número de columnas en una cuadrícula orientación horizontal de colores.|  
|`m_nRowHeight`|Un entero que es el alto de una fila de botones de color en una cuadrícula de colores.|  
|`m_nVertMargin`|Un entero que es el margen vertical entre los botones de color en una cuadrícula de colores.|  
|`m_nVertOffset`|Un entero que es el desplazamiento vertical en el centro del botón de color. Este valor es importante si el botón muestra el texto o una imagen además de un color.|  
|`m_Palette`|A [CPalette](../../mfc/reference/cpalette-class.md) de los colores que se utilizan en el control de barra de color.|  
|`m_pParentBtn`|Un puntero a un [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) objeto que es el elemento primario del botón actual. Este valor es importante si el botón de color está en una jerarquía de controles de barra de herramientas o en un control de cuadrícula de propiedad de color.|  
|`m_pParentRibbonBtn`|Un puntero a un [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) objeto que se encuentra en la cinta de opciones y es el botón primario del botón actual. Este valor es importante si el botón de color está en una jerarquía de controles de barra de herramientas o en un control de cuadrícula de propiedad de color.|  
|`m_pWndPropList`|Un puntero a un [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) objeto.|  
|`m_strAutoColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el **automática** botón. Para obtener más información, consulte [CMFCColorBar::EnableAutomaticButton](#enableautomaticbutton).|  
|`m_strDocColors`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el botón de colores del documento. Para obtener más información, consulte [CMFCColorBar::SetDocumentColors](#setdocumentcolors).|  
|`m_strOtherColor`|A [CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el *otros* botón. Para obtener más información, consulte [CMFCColorBar::EnableOtherButton](#enableotherbutton).|  
  
## <a name="remarks"></a>Comentarios  
 Por lo general, no se crea un `CMFCColorBar` objeto directamente. En su lugar, el [CMFCColorMenuButton clase](../../mfc/reference/cmfccolormenubutton-class.md) (usado en menús y barras de herramientas) o el [CMFCColorButton clase](../../mfc/reference/cmfccolorbutton-class.md) crea la `CMFCColorBar` objeto.  
  
 La `CMFCColorBar` clase proporciona la funcionalidad siguiente:  
  
-   La lista de colores del documento se ajusta automáticamente.  
  
-   Guarda y restaura su estado, junto con el estado del documento.  
  
-   Administra el botón "automático".  
  
-   Usa el [CMFCColorPickerCtrl clase](../../mfc/reference/cmfccolorpickerctrl-class.md) control para seleccionar un color personalizado.  
  
-   Es compatible con un estado "desplazable" (si se crea mediante la [CMFCColorMenuButton clase](../../mfc/reference/cmfccolormenubutton-class.md)).  
  
 Para incorporar la `CMFCColorBar` funcionalidad en la aplicación:  
  
1.  Crear un botón de menú regular y asignar un Id., por ejemplo ID_CHAR_COLOR.  
  
2.  En la clase de ventana de marco, invalidar la [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) método y reemplazar el menú habitual botón con un [CMFCColorMenuButton clase](../../mfc/reference/cmfccolormenubutton-class.md) objeto (mediante una llamada a [CMFCToolBar: : ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)).  
  
3.  Establecer todos los estilos y habilitar o deshabilitar las características de la `CMFCColorBar` objeto durante la [CMFCColorMenuButton clase](../../mfc/reference/cmfccolormenubutton-class.md) creación. El `CMFCColorMenuButton` objeto crea dinámicamente la `CMFCColorBar` objeto después de las llamadas de framework la `CreatePopupMenu` método.  
  
 Cuando el usuario hace clic en un botón de control de barra de color, el marco de trabajo usa el `ON_COMMAND` macro para notificar el elemento primario del control de barra de colores. En la macro, el parámetro de identificador de comando es el valor que asigna al botón de control de barra de colores en el paso 1 (ID_CHAR_COLOR en este ejemplo). Para obtener más información, consulte el [CMFCColorMenuButton clase](../../mfc/reference/cmfccolormenubutton-class.md), [CMFCColorButton clase](../../mfc/reference/cmfccolorbutton-class.md), [CMFCColorPickerCtrl clase](../../mfc/reference/cmfccolorpickerctrl-class.md), [CFrameWndEx clase](../../mfc/reference/cframewndex-class.md), y [CMFCToolBar clase](../../mfc/reference/cmfctoolbar-class.md) clases.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar una barra de colores con varios métodos en la `CMFCColorBar` clase. Los métodos de establecer los márgenes horizontales y verticales, habilitar el otro botón, crean una ventana de control de barra de colores y establece el color seleccionado actualmente. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
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
  
##  <a name="adjustlocations"></a>CMFCColorBar::AdjustLocations  
 Ajusta las posiciones de los botones de color en el control de barra de color.  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo durante la `WM_SIZE` el procesamiento de mensajes.  
  
##  <a name="allowchangetextlabels"></a>CMFCColorBar::AllowChangeTextLabels  
 Indica si se puede cambiar la etiqueta de texto de los botones de color.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método devuelve siempre `FALSE`, lo que significa que las etiquetas de texto no se puede modificar. Invalide este método para habilitar la modificación de las etiquetas de texto.  
  
##  <a name="allowshowonlist"></a>CMFCColorBar::AllowShowOnList  
 Indica si el objeto de control de barra de colores puede aparecer en una lista de la barra de herramientas durante el proceso de personalización.  
  
```  
virtual BOOL AllowShowOnList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método devuelve siempre `TRUE`, lo que significa que el marco de trabajo puede mostrar el control de barra de color durante el proceso de personalización. Invalide este método para implementar un comportamiento diferente.  
  
##  <a name="calcsize"></a>CMFCColorBar::CalcSize  
 Lo llama el marco como parte del proceso de cálculo de diseño.  
  
```  
virtual CSize CalcSize(BOOL bVertDock);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bVertDock`  
 `TRUE`para especificar que el control de barra de colores está acoplado verticalmente; `FALSE` para especificar que el control de barra de colores está acoplado horizontalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño de la matriz de botones de color en un control de barra de color.  
  
##  <a name="cmfccolorbar"></a>CMFCColorBar::CMFCColorBar  
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
 [in] `colors`  
 Una matriz de colores que el marco de trabajo se muestra en el control de barra de color.  
  
 [in] `color`  
 El color seleccionado inicialmente.  
  
 [in] `lpszAutoColor`  
 La etiqueta de texto de la *automática* botón de color (valor predeterminado), o `NULL`.  
  
 La etiqueta para el botón automático estándar es **automática**.  
  
 [in] `lpszOtherColor`  
 La etiqueta de texto de la *otros* botón, que se presenta más opciones de color, o `NULL`.  
  
 La etiqueta estándar para el otro botón es **más colores...** .  
  
 [in] `lpszDocColors`  
 La etiqueta de texto del botón de colores del documento. La paleta de colores del documento enumera todos los colores que utiliza actualmente el documento.  
  
 [in] `lstDocColors`  
 Una lista de colores que usa actualmente el documento.  
  
 [in] `nColumns`  
 El número de columnas que tiene la matriz de colores.  
  
 [in] `nRowsDockHorz`  
 El número de filas que tiene la barra de color cuando está acoplado horizontalmente.  
  
 [in] `nColDockVert`  
 El número de columnas que tiene la barra de color cuando se acopla verticalmente.  
  
 [in] `colorAutomatic`  
 El color predeterminado que se aplica el marco de trabajo al hacer clic en el botón automático.  
  
 [in] `nCommandID`  
 Identificador de comando de control de barra de colores.  
  
 [in] `pParentBtn`  
 Un puntero a un botón primario.  
  
 [in] `src`  
 Existente `CMFCColorBar` objeto que se copiará en el nuevo `CMFCColorBar` objeto.  
  
 [in] `uiCommandID`  
 Identificador del comando.  
  
##  <a name="contexttosize"></a>CMFCColorBar::ContextToSize  
 Calcula los márgenes horizontales y verticales que son necesarios para que contenga los botones en el control de barra de color y ajusta la ubicación de estos botones.  
  
```  
void ContextToSize(
    BOOL bSquareButtons = TRUE,   
    BOOL bCenterButtons = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `bSquareButtons`|`TRUE`para especificar que la forma de los botones en un control de barra de colores sean cuadradas; en caso contrario, `FALSE`. El valor predeterminado es `TRUE`.|  
|[in] `bCenterButtons`|`TRUE`para especificar que se centra el contenido en un botón del control de barra de colores; en caso contrario, `FALSE`. El valor predeterminado es `TRUE`.|  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="create"></a>CMFCColorBar::Create  
 Crea una ventana de control de barra de colores y lo adjunta a la `CMFCColorBar` objeto.  
  
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
 [in] `pParentWnd`  
 Puntero a la ventana primaria.  
  
 [in] `dwStyle`  
 Una combinación bit a bit (OR) de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] `nID`  
 Identificador del comando.  
  
 [in] `pPalette`  
 Puntero a una paleta de colores. De manera predeterminada, es `NULL`.  
  
 [in] `nColumns`  
 El número de columnas en el control de barra de colores. El valor predeterminado es 0.  
  
 [in] `nRowsDockHorz`  
 El número de filas en el control de barra de color cuando está acoplado horizontalmente. El valor predeterminado es 0.  
  
 [in] `nColDockVert`  
 El número de columnas en el control de barra de color cuando se acopla verticalmente. El valor predeterminado es 0.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Para construir un `CMFCColorBar` de objeto, llame al constructor de la clase, a continuación, este método. El `Create` método crea el control de Windows e inicializa una lista de colores.  
  
##  <a name="createcontrol"></a>CMFCColorBar::CreateControl  
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
 [in] `pParentWnd`  
 Puntero a la ventana primaria. No puede ser `NULL`.  
  
 [in] `rect`  
 Un rectángulo delimitador que especifica dónde debe dibujar el control de barra de color.  
  
 [in] `nID`  
 El identificador del control.  
  
 [in] `nColumns`  
 El número ideal de columnas en el control de barra de colores. Este método modifica ese número para ajustar la paleta de colores especificada. El valor predeterminado es -1, lo que significa que no se especifica este parámetro.  
  
 [in] `pPalette`  
 Puntero a una paleta de colores, o `NULL`. Si este parámetro es `NULL`, este método calcula el tamaño del control de barra de colores como si se especificaron 20 colores. De manera predeterminada, es `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la `rect`, `nColumns`, y `pPalette` parámetros para calcular el número adecuado o filas y columnas en el control de barra de colores y, a continuación, llama el [CMFCColorBar::Create](#create) método.  
  
##  <a name="createpalette"></a>CMFCColorBar::CreatePalette  
 Inicializa una paleta con los colores de una matriz de colores especificada.  
  
```  
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,   
    CPalette& palette);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `arColors`|Una matriz de colores.|  
|[in] `palette`|Una paleta de colores.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
##  <a name="enableautomaticbutton"></a>CMFCColorBar::EnableAutomaticButton  
 Muestra u oculta el botón automático.  
  
```  
void EnableAutomaticButton(
    LPCTSTR lpszLabel,  
    COLORREF colorAutomatic,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 La etiqueta de texto de la *automática* botón de color (valor predeterminado), o `NULL`.  
  
 La etiqueta para el botón automático estándar es **automática**.  
  
 [in] `colorAutomatic`  
 El color predeterminado que se aplica el marco de trabajo al hacer clic en el botón automático.  
  
 [in] `bEnable`  
 `TRUE`Para habilitar el botón automático; `FALSE` para deshabilitar el botón automático. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Se elimina la etiqueta de texto del botón automática si el `lpszLabel` parámetro es `NULL` o `bEnable` parámetro es `FALSE`.  
  
##  <a name="enableotherbutton"></a>CMFCColorBar::EnableOtherButton  
 Habilita o deshabilita la presentación de un cuadro de diálogo que permite al usuario seleccionar más colores.  
  
```  
void EnableOtherButton(
    LPCTSTR lpszLabel,  
    BOOL bAltColorDlg=TRUE,  
    BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszLabel`  
 La etiqueta de texto de la *otros* botón, que se presenta más opciones de color, o `NULL`.  
  
 La etiqueta estándar para que este botón es **más colores...** .  
  
 [in] `bAltColorDlg`  
 `TRUE`para mostrar la [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuadro de diálogo; `FALSE` para mostrar el estándar [CColorDialog](../../mfc/reference/ccolordialog-class.md) cuadro de diálogo. El valor predeterminado es `TRUE`.  
  
 [in] `bEnable`  
 `TRUE`Para habilitar el botón; `FALSE` para deshabilitar el botón. El valor predeterminado es `TRUE`.  
  
##  <a name="getcolor"></a>CMFCColorBar::GetColor  
 Recupera el color seleccionado actualmente.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color seleccionado actualmente.  
  
##  <a name="getcolorgridsize"></a>CMFCColorBar::GetColorGridSize  
 Calcula el número de filas y columnas en la cuadrícula de un control de barra de colores.  
  
```  
CSize GetColorGridSize(BOOL bVertDock) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `bVertDock`|`TRUE`para realizar el cálculo de un control de barra de color acoplado verticalmente; en caso contrario, puede realizar el cálculo de un control acoplado horizontalmente.|  
  
### <a name="return-value"></a>Valor devuelto  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) cuyos `cx` componente contiene el número de columnas y cuyo `cy` componente contiene el número de filas.  
  
##  <a name="getcommandid"></a>CMFCColorBar::GetCommandID  
 Recupera el identificador de comando del control de barra de color actual.  
  
```  
UINT GetCommandID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de comando.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario selecciona un nuevo color, el marco de trabajo envía el identificador de comando en un `WM_COMMAND` mensaje para notificar el elemento primario de la `CMFCColorBar` objeto.  
  
##  <a name="getextraheight"></a>CMFCColorBar::GetExtraHeight  
 Calcula el alto adicional que requiera la barra de colores actual para mostrar los elementos de la interfaz de usuario varios, como el **otros** colores de botón o el documento.  
  
```  
int GetExtraHeight(int nNumColumns) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `nNumColumns`|Si el control de barra de colores contiene colores del documento, el número de columnas que se muestran en la cuadrícula de colores del documento. En caso contrario, no se utiliza este valor.|  
  
### <a name="return-value"></a>Valor devuelto  
 El alto adicional calculado que se necesita.  
  
##  <a name="gethighlightedcolor"></a>CMFCColorBar::GetHighlightedColor  
 Recupera el color que indica que un botón en color tiene el foco; es decir, el botón *activa*.  
  
```  
COLORREF GetHighlightedColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gethorzmargin"></a>CMFCColorBar::GetHorzMargin  
 Recupera el margen horizontal, que es el espacio entre la izquierda o la celda de color a la derecha y el límite del área cliente.  
  
```  
int GetHorzMargin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El margen horizontal.  
  
##  <a name="getvertmargin"></a>CMFCColorBar::GetVertMargin  
 Recupera el margen vertical, que es el espacio entre la parte superior o celda de color de la parte inferior y el límite del área cliente.  
  
```  
int GetVertMargin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El margen vertical.  
  
##  <a name="initcolors"></a>CMFCColorBar::InitColors  
 Inicializa una matriz de colores con los colores de una paleta especificado o con la paleta predeterminada del sistema.  
  
```  
static int InitColors(
    CPalette* pPalette,   
    CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pPalette`|Un puntero a un objeto de la paleta, o `NULL`. Si este parámetro es `NULL`, este método usa la paleta predeterminada del sistema operativo.|  
|[in] `arColors`|Una matriz de colores.|  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la matriz de colores.  
  
##  <a name="istearoff"></a>CMFCColorBar::IsTearOff  
 Indica si la barra de colores actual es acoplable.  
  
```  
BOOL IsTearOff() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de barra de colores actual es acoplable; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si el control de barra de color es acoplable, puede ser arrancado una barra de controles y acoplada en otra ubicación.  
  
##  <a name="onkey"></a>CMFCColorBar::OnKey  
 Lo llama el marco cuando el usuario presiona un botón de teclado.  
  
```  
virtual BOOL OnKey(UINT nChar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nChar`  
 El código de tecla virtual para la clave que un usuario presiona.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método procesa la clave especificada; en caso contrario, `FALSE`.  
  
##  <a name="onsendcommand"></a>CMFCColorBar::OnSendCommand  
 Lo llama el marco de trabajo para cerrar una jerarquía de controles de elementos emergentes.  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pButton`|Puntero a un control que se encuentra en una barra de herramientas.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
##  <a name="onupdatecmdui"></a>CMFCColorBar::OnUpdateCmdUI  
 Lo llama el marco para habilitar o deshabilitar un elemento de interfaz de usuario de un control de barra de color antes de que se muestre el elemento.  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTarget`  
 Puntero a una ventana que contiene un elemento de interfaz de usuario para actualizar.  
  
 [in] `bDisableIfNoHndler`  
 `TRUE`Para deshabilitar el elemento de interfaz de usuario si no hay ningún controlador se define en un mapa de mensajes; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario de la aplicación, haga clic en un elemento de interfaz de usuario, el elemento debe saber si debe mostrarse como habilitado o deshabilitado. El destino del mensaje comando proporciona esta información mediante la implementación de un `ON_UPDATE_COMMAND_UI` el controlador de comandos. Use este método para procesar el comando. Para obtener más información, consulte [CCmdUI (clase)](../../mfc/reference/ccmdui-class.md).  
  
##  <a name="opencolordialog"></a>CMFCColorBar::OpenColorDialog  
 Abre un cuadro de diálogo color.  
  
```  
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,  
    COLORREF& colorRes);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `colorDefault`  
 El color que está activado de forma predeterminada cuando se abre el cuadro de diálogo color.  
  
 [out] `colorRes`  
 El color que el usuario seleccionado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el usuario selecciona un color; `FALSE` si el usuario canceló el cuadro de diálogo color.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="rebuild"></a>CMFCColorBar::Rebuild  
 Completamente vuelve a dibujarse el control de barra de color.  
  
```  
virtual void Rebuild();
```  
  
##  <a name="selectpalette"></a>CMFCColorBar::SelectPalette  
 Establece la paleta lógica del contexto de dispositivo especificado en la paleta del botón primario del control de barra de color actual.  
  
```  
CPalette* SelectPalette(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pDC`|Puntero al contexto de dispositivo del botón primario del control de barra de color actual.|  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la paleta que se sustituye por la paleta del botón primario del control de barra de color actual.  
  
##  <a name="setcolor"></a>CMFCColorBar::SetColor  
 Establece el color que está seleccionado actualmente.  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 Un valor de color RGB.  
  
##  <a name="setcolorname"></a>CMFCColorBar::SetColorName  
 Establece un nuevo nombre para un color especificado.  
  
```  
static void SetColorName(
    COLORREF color,  
    const CString& strName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
 El valor RGB de un color.  
  
 [in] `strName`  
 El nuevo nombre para el color especificado.  
  
### <a name="remarks"></a>Comentarios  
 Este método cambia el nombre del color especificado en todos los `CMFCColorBar` objetos de la aplicación.  
  
##  <a name="setcommandid"></a>CMFCColorBar::SetCommandID  
 Establece un nuevo identificador de comando para un control de barra de color.  
  
```  
void SetCommandID(UINT nCommandID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCommandID`  
 Un identificador de comando.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para modificar el identificador de comando de un control de barra de color y para notificar a la ventana primaria del control que ha cambiado el identificador.  
  
##  <a name="setdocumentcolors"></a>CMFCColorBar::SetDocumentColors  
 Establece la lista de colores que se utilizan en el documento actual.  
  
```  
void SetDocumentColors(
    LPCTSTR lpszCaption,  
    CList<COLORREF,COLORREF>& lstDocColors,  
    BOOL bShowWhenDocked=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszCaption`  
 Título que se muestra cuando no se acopla el control de barra de color.  
  
 [in] `lstDocColors`  
 Una lista de colores que reemplaza los colores del documento actual.  
  
 [in] `bShowWhenDocked`  
 `TRUE`para mostrar los colores del documento cuando se acopla el control de barra de color; en caso contrario, `FALSE`. El valor predeterminado es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 *Colores de documento* son los colores que se usan actualmente en un documento. El marco de trabajo mantiene automáticamente una lista de colores de documento, pero puede usar este método para modificar la lista.  
  
##  <a name="sethorzmargin"></a>CMFCColorBar::SetHorzMargin  
 Establece el margen horizontal, que es el espacio entre la izquierda o celda de color a la derecha y el límite del área cliente.  
  
```  
void SetHorzMargin(int nHorzMargin);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nHorzMargin`  
 El margen horizontal, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el [CMFCColorBar::CMFCColorBar](#cmfccolorbar) constructor establece el margen horizontal en 4 píxeles.  
  
##  <a name="setproplist"></a>CMFCColorBar::SetPropList  
 Establece el `m_pWndPropList` protegido el puntero especificado a un control de cuadrícula de propiedades de miembro de datos.  
  
```  
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pWndList`|Puntero al objeto de control de cuadrícula de propiedad.|  
  
##  <a name="setvertmargin"></a>CMFCColorBar::SetVertMargin  
 Establece el margen vertical, que es el espacio entre la celda de color superior o inferior y el límite del área cliente.  
  
```  
void SetVertMargin(int nVertMargin);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nVertMargin`  
 El margen vertical, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el [CMFCColorBar::CMFCColorBar](#cmfccolorbar) constructor establece el margen vertical en 4 píxeles.  
  
##  <a name="showcommandmessagestring"></a>CMFCColorBar::ShowCommandMessageString  
 Las solicitudes de la ventana de marco que posee el control de barra de color para actualizar la línea del mensaje en la barra de estado.  
  
```  
virtual void ShowCommandMessageString(UINT uiCmdId);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmdId`  
 Un identificador de comando. (Este parámetro se omite).  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el `WM_SETMESSAGESTRING` mensaje al propietario del control de barra de colores.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
