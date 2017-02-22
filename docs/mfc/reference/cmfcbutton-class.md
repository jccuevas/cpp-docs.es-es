---
title: "CMFCButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCButton class"
  - "CMFCButton constructor"
  - "CMFCButton::CreateObject method"
  - "CMFCButton::DrawItem method"
  - "CMFCButton::OnDrawParentBackground method"
  - "CMFCButton::PreTranslateMessage method"
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCButton` agrega funcionalidad a la clase de [CButton](../../mfc/reference/cbutton-class.md) como texto del botón que alinea, combinando el texto del botón y una imagen, seleccionando el cursor, y especificar una información sobre herramientas.  
  
## Sintaxis  
  
```  
class CMFCButton : public CButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCButton::CMFCButton`|Constructor predeterminado.|  
|`CMFCButton::~CMFCButton`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCButton::CleanUp](../Topic/CMFCButton::CleanUp.md)|Restablece variables internas y libera los recursos asignados como imágenes, mapas de bits, e iconos.|  
|`CMFCButton::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCButton::DrawItem`|Llamado por el marco cuando un aspecto visual de un botón propietario\- dibujado ha cambiado.  \(Reemplaza [CButton::DrawItem](../Topic/CButton::DrawItem.md).\)|  
|[CMFCButton::EnableFullTextTooltip](../Topic/CMFCButton::EnableFullTextTooltip.md)|Especifica si mostrar el texto completo de una información sobre herramientas en una ventana grande de información sobre herramientas o una versión truncada de texto en una pequeña ventana de información sobre herramientas.|  
|[CMFCButton::EnableMenuFont](../Topic/CMFCButton::EnableMenuFont.md)|Especifica si la fuente del texto del botón es igual que la fuente del menú de la aplicación.|  
|[CMFCButton::EnableWindowsTheming](../Topic/CMFCButton::EnableWindowsTheming.md)|Especifica si el estilo del borde del botón corresponde a Windows el tema actual.|  
|`CMFCButton::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCButton::GetToolTipCtrl](../Topic/CMFCButton::GetToolTipCtrl.md)|Devuelve una referencia al control subyacente de información sobre herramientas.|  
|[CMFCButton::IsAutoCheck](../Topic/CMFCButton::IsAutoCheck.md)|Indica si una casilla o un botón de radio es un botón automático.|  
|[CMFCButton::IsAutorepeatCommandMode](../Topic/CMFCButton::IsAutorepeatCommandMode.md)|Indica si un botón está establecido en el modo de repetición automática.|  
|[CMFCButton::IsCheckBox](../Topic/CMFCButton::IsCheckBox.md)|Indica si un botón es un botón de la casilla.|  
|[CMFCButton::IsChecked](../Topic/CMFCButton::IsChecked.md)|Indica si el botón actual está activado.|  
|[CMFCButton::IsHighlighted](../Topic/CMFCButton::IsHighlighted.md)|Indica si un botón es resaltado.|  
|[CMFCButton::IsPressed](../Topic/CMFCButton::IsPressed.md)|Indica si un botón se inserta y resaltado.|  
|[CMFCButton::IsPushed](../Topic/CMFCButton::IsPushed.md)|Indica si un botón se inserta.|  
|[CMFCButton::IsRadioButton](../Topic/CMFCButton::IsRadioButton.md)|indica si un botón es un botón de opción.|  
|[CMFCButton::IsWindowsThemingEnabled](../Topic/CMFCButton::IsWindowsThemingEnabled.md)|Indica si el estilo del borde del botón corresponde a Windows el tema actual.|  
|`CMFCButton::OnDrawParentBackground`|Dibuja el fondo del elemento primario de un botón en el área especificada.  \(Reemplaza [AFX\_GLOBAL\_DATA::DrawParentBackground](../Topic/AFX_GLOBAL_DATA::DrawParentBackground.md).\)|  
|`CMFCButton::PreTranslateMessage`|Traduce mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).\)|  
|[CMFCButton::SetAutorepeatMode](../Topic/CMFCButton::SetAutorepeatMode.md)|Establece un botón al modo de repetición automática.|  
|[CMFCButton::SetCheckedImage](../Topic/CMFCButton::SetCheckedImage.md)|Establece la imagen de un botón comprobado.|  
|[CMFCButton::SetFaceColor](../Topic/CMFCButton::SetFaceColor.md)|Establece el color de fondo del texto del botón.|  
|[CMFCButton::SetImage](../Topic/CMFCButton::SetImage.md)|Establece la imagen de un botón.|  
|[CMFCButton::SetMouseCursor](../Topic/CMFCButton::SetMouseCursor.md)|Establece la imagen del cursor.|  
|[CMFCButton::SetMouseCursorHand](../Topic/CMFCButton::SetMouseCursorHand.md)|Establece el cursor a la imagen de una mano.|  
|[CMFCButton::SetStdImage](../Topic/CMFCButton::SetStdImage.md)|Usa un objeto de `CMenuImages` para establecer la imagen del botón.|  
|[CMFCButton::SetTextColor](../Topic/CMFCButton::SetTextColor.md)|Establece el color del texto del botón para un botón que no se ha seleccionado.|  
|[CMFCButton::SetTextHotColor](../Topic/CMFCButton::SetTextHotColor.md)|Establece el color del texto del botón para un botón seleccionado que.|  
|[CMFCButton::SetTooltip](../Topic/CMFCButton::SetTooltip.md)|asocia una información sobre herramientas a un botón.|  
|[CMFCButton::SizeToContent](../Topic/CMFCButton::SizeToContent.md)|Cambia el tamaño de un botón para contener el texto del botón e imagen.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCButton::OnDraw](../Topic/CMFCButton::OnDraw.md)|Llamado por el marco para dibujar un botón.|  
|[CMFCButton::OnDrawBorder](../Topic/CMFCButton::OnDrawBorder.md)|Llamado por el marco para dibujar el borde de un botón.|  
|[CMFCButton::OnDrawFocusRect](../Topic/CMFCButton::OnDrawFocusRect.md)|Llamado por el marco para dibujar el rectángulo de foco para un botón.|  
|[CMFCButton::OnDrawText](../Topic/CMFCButton::OnDrawText.md)|Llamado por el marco para dibujar el texto del botón.|  
|[CMFCButton::OnFillBackground](../Topic/CMFCButton::OnFillBackground.md)|Llamado por el marco para dibujar el fondo del texto del botón.|  
|[CMFCButton::SelectFont](../Topic/CMFCButton::SelectFont.md)|Recuperar la fuente que está asociado con el contexto especificado del dispositivo.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCButton::m\_bDrawFocus](../Topic/CMFCButton::m_bDrawFocus.md)|Indica si dibujar un rectángulo de foco alrededor de un botón.|  
|[CMFCButton::m\_bHighlightChecked](../Topic/CMFCButton::m_bHighlightChecked.md)|Indica si resaltar un botón de BS\_CHECKBOX\-style cuando el puntero del mouse del cursor sobre ella.|  
|[CMFCButton::m\_bRightImage](../Topic/CMFCButton::m_bRightImage.md)|Indica si mostrar una imagen a la derecha del botón.|  
|[CMFCButton::m\_bTransparent](../Topic/CMFCButton::m_bTransparent.md)|indica si el botón es transparente.|  
|[CMFCButton::m\_nAlignStyle](../Topic/CMFCButton::m_nAlignStyle.md)|Especifica la alineación del texto del botón.|  
|[CMFCButton::m\_nFlatStyle](../Topic/CMFCButton::m_nFlatStyle.md)|Especifica el estilo de botón, como sin extremos, plano, semi\-plano, o 3D.|  
  
