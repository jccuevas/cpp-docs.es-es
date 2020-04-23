---
title: CMFCButton (Clase)
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
ms.openlocfilehash: e949feaaac3570e1518cfb488cc1c42a471a1c46
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754871"
---
# <a name="cmfcbutton-class"></a>CMFCButton (Clase)

La `CMFCButton` clase agrega funcionalidad a la clase [CButton,](../../mfc/reference/cbutton-class.md) como alinear el texto del botón, combinar texto de botón y una imagen, seleccionar un cursor y especificar una información sobre herramientas.

## <a name="syntax"></a>Sintaxis

```
class CMFCButton : public CButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|`CMFCButton::CMFCButton`|Constructor predeterminado.|
|`CMFCButton::~CMFCButton`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCButton::CleanUp](#cleanup)|Restablece las variables internas y libera los recursos asignados, como imágenes, mapas de bits e iconos.|
|`CMFCButton::CreateObject`|Usado por el marco de trabajo para crear una instancia dinámica de este tipo de clase.|
|`CMFCButton::DrawItem`|Llamado por el marco de trabajo cuando un aspecto visual de un botón dibujado por el propietario ha cambiado. (Reemplaza [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Especifica si se debe mostrar el texto completo de una información sobre herramientas en una ventana de información sobre herramientas grande o una versión truncada del texto en una pequeña ventana de información sobre herramientas.|
|[CMFCButton::EnableMenuFont](#enablemenufont)|Especifica si la fuente de texto del botón es la misma que la fuente del menú de la aplicación.|
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Especifica si el estilo del borde del botón corresponde al tema actual de Windows.|
|`CMFCButton::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Devuelve una referencia al control de información sobre herramientas subyacente.|
|[CMFCButton::IsAutoCheck](#isautocheck)|Indica si una casilla de verificación o un botón de opción es un botón automático.|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Indica si un botón está configurado en modo de repetición automática.|
|[CMFCButton::IsCheckBox](#ischeckbox)|Indica si un botón es un botón de casilla de verificación.|
|[CMFCButton::IsChecked](#ischecked)|Indica si el botón actual está activado.|
|[CMFCButton::IsHighlighted](#ishighlighted)|Indica si un botón está resaltado.|
|[CMFCButton::IsPressed](#ispressed)|Indica si un botón está presionado y resaltado.|
|[CMFCButton::IsPushed](#ispushed)|Indica si se presiona un botón.|
|[CMFCButton::IsRadioButton](#isradiobutton)|Indica si un botón es un botón de opción.|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Indica si el estilo del borde del botón corresponde al tema actual de Windows.|
|`CMFCButton::OnDrawParentBackground`|Dibuja el fondo del elemento primario de un botón en el área especificada. (Reemplaza [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|
|`CMFCButton::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se distribuyan a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Establece un botón en modo de repetición automática.|
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Establece la imagen de un botón activado.|
|[CMFCButton::SetFaceColor](#setfacecolor)|Establece el color de fondo del texto del botón.|
|[CMFCButton::SetImage](#setimage)|Establece la imagen de un botón.|
|[CMFCButton::SetMouseCursor](#setmousecursor)|Establece la imagen del cursor.|
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Establece el cursor en la imagen de una mano.|
|[CMFCButton::SetStdImage](#setstdimage)|Utiliza `CMenuImages` un objeto para establecer la imagen del botón.|
|[CMFCButton::SetTextColor](#settextcolor)|Establece el color del texto del botón para un botón que no está seleccionado.|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Establece el color del texto del botón para un botón seleccionado.|
|[CMFCButton::SetTooltip](#settooltip)|Asocia una información sobre herramientas con un botón.|
|[CMFCButton::SizeToContent](#sizetocontent)|Cambia el tamaño de un botón para que contenga el texto y la imagen del botón.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCButton::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar un botón.|
|[CMFCButton::OnDrawBorder](#ondrawborder)|Llamado por el marco de trabajo para dibujar el borde de un botón.|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Llamado por el marco de trabajo para dibujar el rectángulo de foco para un botón.|
|[CMFCButton::OnDrawText](#ondrawtext)|Llamado por el marco de trabajo para dibujar el texto del botón.|
|[CMFCButton::OnFillBackground](#onfillbackground)|Llamado por el marco de trabajo para dibujar el fondo del texto del botón.|
|[CMFCButton::SelectFont](#selectfont)|Recupera la fuente asociada al contexto de dispositivo especificado.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Especifica la alineación del texto del botón.|
|[CMFCButton::m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Especifica si se deben utilizar temas de Windows XP.|
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Indica si se debe dibujar un rectángulo de foco alrededor de un botón.|
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Especifica el estilo del botón, como sin bordes, plano, semiplano o 3D.|
|[CMFCButton::m_bGrayDisabled](#m_bGrayDisabled)|Cuando TRUE, habilita un botón deshabilitado para dibujar se dibuja como atenuado.|
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Indica si se debe resaltar un botón de estilo BS_CHECKBOX cuando el cursor se desplaza sobre él.|
|[CMFCButton::m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|Indica si se debe responder a eventos de botón hacia abajo.|
|[CMFCButton::m_bRightImage](#m_brightimage)|Indica si se debe mostrar una imagen en el lado derecho del botón.|
|[CMFCButton::m_bTopImage](#m_bTopImage)| Indica si la imagen está enlaparte del botón.|
|[CMFCButton::m_bTransparent](#m_btransparent)|Indica si el botón es transparente.|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| Indica si el último evento de clic fue un doble clic.|

## <a name="remarks"></a>Observaciones

Otros tipos de botones `CMFCButton` se derivan de la clase, como la [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) clase, que admite hipervínculos y la `CMFCColorButton` clase, que admite un cuadro de diálogo selector de color.

El estilo `CMFCButton` de un objeto puede ser *3D,* *plano,* *semiplano* o *sin borde.* El texto del botón se puede alinear a la izquierda, la parte superior o el centro de un botón. En tiempo de ejecución, puede controlar si el botón muestra texto, una imagen o texto y una imagen. También puede especificar que se muestre una imagen de cursor determinada cuando el cursor se pase sobre un botón.

Cree un control de botón directamente en el código o mediante la herramienta **Asistente para clases MFC** y una plantilla de cuadro de diálogo. Si crea un control de `CMFCButton` botón directamente, agregue una `Create` variable a `CMFCButton` la aplicación y, a continuación, llame al constructor y los métodos del objeto. Si utiliza el **Asistente para clases MFC**, agregue una `CButton` variable a `CButton` `CMFCButton`la aplicación y, a continuación, cambie el tipo de la variable de a .

Para controlar los mensajes de notificación en una aplicación de cuadro de diálogo, agregue una entrada de mapa de mensajes y un controlador de eventos para cada notificación. Las notificaciones enviadas por un `CMFCButton` objeto son `CButton` las mismas que las enviadas por un objeto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo configurar las propiedades `CMFCButton` del botón mediante varios métodos en la clase. El ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

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

**Encabezado:** afxbutton.h

## <a name="cmfcbuttoncleanup"></a><a name="cleanup"></a>CMFCButton::CleanUp

Restablece las variables internas y libera los recursos asignados, como imágenes, mapas de bits e iconos.

```
virtual void CleanUp();
```

## <a name="cmfcbuttonenablefulltexttooltip"></a><a name="enablefulltexttooltip"></a>CMFCButton::EnableFullTextTooltip

Especifica si se debe mostrar el texto completo de una información sobre herramientas en una ventana de información sobre herramientas grande o una versión truncada del texto en una pequeña ventana de información sobre herramientas.

```cpp
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>Parámetros

*Bon*<br/>
[en] TRUE para mostrar todo el texto; FALSE para mostrar texto truncado.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonenablemenufont"></a><a name="enablemenufont"></a>CMFCButton::EnableMenuFont

Especifica si la fuente de texto del botón es la misma que la fuente del menú de la aplicación.

```cpp
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*Bon*<br/>
[en] TRUE para utilizar la fuente del menú de la aplicación como fuente de texto del botón; FALSE para utilizar la fuente del sistema. El valor predeterminado es TRUE.

*bRedraw*<br/>
[en] TRUE para volver a dibujar inmediatamente la pantalla; de lo contrario, FALSE. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

Si no utiliza este método para especificar la fuente de texto del botón, puede especificar la fuente con el [CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont) método. Si no especifica una fuente en absoluto, el marco de trabajo establece una fuente predeterminada.

## <a name="cmfcbuttonenablewindowstheming"></a><a name="enablewindowstheming"></a>CMFCButton::EnableWindowsTheming

Especifica si el estilo del borde del botón corresponde al tema actual de Windows.

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para usar el tema actual de Windows para dibujar bordes de botón; FALSE para no utilizar el tema de Windows. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

Este método afecta a todos los botones `CMFCButton` de la aplicación que se derivan de la clase.

## <a name="cmfcbuttongettooltipctrl"></a><a name="gettooltipctrl"></a>CMFCButton::GetToolTipCtrl

Devuelve una referencia al control de información sobre herramientas subyacente.

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>Valor devuelto

Una referencia al control de información sobre herramientas subyacente.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonisautocheck"></a><a name="isautocheck"></a>CMFCButton::IsAutoCheck

Indica si una casilla de verificación o un botón de opción es un botón automático.

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el botón tiene BS_AUTOCHECKBOX de estilo o BS_AUTORADIOBUTTON; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonisautorepeatcommandmode"></a><a name="isautorepeatcommandmode"></a>CMFCButton::IsAutorepeatCommandMode

Indica si un botón está configurado en modo de repetición automática.

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el botón está establecido en modo de repetición automática; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice el [método CMFCButton::SetAutorepeatMode](#setautorepeatmode) para establecer un botón en modo de repetición automática.

## <a name="cmfcbuttonischeckbox"></a><a name="ischeckbox"></a>CMFCButton::IsCheckBox

Indica si un botón es un botón de casilla de verificación.

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el botón tiene BS_CHECKBOX o BS_AUTOCHECKBOX estilo; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonischecked"></a><a name="ischecked"></a>CMFCButton::IsChecked

Indica si el botón actual está activado.

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se marca el botón actual; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

El marco de trabajo utiliza diferentes maneras de indicar que se comprueban diferentes tipos de botones. Por ejemplo, un botón de opción se comprueba cuando contiene un punto; una casilla de verificación está marcada cuando contiene una **X**.

## <a name="cmfcbuttonishighlighted"></a><a name="ishighlighted"></a>CMFCButton::IsHighlighted

Indica si un botón está resaltado.

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se resalta el botón; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Un botón se resalta cuando el ratón pasa el ratón sobre el botón.

## <a name="cmfcbuttonispressed"></a><a name="ispressed"></a>CMFCButton::IsPressed

Indica si un botón está presionado y resaltado.

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se pulsa el botón; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonispushed"></a><a name="ispushed"></a>CMFCButton::IsPushed

Indica si se presiona un botón.

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se presiona el botón; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonisradiobutton"></a><a name="isradiobutton"></a>CMFCButton::IsRadioButton

Indica si un botón es un botón de opción.

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el estilo de botón es BS_RADIOBUTTON o BS_AUTORADIOBUTTON; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttoniswindowsthemingenabled"></a><a name="iswindowsthemingenabled"></a>CMFCButton::IsWindowsThemingEnabled

Indica si el estilo del borde del botón corresponde al tema actual de Windows.

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>Valor devuelto

TRUESi el estilo del borde del botón corresponde al tema actual de Windows; de lo contrario, FALSE.

## <a name="cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton::m_bDontUseWinXPTheme

Especifica si se deben utilizar temas de Windows XP al dibujar el botón.

```
BOOL m_bDontUseWinXPTheme;
```

## <a name="cmfcbuttonm_bdrawfocus"></a><a name="m_bdrawfocus"></a>CMFCButton::m_bDrawFocus

Indica si se debe dibujar un rectángulo de foco alrededor de un botón.

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Observaciones

Establezca `m_bDrawFocus` el miembro en TRUE para especificar que el marco de trabajo dibujará un rectángulo de foco alrededor del texto y la imagen del botón si el botón recibe el foco.

El `CMFCButton` constructor inicializa este miembro en TRUE.

## <a name="cmfcbuttonm_bgraydisabled"></a><a name="m_bGrayDisabled"></a>CMFCButton::m_bGrayDisabled

Cuando TRUE, habilita un botón deshabilitado para dibujar se dibuja como atenuado.

```
BOOL m_bGrayDisabled;
```

## <a name="cmfcbuttonm_bhighlightchecked"></a><a name="m_bhighlightchecked"></a>CMFCButton::m_bHighlightChecked

Indica si se debe resaltar un botón de estilo BS_CHECKBOX cuando el cursor se desplaza sobre él.

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Observaciones

Establezca `m_bHighlightChecked` el miembro en TRUE para especificar que el marco de trabajo resaltará un botón de estilo BS_CHECKBOX cuando el mouse se pase sobre él.

## <a name="cmfcbuttonm_bresponseonbuttondown"></a><a name="m_bResponseOnButtonDown"></a>CMFCButton::m_bResponseOnButtonDown

Indica si se debe responder a eventos de botón hacia abajo.

```
BOOL m_bResponseOnButtonDown;
```

## <a name="cmfcbuttonm_brightimage"></a><a name="m_brightimage"></a>CMFCButton::m_bRightImage

Indica si se debe mostrar una imagen en el lado derecho del botón.

```
BOOL m_bRightImage;
```

## <a name="cmfcbuttonm_btopimagem_btopimage"></a><a name="m_bTopImage"></a>CMFCButton::m_bTopImage](#m_bTopImage)

Indica si la imagen está enlaparte del botón.

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Observaciones

Establezca `m_bRightImage` el miembro en TRUE para especificar que el marco de trabajo mostrará la imagen del botón a la derecha de la etiqueta de texto del botón.

## <a name="cmfcbuttonm_btransparent"></a><a name="m_btransparent"></a>CMFCButton::m_bTransparent

Indica si el botón es transparente.

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Observaciones

Establezca `m_bTransparent` el miembro en TRUE para especificar que el marco de trabajo hará que el botón sea transparente. El `CMFCButton` constructor inicializa este miembro en FALSE.

## <a name="cmfcbuttonm_nalignstyle"></a><a name="m_nalignstyle"></a>CMFCButton::m_nAlignStyle

Especifica la alineación del texto del botón.

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Observaciones

Utilice uno de `CMFCButton::AlignStyle` los siguientes valores de enumeración para especificar la alineación del texto del botón:

|Value|Descripción|
|-----------|-----------------|
|ALIGN_CENTER|(Predeterminado) Alinea el texto del botón con el centro del botón.|
|ALIGN_LEFT|Alinea el texto del botón con el lado izquierdo del botón.|
|ALIGN_RIGHT|Alinea el texto del botón con el lado derecho del botón.|

El `CMFCButton` constructor inicializa este miembro en ALIGN_CENTER.

## <a name="cmfcbuttonm_bwasdblclkm_bwasdblclk"></a><a name="m_bWasDblClk"></a>CMFCButton::m_bWasDblClk](#m_bWasDblClk)

Indica si el último evento de clic fue un doble clic.

```
BOOL m_bWasDblClk;
```

## <a name="cmfcbuttonm_nflatstyle"></a><a name="m_nflatstyle"></a>CMFCButton::m_nFlatStyle

Especifica el estilo del botón, como sin bordes, plano, semiplano o 3D.

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Observaciones

En la tabla `CMFCButton::m_nFlatStyle` siguiente se enumeran los valores de enumeración que especifican la apariencia de un botón.

|Value|Descripción|
|-----------|-----------------|
|BUTTONSTYLE_3D|(Predeterminado) El botón parece tener lados altos y tridimensionales. Cuando se hace clic en el botón, el botón parece ser presionado en una sangría profunda.|
|BUTTONSTYLE_FLAT|Cuando el ratón no se detiene sobre el botón, el botón parece ser bidimensional y no tiene lados elevados. Cuando el ratón se detiene sobre el botón, el botón parece tener lados bajos y tridimensionales. Cuando se hace clic en el botón, el botón parece ser presionado en una sangría superficial.|
|BUTTONSTYLE_SEMIFLAT|El botón parece tener lados bajos y tridimensionales. Cuando se hace clic en el botón, el botón parece ser presionado en una sangría profunda.|
|BUTTONSTYLE_NOBORDERS|El botón no tiene lados elevados y siempre aparece bidimensional. El botón no parece estar presionado en una sangría cuando se hace clic en él.|

El `CMFCButton` constructor inicializa este miembro en BUTTONSTYLE_3D.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `m_nFlatStyle` cómo establecer `CMFCButton` los valores de la variable miembro en la clase. Este ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

## <a name="cmfcbuttonondraw"></a><a name="ondraw"></a>CMFCButton::OnDraw

Llamado por el marco de trabajo para dibujar un botón.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] Una referencia a un rectángulo que limita el botón.

*uiState*<br/>
[en] El estado actual del botón. Para obtener más `itemState` información, vea el miembro de la [estructura DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) tema.

### <a name="remarks"></a>Observaciones

Invalide este método para usar su propio código para dibujar un botón.

## <a name="cmfcbuttonondrawborder"></a><a name="ondrawborder"></a>CMFCButton::OnDrawBorder

Llamado por el marco de trabajo para dibujar el borde de un botón.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*rectClient*<br/>
[en] Una referencia a un rectángulo que limita el botón.

*uiState*<br/>
[en] El estado actual del botón. Para obtener más `itemState` información, vea el miembro de la [estructura DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) tema.

### <a name="remarks"></a>Observaciones

Invalide este método para usar su propio código para dibujar el borde.

## <a name="cmfcbuttonondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCButton::OnDrawFocusRect

Llamado por el marco de trabajo para dibujar el rectángulo de foco para un botón.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*rectClient*<br/>
[en] Una referencia a un rectángulo que limita el botón.

### <a name="remarks"></a>Observaciones

Invalide este método para usar su propio código para dibujar el rectángulo de foco.

## <a name="cmfcbuttonondrawtext"></a><a name="ondrawtext"></a>CMFCButton::OnDrawText

Llamado por el marco de trabajo para dibujar el texto del botón.

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
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] Una referencia a un rectángulo que limita el botón.

*strText*<br/>
[en] El texto que se desea dibujar.

*uiDTFlags*<br/>
[en] Indicadores que especifican cómo dar formato al texto. Para obtener más información, vea el *nFormat* parámetro de la [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) método.

*uiState*<br/>
[in] Reservado.

### <a name="remarks"></a>Observaciones

Invalide este método para usar su propio código para dibujar el texto del botón.

## <a name="cmfcbuttononfillbackground"></a><a name="onfillbackground"></a>CMFCButton::OnFillBackground

Llamado por el marco de trabajo para dibujar el fondo del texto del botón.

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*rectClient*<br/>
[en] Una referencia a un rectángulo que limita el botón.

### <a name="remarks"></a>Observaciones

Invalide este método para usar su propio código para dibujar el fondo de un botón.

## <a name="cmfcbuttonselectfont"></a><a name="selectfont"></a>CMFCButton::SelectFont

Recupera la fuente asociada al contexto de dispositivo especificado.

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

### <a name="return-value"></a>Valor devuelto

Invalide este método para usar su propio código para recuperar la fuente.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonsetautorepeatmode"></a><a name="setautorepeatmode"></a>CMFCButton::SetAutorepeatMode

Establece un botón en modo de repetición automática.

```cpp
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>Parámetros

*nTimeDelay*<br/>
[en] Número no negativo que especifica el intervalo entre los mensajes que se envían a la ventana primaria. El intervalo se mide en milisegundos y su valor predeterminado es 500 milisegundos. Especifique cero para deshabilitar el modo de mensaje de repetición automática.

### <a name="remarks"></a>Observaciones

Este método hace que el botón envíe constantemente mensajes de WM_COMMAND a la ventana primaria hasta que se libere el botón o el *nTimeDelay* parámetro se establece en cero.

## <a name="cmfcbuttonsetcheckedimage"></a><a name="setcheckedimage"></a>CMFCButton::SetCheckedImage

Establece la imagen de un botón activado.

```cpp
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
[en] Controle el icono que contiene el mapa de bits y la máscara de la nueva imagen.

*bAutoDestroy*<br/>
[en] TRUE para especificar que los recursos de mapa de bits se destruyan automáticamente; de lo contrario, FALSE. El valor predeterminado es TRUE.

*hIconHot*<br/>
[en] Controle el icono que contiene la imagen para el estado seleccionado.

*hBitmap*<br/>
[en] Controle el mapa de bits que contiene la imagen para el estado no seleccionado.

*hBitmapHot*<br/>
[en] Controle el mapa de bits que contiene la imagen para el estado seleccionado.

*bMap3dColors*<br/>
[en] Especifica un color transparente para el fondo del botón; es decir, la cara del botón. TRUE para utilizar el valor de color RGB(192, 192, 192); FALSE para utilizar el `AFX_GLOBAL_DATA::clrBtnFace`valor de color definido por .

*uiBmpResId*<br/>
[en] Id. de recurso para la imagen no seleccionada.

*uiBmpHotResId*<br/>
[en] ID de recurso para la imagen seleccionada.

*hIconDisabled*<br/>
[en] Controle el icono de la imagen deshabilitada.

*hBitmapDisabled*<br/>
[en] Controle el mapa de bits que contiene la imagen deshabilitada.

*uiBmpDsblResID*<br/>
[en] ID de recurso del mapa de bits deshabilitado.

*bAlphaBlend*<br/>
[en] TRUE para utilizar solo imágenes de 32 bits que utilizan el canal alfa; FALSE, para no utilizar sólo imágenes de canal alfa. El valor predeterminado es FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonsetfacecolor"></a><a name="setfacecolor"></a>CMFCButton::SetFaceColor

Establece el color de fondo del texto del botón.

```cpp
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>Parámetros

*crFace*<br/>
[en] Un valor de color RGB.

*bRedraw*<br/>
[en] TRUE para volver a dibujar la pantalla inmediatamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método para definir un nuevo color de relleno para el fondo del botón (cara). Tenga en cuenta que el fondo no se rellena cuando el [CMFCButton::m_bTransparent](#m_btransparent) variable miembro es TRUE.

## <a name="cmfcbuttonsetimage"></a><a name="setimage"></a>CMFCButton::SetImage

Establece la imagen de un botón.

```cpp
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
[en] Controle el icono que contiene el mapa de bits y la máscara de la nueva imagen.

*bAutoDestroy*<br/>
[en] TRUE para especificar que los recursos de mapa de bits se destruyan automáticamente; de lo contrario, FALSE. El valor predeterminado es TRUE.

*hIconHot*<br/>
[en] Controle el icono que contiene la imagen para el estado seleccionado.

*hBitmap*<br/>
[en] Controle el mapa de bits que contiene la imagen para el estado no seleccionado.

*hBitmapHot*<br/>
[en] Controle el mapa de bits que contiene la imagen para el estado seleccionado.

*uiBmpResId*<br/>
[en] Id. de recurso para la imagen no seleccionada.

*uiBmpHotResId*<br/>
[en] ID de recurso para la imagen seleccionada.

*bMap3dColors*<br/>
[en] Especifica un color transparente para el fondo del botón; es decir, la cara del botón. TRUE para utilizar el valor de color RGB(192, 192, 192); FALSE para utilizar el `AFX_GLOBAL_DATA::clrBtnFace`valor de color definido por .

*hIconDisabled*<br/>
[en] Controle el icono de la imagen deshabilitada.

*hBitmapDisabled*<br/>
[en] Controle el mapa de bits que contiene la imagen deshabilitada.

*uiBmpDsblResID*<br/>
[en] ID de recurso del mapa de bits deshabilitado.

*bAlphaBlend*<br/>
[en] TRUE para utilizar solo imágenes de 32 bits que utilizan el canal alfa; FALSE, para no utilizar sólo imágenes de canal alfa. El valor predeterminado es FALSE.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `SetImage` cómo utilizar `CMFCButton` varias versiones del método en la clase. El ejemplo forma parte del [ejemplo Nuevos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

## <a name="cmfcbuttonsetmousecursor"></a><a name="setmousecursor"></a>CMFCButton::SetMouseCursor

Establece la imagen del cursor.

```cpp
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>Parámetros

*hcursor*<br/>
[en] El identificador de un cursor.

### <a name="remarks"></a>Observaciones

Utilice este método para asociar una imagen de cursor, como el cursor de la mano, con el botón. El cursor se carga desde los recursos de la aplicación.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `SetMouseCursor` muestra `CMFCButton` cómo utilizar el método en la clase. El ejemplo forma parte del código del [ejemplo Nuevos controles.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

## <a name="cmfcbuttonsetmousecursorhand"></a><a name="setmousecursorhand"></a>CMFCButton::SetMouseCursorHand

Establece el cursor en la imagen de una mano.

```cpp
void SetMouseCursorHand();
```

### <a name="remarks"></a>Observaciones

Utilice este método para asociar la imagen del cursor de una mano con el botón. El cursor se carga desde los recursos de la aplicación.

## <a name="cmfcbuttonsetstdimage"></a><a name="setstdimage"></a>CMFCButton::SetStdImage

Utiliza `CMenuImages` un objeto para establecer la imagen del botón.

```cpp
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Uno de los identificadores de imagen `CMenuImage::IMAGES_IDS` de botón que se define en la enumeración. Los valores de imagen especifican imágenes como flechas, pines y botones de opción.

*state*<br/>
[en] Uno de los identificadores de estado `CMenuImages::IMAGE_STATE` de imagen de botón que se define en la enumeración. Los estados de imagen especifican colores de botón como negro, gris, gris claro, blanco y gris oscuro. El valor predeterminado es `CMenuImages::ImageBlack`.

*idDisabled*<br/>
[en] Uno de los identificadores de imagen `CMenuImage::IMAGES_IDS` de botón que se define en la enumeración. La imagen indica que el botón está deshabilitado. El valor predeterminado es la `CMenuImages::IdArrowDown`primera imagen de botón ( ).

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonsettextcolor"></a><a name="settextcolor"></a>CMFCButton::SetTextColor

Establece el color del texto del botón para un botón que no está seleccionado.

```cpp
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>Parámetros

*clrText*<br/>
[en] Un valor de color RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonsettexthotcolor"></a><a name="settexthotcolor"></a>CMFCButton::SetTextHotColor

Establece el color del texto del botón para un botón seleccionado.

```cpp
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>Parámetros

*clrTextHot*<br/>
[en] Un valor de color RGB.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonsettooltip"></a><a name="settooltip"></a>CMFCButton::SetTooltip

Asocia una información sobre herramientas con un botón.

```cpp
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>Parámetros

*lpszToolTipText*<br/>
[en] Puntero al texto de la información sobre herramientas. Especifique NULL para deshabilitar la información sobre herramientas.

### <a name="remarks"></a>Observaciones

## <a name="cmfcbuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCButton::SizeToContent

Cambia el tamaño de un botón para que contenga el texto y la imagen del botón.

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>Parámetros

*bCalcOnly*<br/>
[en] TRUE para calcular, pero no cambiar, el nuevo tamaño del botón; FALSE para cambiar el tamaño del botón. El valor predeterminado es FALSE.

### <a name="return-value"></a>Valor devuelto

Objeto `CSize` que contiene el nuevo tamaño del botón.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método calcula un nuevo tamaño que incluye un margen horizontal de 10 píxeles y un margen vertical de 5 píxeles.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl (clase)](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton (Clase)](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton (clase)](../../mfc/reference/cmfcmenubutton-class.md)
