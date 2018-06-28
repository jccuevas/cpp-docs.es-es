---
title: Clase CMFCButton | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afd30c9f27d83e7d4cfaf9b993b258b069f73dc4
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039237"
---
# <a name="cmfcbutton-class"></a>Clase CMFCButton
El `CMFCButton` clase agrega funcionalidad a la [CButton](../../mfc/reference/cbutton-class.md) clase como alinear el texto del botón, combinar el texto del botón y una imagen, seleccionar un cursor y especificar una información sobre herramientas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCButton : public CButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCButton::CMFCButton`|Constructor predeterminado.|  
|`CMFCButton::~CMFCButton`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCButton::CleanUp](#cleanup)|Restablece las variables internas y libera los recursos asignados, como imágenes, mapas de bits e iconos.|  
|`CMFCButton::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCButton::DrawItem`|Lo llama el marco de trabajo cuando ha cambiado la apariencia de un botón dibujado por el propietario. (Invalida [CButton::DrawItem](../../mfc/reference/cbutton-class.md#drawitem).)|  
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|Especifica si se muestra el texto completo de una información sobre herramientas en una ventana grande de información sobre herramientas o una versión truncada del texto en una ventana pequeña de información sobre herramientas.|  
|[CMFCButton::EnableMenuFont](#enablemenufont)|Especifica si la fuente del texto de botón es el mismo que la fuente del menú de aplicación.|  
|[CMFCButton::EnableWindowsTheming](#enablewindowstheming)|Especifica si el estilo del borde de botón se corresponde con el tema de Windows actual.|  
|`CMFCButton::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCButton::GetToolTipCtrl](#gettooltipctrl)|Devuelve una referencia al control de información sobre herramientas subyacente.|  
|[CMFCButton::IsAutoCheck](#isautocheck)|Indica si la casilla de verificación o botón de opción es un botón automático.|  
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|Indica si un botón se establece en modo de repetición automática.|  
|[CMFCButton::IsCheckBox](#ischeckbox)|Indica si un botón es un botón de casilla de verificación.|  
|[CMFCButton::IsChecked](#ischecked)|Indica si está activado el botón actual.|  
|[CMFCButton::IsHighlighted](#ishighlighted)|Indica si un botón se resalta.|  
|[CMFCButton::IsPressed](#ispressed)|Indica si se inserta un botón y se resalta.|  
|[CMFCButton::IsPushed](#ispushed)|Indica si se inserta un botón.|  
|[CMFCButton::IsRadioButton](#isradiobutton)|Indica si un botón es un botón de radio.|  
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|Indica si el estilo del borde de botón se corresponde con el tema de Windows actual.|  
|`CMFCButton::OnDrawParentBackground`|Dibuja el fondo del elemento primario de un botón en el área especificada. (Invalida [AFX_GLOBAL_DATA::DrawParentBackground](../../mfc/reference/afx-global-data-structure.md)|  
|`CMFCButton::PreTranslateMessage`|Convierte los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|  
|[CMFCButton::SetAutorepeatMode](#setautorepeatmode)|Establece un botón en modo de repetición automática.|  
|[CMFCButton::SetCheckedImage](#setcheckedimage)|Establece la imagen de un botón activado.|  
|[CMFCButton::SetFaceColor](#setfacecolor)|Establece el color de fondo para el texto del botón.|  
|[CMFCButton::SetImage](#setimage)|Establece la imagen de un botón.|  
|[CMFCButton::SetMouseCursor](#setmousecursor)|Establece la imagen del cursor.|  
|[CMFCButton::SetMouseCursorHand](#setmousecursorhand)|Establece el cursor a la imagen de una mano.|  
|[CMFCButton::SetStdImage](#setstdimage)|Usa un `CMenuImages` objeto que se va a establecer la imagen del botón.|  
|[CMFCButton::SetTextColor](#settextcolor)|Establece el color del texto del botón para un botón que no está seleccionado.|  
|[CMFCButton::SetTextHotColor](#settexthotcolor)|Establece el color del texto del botón para un botón que está seleccionado.|  
|[CMFCButton::SetTooltip](#settooltip)|Asocia una información sobre herramientas con un botón.|  
|[CMFCButton::SizeToContent](#sizetocontent)|Cambia el tamaño de un botón para que contenga el texto del botón y la imagen.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCButton::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar un botón.|  
|[CMFCButton::OnDrawBorder](#ondrawborder)|Lo llama el marco de trabajo para dibujar el borde de un botón.|  
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|Lo llama el marco de trabajo para dibujar el rectángulo de foco para un botón.|  
|[CMFCButton::OnDrawText](#ondrawtext)|Lo llama el marco de trabajo para dibujar el texto del botón.|  
|[CMFCButton::OnFillBackground](#onfillbackground)|Lo llama el marco de trabajo para dibujar el fondo del texto del botón.|  
|[CMFCButton::SelectFont](#selectfont)|Recupera la fuente que está asociada con el contexto de dispositivo especificado.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCButton::m_bDrawFocus](#m_bdrawfocus)|Indica si se debe dibujar un rectángulo de foco alrededor de un botón.|  
|[CMFCButton::m_bHighlightChecked](#m_bhighlightchecked)|Indica si se deben resaltar un botón de estilo BS_CHECKBOX cuando el cursor se desplaza sobre él.|  
|[CMFCButton::m_bRightImage](#m_brightimage)|Indica si se debe mostrar una imagen en el lado derecho del botón.|  
|[CMFCButton::m_bTransparent](#m_btransparent)|Indica si el botón es transparente.|  
|[CMFCButton::m_nAlignStyle](#m_nalignstyle)|Especifica la alineación del texto del botón.|  
|[CMFCButton::m_nFlatStyle](#m_nflatstyle)|Especifica el estilo del botón, por ejemplo, plana y sin bordes, sin formato, y 3D.|  
  
## <a name="remarks"></a>Comentarios  
 Otros tipos de botones se derivan de la `CMFCButton` class, como el [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) (clase), que es compatible con hipervínculos, y `CMFCColorButton` (clase), que es compatible con un cuadro de diálogo de selector de color.  
  
 El estilo de un `CMFCButton` objeto puede ser *3D*, *plana*, *semi-plana y* o *ningún borde*. Texto del botón se puede alinear a la izquierda, la parte superior o el centro de un botón. En tiempo de ejecución, puede controlar si el botón muestra texto, una imagen o texto y una imagen. También puede especificar que se muestra una imagen de cursor determinado cuando el cursor se sitúa sobre un botón.  
  
 Crear un control de botón, ya sea directamente en el código o mediante el **Asistente para clases MFC** herramienta y una plantilla de cuadro de diálogo. Si crea un control de botón directamente, agregar un `CMFCButton` variable a su aplicación y, después, llame al constructor y `Create` métodos de la `CMFCButton` objeto. Si usas el **Asistente para clases MFC**, agregue un `CButton` variable a la aplicación y, a continuación, cambie el tipo de la variable de `CButton` a `CMFCButton`.  
  
 Para controlar los mensajes de notificación en una aplicación de cuadro de diálogo, agregue una entrada de mapa de mensajes y un controlador de eventos de cada notificación. Las notificaciones enviadas por un `CMFCButton` objeto son los mismos que los enviados por un `CButton` objeto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar las propiedades del botón con varios métodos en la `CMFCButton` clase. El ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
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
  
##  <a name="cleanup"></a>  CMFCButton::CleanUp  
 Restablece las variables internas y libera los recursos asignados, como imágenes, mapas de bits e iconos.  
  
```  
virtual void CleanUp();
```  
  
##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip  
 Especifica si se muestra el texto completo de una información sobre herramientas en una ventana grande de información sobre herramientas o una versión truncada del texto en una ventana pequeña de información sobre herramientas.  
  
```  
void EnableFullTextTooltip(BOOL bOn=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *Ben*  
 `TRUE` para mostrar todo el texto; `FALSE` a texto de presentación truncado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont  
 Especifica si la fuente del texto de botón es el mismo que la fuente del menú de aplicación.  
  
```  
void EnableMenuFont(
    BOOL bOn=TRUE,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *Ben*  
 `TRUE` Para usar la fuente del menú de aplicación como la fuente del texto de botón; `FALSE` para usar la fuente del sistema. De manera predeterminada, es `TRUE`.  
  
 [in] *bRedraw*  
 `TRUE` Para volver a dibujar inmediatamente la pantalla; en caso contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Si no usa este método para especificar la fuente del texto de botón, puede especificar la fuente con la [CWnd::SetFont](../../mfc/reference/cwnd-class.md#setfont) método. Si no especifica una fuente, el marco de trabajo establece una fuente predeterminada.  
  
##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming  
 Especifica si el estilo del borde de botón se corresponde con el tema de Windows actual.  
  
```  
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHabilitar el*  
 `TRUE` Para utilizar el tema de Windows actual para dibujar los bordes del botón; `FALSE` para no utilizar el tema de Windows. De manera predeterminada, es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método afecta a todos los botones de la aplicación que se derivan de la `CMFCButton` clase.  
  
##  <a name="gettooltipctrl"></a>  CMFCButton::GetToolTipCtrl  
 Devuelve una referencia al control de información sobre herramientas subyacente.  
  
```  
CToolTipCtrl& GetToolTipCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al control de información sobre herramientas subyacente.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck  
 Indica si la casilla de verificación o botón de opción es un botón automático.  
  
```  
BOOL IsAutoCheck() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si el botón tiene el estilo BS_AUTOCHECKBOX o BS_AUTORADIOBUTTON; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode  
 Indica si un botón se establece en modo de repetición automática.  
  
```  
BOOL IsAutorepeatCommandMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el botón se establece en modo de repetición automática; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCButton::SetAutorepeatMode](#setautorepeatmode) método para establecer un botón en modo de repetición automática.  
  
##  <a name="ischeckbox"></a>  CMFCButton::IsCheckBox  
 Indica si un botón es un botón de casilla de verificación.  
  
```  
BOOL IsCheckBox() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el botón tiene el estilo BS_CHECKBOX o BS_AUTOCHECKBOX; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ischecked"></a>  CMFCButton::IsChecked  
 Indica si está activado el botón actual.  
  
```  
BOOL IsChecked() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si se activa el botón actual; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo muestran maneras diferentes para indicar que se comprueban los diferentes tipos de botones. Por ejemplo, un botón de radio se comprueba cuando contiene un punto; una casilla está activada cuando contiene un **X**.  
  
##  <a name="ishighlighted"></a>  CMFCButton::IsHighlighted  
 Indica si un botón se resalta.  
  
```  
BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el botón está resaltado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Un botón se resalta cuando se desplaza el mouse sobre el botón.  
  
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
 TRUE si el botón está presionado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isradiobutton"></a>  CMFCButton::IsRadioButton  
 Indica si un botón es un botón de radio.  
  
```  
BOOL IsRadioButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el estilo de botón es BS_RADIOBUTTON o BS_AUTORADIOBUTTON; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled  
 Indica si el estilo del borde de botón se corresponde con el tema de Windows actual.  
  
```  
static BOOL IsWindowsThemingEnabled();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si el estilo del borde de botón que se corresponde con el tema actual de Windows; en caso contrario, `FALSE`.  
  
##  <a name="m_bdrawfocus"></a>  CMFCButton::m_bDrawFocus  
 Indica si se debe dibujar un rectángulo de foco alrededor de un botón.  
  
```  
BOOL m_bDrawFocus;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer el `m_bDrawFocus` miembro `TRUE` para especificar que el marco se dibuja un rectángulo de foco alrededor del texto del botón y si el botón recibe el foco de la imagen.  
  
 El `CMFCButton` constructor inicializa este miembro por `TRUE`.  
  
##  <a name="m_bhighlightchecked"></a>  CMFCButton::m_bHighlightChecked  
 Indica si se deben resaltar un botón de estilo BS_CHECKBOX cuando el cursor se desplaza sobre él.  
  
```  
BOOL m_bHighlightChecked;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer el `m_bHighlightChecked` miembro `TRUE` para especificar que el marco de trabajo resaltará un botón de estilo BS_CHECKBOX cuando se desplaza el mouse sobre él.  
  
##  <a name="m_brightimage"></a>  CMFCButton::m_bRightImage  
 Indica si se debe mostrar una imagen en el lado derecho del botón.  
  
```  
BOOL m_bRightImage;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer el `m_bRightImage` miembro `TRUE` para especificar que el marco de trabajo mostrará la imagen del botón a la derecha de la etiqueta de texto del botón.  
  
##  <a name="m_btransparent"></a>  CMFCButton::m_bTransparent  
 Indica si el botón es transparente.  
  
```  
BOOL m_bTransparent;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer el `m_bTransparent` miembro `TRUE` para especificar que el marco de trabajo realizará el botón transparente. El `CMFCButton` constructor inicializa este miembro por `FALSE`.  
  
##  <a name="m_nalignstyle"></a>  CMFCButton::m_nAlignStyle  
 Especifica la alineación del texto del botón.  
  
```  
AlignStyle m_nAlignStyle;  
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice uno de los siguientes `CMFCButton::AlignStyle` valores de enumeración para especificar la alineación del texto del botón:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|ALIGN_CENTER|(Valor predeterminado) Alinea el texto del botón en el centro del botón.|  
|ALIGN_LEFT|Alinea el texto del botón a la izquierda del botón.|  
|ALIGN_RIGHT|Alinea el texto del botón a la derecha del botón.|  
  
 El `CMFCButton` constructor inicializa este miembro por ALIGN_CENTER.  
  
##  <a name="m_nflatstyle"></a>  CMFCButton::m_nFlatStyle  
 Especifica el estilo del botón, por ejemplo, plana y sin bordes, sin formato, y 3D.  
  
```  
FlatStyle  m_nFlatStyle;  
```  
  
### <a name="remarks"></a>Comentarios  
 La siguiente tabla se recogen los `CMFCButton::m_nFlatStyle` valores de enumeración que especifican la apariencia de un botón.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|BUTTONSTYLE_3D|(Valor predeterminado) Aparece el botón tener partes alta y tridimensionales. Cuando se hace clic en el botón, aparece el botón presionado en una sangría de profundidad.|  
|BUTTONSTYLE_FLAT|Cuando no sitúe el mouse sobre el botón, el botón aparece como bidimensional y no tiene lados generados. Cuando se detiene el mouse sobre el botón, aparece el botón tener lados bajos, tridimensionales. Cuando se hace clic en el botón, aparece el botón presionado en una sangría superficial.|  
|BUTTONSTYLE_SEMIFLAT|Aparece el botón tener lados bajos, tridimensionales. Cuando se hace clic en el botón, aparece el botón presionado en una sangría de profundidad.|  
|BUTTONSTYLE_NOBORDERS|El botón no se generado lados y siempre aparece bidimensional. El botón no aparece presionado en aplicar una sangría cuando se hace clic en.|  
  
 El `CMFCButton` constructor inicializa este miembro por `BUTTONSTYLE_3D`.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer los valores de la `m_nFlatStyle` variable miembro en la `CMFCButton` clase. Este ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]  
  
##  <a name="ondraw"></a>  CMFCButton::OnDraw  
 Lo llama el marco de trabajo para dibujar un botón.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rect*  
 Una referencia a un rectángulo que delimita el botón.  
  
 [in] *uiState*  
 El estado actual de los botones. Para obtener más información, consulte el `itemState` miembro de la [DRAWITEMSTRUCT (estructura)](../../mfc/reference/drawitemstruct-structure.md) tema.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para utilizar su propio código para dibujar un botón.  
  
##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder  
 Lo llama el marco de trabajo para dibujar el borde de un botón.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect& rectClient,  
    UINT uiState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rectClient*  
 Una referencia a un rectángulo que delimita el botón.  
  
 [in] *uiState*  
 El estado actual de los botones. Para obtener más información, consulte el `itemState` miembro de la [DRAWITEMSTRUCT (estructura)](../../mfc/reference/drawitemstruct-structure.md) tema.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para utilizar su propio código para dibujar el borde.  
  
##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect  
 Lo llama el marco de trabajo para dibujar el rectángulo de foco para un botón.  
  
```  
virtual void OnDrawFocusRect(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rectClient*  
 Una referencia a un rectángulo que delimita el botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para utilizar su propio código para dibujar el rectángulo de foco.  
  
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
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rect*  
 Una referencia a un rectángulo que delimita el botón.  
  
 [in] *strText*  
 Texto que se va a trazar.  
  
 [in] *uiDTFlags*  
 Marcas que especifican cómo dar formato al texto. Para obtener más información, consulte el *nFormat* parámetro de la [CDC:: DrawText](../../mfc/reference/cdc-class.md#drawtext) método.  
  
 [in] *uiState*  
 (Reservado).  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para utilizar su propio código para dibujar el texto del botón.  
  
##  <a name="onfillbackground"></a>  CMFCButton::OnFillBackground  
 Lo llama el marco de trabajo para dibujar el fondo del texto del botón.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    const CRect& rectClient);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
 [in] *rectClient*  
 Una referencia a un rectángulo que delimita el botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para utilizar su propio código para dibujar el fondo de un botón.  
  
##  <a name="selectfont"></a>  CMFCButton::SelectFont  
 Recupera la fuente que está asociada con el contexto de dispositivo especificado.  
  
```  
virtual CFont* SelectFont(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 Puntero a un contexto de dispositivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Invalide este método para utilizar su propio código para recuperar la fuente.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setautorepeatmode"></a>  CMFCButton::SetAutorepeatMode  
 Establece un botón en modo de repetición automática.  
  
```  
void SetAutorepeatMode(int nTimeDelay=500);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nTimeDelay*  
 Un número no negativo que especifica el intervalo entre los mensajes que se envían a la ventana primaria. El intervalo se mide en milisegundos y su valor predeterminado es 500 milisegundos. Especifique cero para deshabilitar el modo de mensaje de repetición automática.  
  
### <a name="remarks"></a>Comentarios  
 Este método hace que el botón Enviar constantemente WM_COMMAND (mensajes) a la ventana primaria hasta que se libere el botón, o la *nTimeDelay* parámetro se establece en cero.  
  
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
 [in] *hIcon*  
 Identificador del icono que contiene el mapa de bits y una máscara para la nueva imagen.  
  
 [in] *bAutoDestroy*  
 `TRUE` para especificar que los recursos de mapa de bits se destruyen automáticamente; en caso contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
 [in] *hIconHot*  
 Identificador del icono que contiene la imagen del estado seleccionado.  
  
 [in] *hBitmap*  
 Identificador de mapa de bits que contiene la imagen para el estado no se han seleccionado.  
  
 [in] *hBitmapHot*  
 Identificador de mapa de bits que contiene la imagen del estado seleccionado.  
  
 [in] *bMap3dColors*  
 Especifica un color transparente para el fondo del botón; es decir, la imagen del botón. `TRUE` Para usar el valor de color RGB (192, 192, 192); `FALSE` para usar el valor de color definido por `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] *uiBmpResId*  
 Id. de recurso de la imagen no se han seleccionado.  
  
 [in] *uiBmpHotResId*  
 Id. de recurso para la imagen seleccionada.  
  
 [in] *hIconDisabled*  
 Identificador para el icono de la imagen deshabilitada.  
  
 [in] *hBitmapDisabled*  
 Identificador de mapa de bits que contiene la imagen deshabilitada.  
  
 [in] *uiBmpDsblResID*  
 Id. de recurso del mapa de bits deshabilitada.  
  
 [in] *bAlphaBlend*  
 `TRUE` usar sólo las imágenes de 32 bits que utilizan el canal alfa; `FALSE`, para no usar sólo las imágenes de canal alfa. De manera predeterminada, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor  
 Establece el color de fondo para el texto del botón.  
  
```  
void SetFaceColor(
    COLORREF crFace,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *crFace*  
 Un valor de color RGB.  
  
 [in] *bRedraw*  
 `TRUE` Para volver a dibujar la pantalla inmediatamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para definir un nuevo color de relleno para el fondo del botón (cara). Observe que el fondo no rellena cuando el [CMFCButton::m_bTransparent](#m_btransparent) es una variable miembro `TRUE`.  
  
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
 [in] *hIcon*  
 Identificador del icono que contiene el mapa de bits y una máscara para la nueva imagen.  
  
 [in] *bAutoDestroy*  
 `TRUE` para especificar que los recursos de mapa de bits se destruyen automáticamente; en caso contrario, `FALSE`. De manera predeterminada, es `TRUE`.  
  
 [in] *hIconHot*  
 Identificador del icono que contiene la imagen del estado seleccionado.  
  
 [in] *hBitmap*  
 Identificador de mapa de bits que contiene la imagen para el estado no se han seleccionado.  
  
 [in] *hBitmapHot*  
 Identificador de mapa de bits que contiene la imagen del estado seleccionado.  
  
 [in] *uiBmpResId*  
 Id. de recurso de la imagen no se han seleccionado.  
  
 [in] *uiBmpHotResId*  
 Id. de recurso para la imagen seleccionada.  
  
 [in] *bMap3dColors*  
 Especifica un color transparente para el fondo del botón; es decir, la imagen del botón. `TRUE` Para usar el valor de color RGB (192, 192, 192); `FALSE` para usar el valor de color definido por `AFX_GLOBAL_DATA::clrBtnFace`.  
  
 [in] *hIconDisabled*  
 Identificador para el icono de la imagen deshabilitada.  
  
 [in] *hBitmapDisabled*  
 Identificador de mapa de bits que contiene la imagen deshabilitada.  
  
 [in] *uiBmpDsblResID*  
 Id. de recurso del mapa de bits deshabilitada.  
  
 [in] *bAlphaBlend*  
 `TRUE` usar sólo las imágenes de 32 bits que utilizan el canal alfa; `FALSE`, para no usar sólo las imágenes de canal alfa. De manera predeterminada, es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar las diversas versiones de la `SetImage` método en la `CMFCButton` clase. El ejemplo forma parte de la [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]  
  
##  <a name="setmousecursor"></a>  CMFCButton::SetMouseCursor  
 Establece la imagen del cursor.  
  
```  
void SetMouseCursor(HCURSOR hcursor);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *hcursor*  
 El identificador de un cursor.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para asociar una imagen del cursor, por ejemplo, el cursor de mano, con el botón. El cursor se carga desde los recursos de aplicación.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `SetMouseCursor` método en la `CMFCButton` clase. El ejemplo forma parte del código en el [ejemplo nuevos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]  
  
##  <a name="setmousecursorhand"></a>  CMFCButton::SetMouseCursorHand  
 Establece el cursor a la imagen de una mano.  
  
```  
void SetMouseCursorHand();
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para asociar la imagen de cursor de mano con el botón. El cursor se carga desde los recursos de aplicación.  
  
##  <a name="setstdimage"></a>  CMFCButton::SetStdImage  
 Usa un `CMenuImages` objeto que se va a establecer la imagen del botón.  
  
```  
void SetStdImage(
    CMenuImages::IMAGES_IDS id,  
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,  
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *Id.*  
 Uno de los identificadores de la imagen de botón que se define en el `CMenuImage::IMAGES_IDS` enumeración. Los valores de la imagen especifican imágenes como flechas, PIN y botones de radio.  
  
 [in] *estado*  
 Uno de los identificadores de estado de imagen de botón que se define en el `CMenuImages::IMAGE_STATE` enumeración. Los Estados de imagen especificarán colores de botón como gris de negro, gris claro, blanco y oscuro gris. El valor predeterminado es `CMenuImages::ImageBlack`.  
  
 [in] *idDisabled*  
 Uno de los identificadores de la imagen de botón que se define en el `CMenuImage::IMAGES_IDS` enumeración. La imagen indica que el botón está deshabilitado. El valor predeterminado es la primera imagen del botón ( `CMenuImages::IdArrowDown`).  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settextcolor"></a>  CMFCButton::SetTextColor  
 Establece el color del texto del botón para un botón que no está seleccionado.  
  
```  
void SetTextColor(COLORREF clrText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *clrText*  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor  
 Establece el color del texto del botón para un botón que está seleccionado.  
  
```  
void SetTextHotColor(COLORREF clrTextHot);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *clrTextHot*  
 Un valor de color RGB.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="settooltip"></a>  CMFCButton::SetTooltip  
 Asocia una información sobre herramientas con un botón.  
  
```  
void SetTooltip(LPCTSTR lpszToolTipText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszToolTipText*  
 Puntero al texto de la información sobre herramientas. Especifique NULL para deshabilitar la información sobre herramientas.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="sizetocontent"></a>  CMFCButton::SizeToContent  
 Cambia el tamaño de un botón para que contenga el texto del botón y la imagen.  
  
```  
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bCalcOnly*  
 `TRUE` para calcular, pero no cambiar, el nuevo tamaño del botón; `FALSE` para cambiar el tamaño del botón. De manera predeterminada, es `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CSize` objeto que contiene el nuevo tamaño del botón.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método calcula un nuevo tamaño que incluya un margen horizontal de 10 píxeles y un margen vertical de 5 píxeles.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)   
 [Clase CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton (clase)](../../mfc/reference/cmfcmenubutton-class.md)