## Comentarios  
 Derivan a otros tipos de botones de la clase de `CMFCButton` , como la clase de [CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md) , que admite los hipervínculos, y la clase de `CMFCColorButton` , que admite un cuadro de diálogo Selector de colores.  
  
 El estilo de un objeto de `CMFCButton` puede ser *3D*, *plano*, semi\- *plano* o *ningún borde*.  El texto del botón se puede clasificar en el izquierdo, superior, o centro de un botón.  En tiempo de ejecución, puede controlar si el botón texto, una imagen, o texto y una imagen.  También puede especificar una imagen particular del cursor se mostrará cuando el puntero del mouse del cursor sobre un botón.  
  
 Crear un control de botón directamente en el código, o mediante la herramienta de **Asistente para clases MFC** y una plantilla de cuadro de diálogo.  Si crea un control de botón directamente, agregue una variable de `CMFCButton` a la aplicación, y llame al constructor y los métodos de `Create` de `CMFCButton` se oponen.  Si utiliza **Asistente para clases MFC**, agregue una variable de `CButton` a la aplicación, y después cambie el tipo de la variable de `CButton` a `CMFCButton`.  
  
 Para controlar los mensajes de notificación en una aplicación de cuadro de diálogo, agregue una entrada del mapa de mensajes y un controlador de eventos para cada notificación.  Las notificaciones enviadas por un objeto de `CMFCButton` son iguales que las enviadas por un objeto de `CButton` .  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar las propiedades del botón mediante varios métodos en la clase de `CMFCButton` .  El ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/CPP/cmfcbutton-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/CPP/cmfcbutton-class_2.cpp)]  
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/CPP/cmfcbutton-class_3.cpp)]  
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/CPP/cmfcbutton-class_4.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCButton](../../mfc/reference/cmfcbutton-class.md)  
  
## Requisitos  
 **encabezado:** afxbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCLinkCtrl Class](../../mfc/reference/cmfclinkctrl-class.md)   
 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md)   
 [CMFCMenuButton \(clase\)](../../mfc/reference/cmfcmenubutton-class.md)