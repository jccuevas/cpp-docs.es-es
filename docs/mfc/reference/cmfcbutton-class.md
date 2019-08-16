---
title: Clase CMFCButton
ms.date: 08/28/2018
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
helpviewer_keywords:
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
ms.openlocfilehash: 7628ac353d01c2a6853e35a35bd1f702d3bb041e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505859"
---
# <a name="cmfcbutton-class"></a>Clase CMFCButton

La `CMFCButton` clase agrega funcionalidad a la clase [CButton](../../mfc/reference/cbutton-class.md) , como alinear el texto del botón, combinar el texto del botón y una imagen, seleccionar un cursor y especificar una información sobre herramientas.

## <a name="syntax"></a>Sintaxis

```
class CMFCButton : public CButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`CMFCButton::CMFCButton`|Constructor predeterminado.|
|`CMFCButton::~CMFCButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCButton::CleanUp](#cleanup)|Restablece las variables internas y libera los recursos asignados, como imágenes, mapas de bits e iconos.|
|`CMFCButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCButton::DrawItem`|Lo llama el marco de trabajo cuando ha cambiado un aspecto visual de un botón dibujado por el propietario. (Invalida [CButton::D rawitem](../../mfc/reference/cbutton-class.md#drawitem)).|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Especifica si se va a mostrar el texto completo de una información sobre herramientas en una ventana de información sobre herramientas grande o en una versión truncada del texto en una pequeña ventana de información sobre herramientas.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Especifica si la fuente del texto del botón es igual que la fuente del menú de la aplicación.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Especifica si el estilo del borde del botón corresponde al tema actual de Windows.|
|`CMFCButton::GetThisClass`|Lo usa el marco de trabajo para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Devuelve una referencia al control ToolTip subyacente.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Indica si una casilla o un botón de radio es un botón automático.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Indica si un botón está establecido en modo de repetición automática.|
|[CMFCButton::IsCheckBox](#ischeckbox)|Indica si un botón es un botón de casilla.|
|[CMFCButton::IsChecked](#ischecked)|Indica si el botón actual está activado.|
|[CMFCButton::IsHighlighted](#ishighlighted)|Indica si un botón está resaltado.|
|[CMFCButton::IsPressed](#ispressed)|Indica si se inserta un botón y se resalta.|
|[CMFCButton::IsPushed](#ispushed)|Indica si se inserta un botón.|
|[CMFCButton::IsRadioButton](#isradiobutton)|Indica si un botón es un botón de radio.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Indica si el estilo del borde del botón corresponde al tema actual de Windows.|
|`CMFCButton::OnDrawParentBackground`|Dibuja el fondo del elemento primario de un botón en el área especificada. (Invalida [AFX_GLOBAL_DATA::D rawparentbackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Establece un botón en modo de repetición automática.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Establece la imagen de un botón activado.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Establece el color de fondo del texto del botón.|
|[CMFCButton::SetImage](#setimage)|Establece la imagen de un botón.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Establece la imagen del cursor.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Establece el cursor en la imagen de una mano.|
|[CMFCButton::SetStdImage](#setstdimage)|Utiliza un `CMenuImages` objeto para establecer la imagen del botón.|
|[CMFCButton::SetTextColor](#settextcolor)|Establece el color del texto del botón para un botón que no está seleccionado.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Establece el color del texto del botón para un botón que está seleccionado.|
|[CMFCButton::SetTooltip](#settooltip)|Asocia una información sobre herramientas a un botón.|
|[CMFCButton::SizeToContent](#sizetocontent)|Cambia el tamaño de un botón para que contenga la imagen y el texto del botón.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar un botón.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Lo llama el marco de trabajo para dibujar el borde de un botón.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Lo llama el marco de trabajo para dibujar el rectángulo de foco de un botón.|
|[CMFCButton::OnDrawText](#ondrawtext)|Lo llama el marco de trabajo para dibujar el texto del botón.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Lo llama el marco de trabajo para dibujar el fondo del texto del botón.|
|[CMFCButton::SelectFont](#selectfont)|Recupera la fuente asociada al contexto de dispositivo especificado.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Especifica la alineación del texto del botón.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Especifica si se van a usar los temas de Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Indica si se debe dibujar un rectángulo de foco alrededor de un botón.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Especifica el estilo del botón, como sin borde, plano, Semiplano o 3D.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Cuando es TRUE, permite que un botón deshabilitado se dibuje como atenuado.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Indica si se debe resaltar un botón de estilo BS_CHECKBOX cuando el cursor se desplaza sobre él.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Indica si se debe responder a los eventos de presionar el botón.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Indica si se va a mostrar una imagen en el lado derecho del botón.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Indica si la imagen está en la parte superior del botón.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Indica si el botón es transparente.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Indica si el último evento de clic fue un doble clic.|

## <a name="remarks"></a>Comentarios

Otros tipos de botones se derivan de `CMFCButton` la clase, como la clase [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) , que admite hipervínculos, y la `CMFCColorButton` clase, que admite un cuadro de diálogo Selector de colores.

El estilo de un `CMFCButton` objeto puede ser *3D*, *plana*, *semi-plana y* o *ningún borde*. El texto del botón se puede alinear a la izquierda, en la parte superior o en el centro de un botón. En tiempo de ejecución, puede controlar si el botón muestra texto, una imagen o texto y una imagen. También puede especificar que se muestre una imagen de cursor determinada cuando el cursor se desplaza sobre un botón.

Cree un control de botón directamente en el código o mediante la herramienta **Asistente para clases MFC** y una plantilla de cuadro de diálogo. Si crea un control de botón directamente, agregue una `CMFCButton` variable a la aplicación y, a continuación, llame al `Create` constructor y a `CMFCButton` los métodos del objeto. Si usa el **Asistente para clases MFC**, agregue una `CButton` variable a la aplicación y, a continuación, cambie el tipo de la `CButton` variable `CMFCButton`de a.

Para controlar los mensajes de notificación en una aplicación de cuadro de diálogo, agregue una entrada de mapa de mensajes y un controlador de eventos para cada notificación. Las notificaciones enviadas por `CMFCButton` un objeto son las mismas que las enviadas `CButton` por un objeto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar las propiedades del botón mediante el uso de varios métodos `CMFCButton` en la clase. El ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxbutton. h

##  <a name="cleanup"></a>  CMFCButton::CleanUp

Restablece las variables internas y libera los recursos asignados, como imágenes, mapas de bits e iconos.

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip

Especifica si se va a mostrar el texto completo de una información sobre herramientas en una ventana de información sobre herramientas grande o en una versión truncada del texto en una pequeña ventana de información sobre herramientas.

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Parámetros

*bOn*<br/>
de TRUE para mostrar todo el texto; FALSE para mostrar el texto truncado.

### <a name="remarks"></a>Comentarios

##  <a name="enablemenufont"></a>CMFCButton::EnableMenuFont

Especifica si la fuente del texto del botón es igual que la fuente del menú de la aplicación.

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*bOn*<br/>
de TRUE para usar la fuente del menú de la aplicación como fuente del texto del botón; FALSE para usar la fuente del sistema. El valor predeterminado es TRUE.

*bRedraw*<br/>
de TRUE para volver a dibujar la pantalla inmediatamente; en caso contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

Si no usa este método para especificar la fuente del texto del botón, puede especificar la fuente con el método [CWnd:: SetFont](../../mfc/reference/cwnd-class.md#setfont) . Si no especifica una fuente, el marco de trabajo establece una fuente predeterminada.

##  <a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

Especifica si el estilo del borde del botón corresponde al tema actual de Windows.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de TRUE para usar el tema actual de Windows para dibujar los bordes del botón; FALSE para no usar el tema de Windows. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

Este método afecta a todos los botones de la aplicación que se derivan de la `CMFCButton` clase.

##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl

Devuelve una referencia al control ToolTip subyacente.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Valor devuelto

Referencia al control ToolTip subyacente.

### <a name="remarks"></a>Comentarios

##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck

Indica si una casilla o un botón de radio es un botón automático.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el botón tiene el estilo BS_AUTOCHECKBOX o BS_AUTORADIOBUTTON; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode

Indica si un botón está establecido en modo de repetición automática.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el botón está establecido en modo de repetición automática; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use el método [CMFCButton:: SetAutorepeatMode](#setautorepeatmode) para establecer un botón en modo de repetición automática.

##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox

Indica si un botón es un botón de casilla.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el botón tiene el estilo BS_CHECKBOX o BS_AUTOCHECKBOX; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="ischecked"></a>CMFCButton:: IsChecked

Indica si el botón actual está activado.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el botón actual está activado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El marco de trabajo utiliza diferentes maneras de indicar que se comprueban diferentes tipos de botones. Por ejemplo, se comprueba un botón de radio cuando contiene un punto; se activa una casilla cuando contiene una **X**.

##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted

Indica si un botón está resaltado.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el botón está resaltado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Un botón se resalta cuando se mantiene el mouse sobre el botón.

##  <a name="ispressed"></a>  CMFCButton::IsPressed

Indica si se inserta un botón y se resalta.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se presiona el botón; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="ispushed"></a>  CMFCButton::IsPushed

Indica si se inserta un botón.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se inserta el botón; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton

Indica si un botón es un botón de radio.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el estilo del botón es BS_RADIOBUTTON o BS_AUTORADIOBUTTON; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled

Indica si el estilo del borde del botón corresponde al tema actual de Windows.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el estilo del borde del botón corresponde al tema actual de Windows; en caso contrario, FALSE.

## <a name="a-namem_bdontusewinxptheme-cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/> CMFCButton::m_bDontUseWinXPTheme

Especifica si se deben usar los temas de Windows XP al dibujar el botón.

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus

Indica si se debe dibujar un rectángulo de foco alrededor de un botón.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Comentarios

Establezca el `m_bDrawFocus` miembro en true para especificar que el marco de trabajo dibujará un rectángulo de foco alrededor de la imagen y el texto del botón si el botón recibe el foco.

El `CMFCButton` constructor inicializa este miembro como true.

##  <a name="m_bGrayDisabled"></a>  CMFCButton::m_bGrayDisabled

Cuando es TRUE, permite que un botón deshabilitado se dibuje como atenuado.

```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked

Indica si se debe resaltar un botón de estilo BS_CHECKBOX cuando el cursor se desplaza sobre él.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Comentarios

Establezca el `m_bHighlightChecked` miembro en true para especificar que el marco resaltará un botón de estilo BS_CHECKBOX cuando el mouse se desplace sobre él.

##  <a name="m_bResponseOnButtonDown"></a> CMFCButton::m_bResponseOnButtonDown

Indica si se debe responder a los eventos de presionar el botón.

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage

Indica si se va a mostrar una imagen en el lado derecho del botón.

```
BOOL m_bRightImage;
```

##  <a name="m_bTopImage"></a>  CMFCButton::m_bTopImage](#m_bTopImage)

Indica si la imagen está en la parte superior del botón.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Comentarios

Establezca el `m_bRightImage` miembro en true para especificar que el marco de trabajo mostrará la imagen del botón a la derecha de la etiqueta de texto del botón.

##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent

Indica si el botón es transparente.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Comentarios

Establezca el `m_bTransparent` miembro en true para especificar que el marco hará que el botón sea transparente. El `CMFCButton` constructor inicializa este miembro en false.

##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle

Especifica la alineación del texto del botón.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Comentarios

Use uno de los siguientes `CMFCButton::AlignStyle` valores de enumeración para especificar la alineación del texto del botón:

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|ALIGN_CENTER|Predeterminada Alinea el texto del botón en el centro del botón.|
|ALIGN_LEFT|Alinea el texto del botón en el lado izquierdo del botón.|
|ALIGN_RIGHT|Alinea el texto del botón a la parte derecha del botón.|

El `CMFCButton` constructor inicializa este miembro en ALIGN_CENTER.

##  <a name="m_bWasDblClk"></a>  CMFCButton::m_bWasDblClk](#m_bWasDblClk)|

Indica si el último evento de clic fue un doble clic. |

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle

Especifica el estilo del botón, como sin borde, plano, Semiplano o 3D.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Comentarios

En la tabla siguiente se `CMFCButton::m_nFlatStyle` enumeran los valores de enumeración que especifican la apariencia de un botón.

|Value|DESCRIPCIÓN|
|-----------|-----------------|
|BUTTONSTYLE_3D|Predeterminada El botón parece tener lados altos de tres dimensiones. Cuando se hace clic en el botón, el botón aparece presionado en una sangría profunda.|
|BUTTONSTYLE_FLAT|Cuando el mouse no se detiene sobre el botón, parece que el botón es bidimensional y no tiene lados elevados. Cuando el mouse se detiene sobre el botón, el botón parece tener lados inferiores de tres dimensiones. Cuando se hace clic en el botón, el botón aparece presionado en una sangría superficial.|
|BUTTONSTYLE_SEMIFLAT|El botón parece tener lados inferiores de tres dimensiones. Cuando se hace clic en el botón, el botón aparece presionado en una sangría profunda.|
|BUTTONSTYLE_NOBORDERS|El botón no tiene lados elevados y siempre aparece bidimensional. El botón no parece estar presionado en una sangría cuando se hace clic en él.|

El `CMFCButton` constructor inicializa este miembro en BUTTONSTYLE_3D.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer los valores de `m_nFlatStyle` la variable miembro en `CMFCButton` la clase. Este ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

##  <a name="ondraw"></a>CMFCButton:: OnDraw

Lo llama el marco de trabajo para dibujar un botón.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contexto de dispositivo.

*rect*<br/>
de Referencia a un rectángulo que delimita el botón.

*uiState*<br/>
de Estado actual del botón. Para obtener más información, vea `itemState` el tema sobre el miembro de la [estructura drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) .

### <a name="remarks"></a>Comentarios

Invalide este método para usar su propio código para dibujar un botón.

##  <a name="ondrawborder"></a>CMFCButton::OnDrawBorder

Lo llama el marco de trabajo para dibujar el borde de un botón.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contexto de dispositivo.

*rectClient*<br/>
de Referencia a un rectángulo que delimita el botón.

*uiState*<br/>
de Estado actual del botón. Para obtener más información, vea `itemState` el tema sobre el miembro de la [estructura drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) .

### <a name="remarks"></a>Comentarios

Invalide este método para usar su propio código para dibujar el borde.

##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect

Lo llama el marco de trabajo para dibujar el rectángulo de foco de un botón.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contexto de dispositivo.

*rectClient*<br/>
de Referencia a un rectángulo que delimita el botón.

### <a name="remarks"></a>Comentarios

Invalide este método para usar su propio código para dibujar el rectángulo de foco.

##  <a name="ondrawtext"></a>  CMFCButton::OnDrawText

Lo llama el marco de trabajo para dibujar el texto del botón.

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contexto de dispositivo.

*rect*<br/>
de Referencia a un rectángulo que delimita el botón.

*strText*<br/>
de Texto que se va a dibujar.

*uiDTFlags*<br/>
de Marcas que especifican cómo dar formato al texto. Para obtener más información, vea el parámetro *nFormat* del método [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext) .

*uiState*<br/>
[in] Reservado.

### <a name="remarks"></a>Comentarios

Invalide este método para usar su propio código para dibujar el texto del botón.

##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground

Lo llama el marco de trabajo para dibujar el fondo del texto del botón.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contexto de dispositivo.

*rectClient*<br/>
de Referencia a un rectángulo que delimita el botón.

### <a name="remarks"></a>Comentarios

Invalide este método para usar su propio código para dibujar el fondo de un botón.

##  <a name="selectfont"></a>  CMFCButton::SelectFont

Recupera la fuente asociada al contexto de dispositivo especificado.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de Un puntero a un contexto de dispositivo.

### <a name="return-value"></a>Valor devuelto

Invalide este método para usar su propio código para recuperar la fuente.

### <a name="remarks"></a>Comentarios

##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode

Establece un botón en modo de repetición automática.

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Parámetros

*nTimeDelay*<br/>
de Un número no negativo que especifica el intervalo entre los mensajes que se envían a la ventana primaria. El intervalo se mide en milisegundos y su valor predeterminado es 500 milisegundos. Especifique cero para deshabilitar el modo de mensaje de repetición automática.

### <a name="remarks"></a>Comentarios

Este método hace que el botón envíe constantemente mensajes WM_COMMAND a la ventana primaria hasta que se libere el botón o el parámetro *nTimeDelay* se establezca en cero.

##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage

Establece la imagen de un botón activado.

```
void SetCheckedImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetCheckedImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetCheckedImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
de Identificador del icono que contiene el mapa de bits y la máscara de la nueva imagen.

*bAutoDestroy*<br/>
de TRUE para especificar que los recursos de mapa de bits se destruyan automáticamente; en caso contrario, FALSE. El valor predeterminado es TRUE.

*hIconHot*<br/>
de Identificador del icono que contiene la imagen para el estado seleccionado.

*hBitmap*<br/>
de Identificador del mapa de bits que contiene la imagen para el estado no seleccionado.

*hBitmapHot*<br/>
de Identificador del mapa de bits que contiene la imagen para el estado seleccionado.

*bMap3dColors*<br/>
de Especifica un color transparente para el fondo del botón. es decir, el aspecto del botón. TRUE para usar el valor de color RGB (192, 192, 192); FALSE para usar el valor de color definido `AFX_GLOBAL_DATA::clrBtnFace`por.

*uiBmpResId*<br/>
de IDENTIFICADOR de recurso de la imagen no seleccionada.

*uiBmpHotResId*<br/>
de IDENTIFICADOR de recurso de la imagen seleccionada.

*hIconDisabled*<br/>
de Identificador del icono de la imagen deshabilitada.

*hBitmapDisabled*<br/>
de Identificador del mapa de bits que contiene la imagen deshabilitada.

*uiBmpDsblResID*<br/>
de IDENTIFICADOR de recurso del mapa de bits deshabilitado.

*bAlphaBlend*<br/>
de TRUE para usar solo imágenes de 32 bits que utilizan el canal alfa; FALSE, para no usar solo imágenes de canal alfa. El valor predeterminado es FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor

Establece el color de fondo del texto del botón.

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*crFace*<br/>
de Valor de color RGB.

*bRedraw*<br/>
de TRUE para volver a dibujar la pantalla inmediatamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Utilice este método para definir un nuevo color de relleno para el fondo del botón (la esfera). Tenga en cuenta que el fondo no se rellena cuando la variable miembro [CMFCButton:: m_bTransparent](#m_btransparent) es true.

##  <a name="setimage"></a>  CMFCButton::SetImage

Establece la imagen de un botón.

```
void SetImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>Parámetros

*hIcon*<br/>
de Identificador del icono que contiene el mapa de bits y la máscara de la nueva imagen.

*bAutoDestroy*<br/>
de TRUE para especificar que los recursos de mapa de bits se destruyan automáticamente; en caso contrario, FALSE. El valor predeterminado es TRUE.

*hIconHot*<br/>
de Identificador del icono que contiene la imagen para el estado seleccionado.

*hBitmap*<br/>
de Identificador del mapa de bits que contiene la imagen para el estado no seleccionado.

*hBitmapHot*<br/>
de Identificador del mapa de bits que contiene la imagen para el estado seleccionado.

*uiBmpResId*<br/>
de IDENTIFICADOR de recurso de la imagen no seleccionada.

*uiBmpHotResId*<br/>
de IDENTIFICADOR de recurso de la imagen seleccionada.

*bMap3dColors*<br/>
de Especifica un color transparente para el fondo del botón. es decir, el aspecto del botón. TRUE para usar el valor de color RGB (192, 192, 192); FALSE para usar el valor de color definido `AFX_GLOBAL_DATA::clrBtnFace`por.

*hIconDisabled*<br/>
de Identificador del icono de la imagen deshabilitada.

*hBitmapDisabled*<br/>
de Identificador del mapa de bits que contiene la imagen deshabilitada.

*uiBmpDsblResID*<br/>
de IDENTIFICADOR de recurso del mapa de bits deshabilitado.

*bAlphaBlend*<br/>
de TRUE para usar solo imágenes de 32 bits que utilizan el canal alfa; FALSE, para no usar solo imágenes de canal alfa. El valor predeterminado es FALSE.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar varias versiones del `SetImage` método en la `CMFCButton` clase. El ejemplo forma parte del [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor

Establece la imagen del cursor.

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Parámetros

*hcursor*<br/>
de Identificador de un cursor.

### <a name="remarks"></a>Comentarios

Utilice este método para asociar una imagen de cursor, como el cursor de mano, con el botón. El cursor se carga desde los recursos de la aplicación.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `SetMouseCursor` el método en `CMFCButton` la clase. El ejemplo forma parte del código en el [ejemplo de nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand

Establece el cursor en la imagen de una mano.

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>Comentarios

Utilice este método para asociar la imagen de cursor de una mano con el botón. El cursor se carga desde los recursos de la aplicación.

##  <a name="setstdimage"></a>  CMFCButton::SetStdImage

Utiliza un `CMenuImages` objeto para establecer la imagen del botón.

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
de Uno de los identificadores de imagen de botón que se define `CMenuImage::IMAGES_IDS` en la enumeración. Los valores de imagen especifican imágenes como flechas, PIN y botones de radio.

*state*<br/>
de Uno de los identificadores de estado de imagen de botón que se `CMenuImages::IMAGE_STATE` define en la enumeración. Los Estados de la imagen especifican los colores del botón, como el negro, el gris, el gris claro, el blanco y el gris oscuro. El valor predeterminado es `CMenuImages::ImageBlack`.

*idDisabled*<br/>
de Uno de los identificadores de imagen de botón que se define `CMenuImage::IMAGES_IDS` en la enumeración. La imagen indica que el botón está deshabilitado. El valor predeterminado es la primera imagen del botón `CMenuImages::IdArrowDown`().

### <a name="remarks"></a>Comentarios

##  <a name="settextcolor"></a>  CMFCButton::SetTextColor

Establece el color del texto del botón para un botón que no está seleccionado.

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Parámetros

*clrText*<br/>
de Valor de color RGB.

### <a name="remarks"></a>Comentarios

##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor

Establece el color del texto del botón para un botón que está seleccionado.

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Parámetros

*clrTextHot*<br/>
de Valor de color RGB.

### <a name="remarks"></a>Comentarios

##  <a name="settooltip"></a>CMFCButton:: SetTooltip

Asocia una información sobre herramientas a un botón.

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Parámetros

*lpszToolTipText*<br/>
de Puntero al texto de la información sobre herramientas. Especifique NULL para deshabilitar la información sobre herramientas.

### <a name="remarks"></a>Comentarios

##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent

Cambia el tamaño de un botón para que contenga la imagen y el texto del botón.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parámetros

*bCalcOnly*<br/>
de TRUE para calcular, pero no cambiar, el nuevo tamaño del botón; FALSE para cambiar el tamaño del botón. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

`CSize` Objeto que contiene el nuevo tamaño del botón.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método calcula un nuevo tamaño que incluye un margen horizontal de 10 píxeles y un margen vertical de 5 píxeles.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl (clase)](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton (clase)](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton (clase)](../../mfc/reference/cmfcmenubutton-class.md)
