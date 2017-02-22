---
title: "CMFCRibbonGallery Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonGallery"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonGallery class"
ms.assetid: 9734c9c9-981c-4b3f-8c59-264fd41811b4
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCRibbonGallery Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa galerías de la cinta de opciones de estilo de Office 2007.  
  
## Sintaxis  
  
```  
class CMFCRibbonGallery : public CMFCRibbonButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGallery::CMFCRibbonGallery](../Topic/CMFCRibbonGallery::CMFCRibbonGallery.md)|Las construcciones e inicializan un objeto de `CMFCRibbonGallery` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGallery::AddGroup](../Topic/CMFCRibbonGallery::AddGroup.md)|Agrega un nuevo grupo a la galería.|  
|[CMFCRibbonGallery::AddSubItem](../Topic/CMFCRibbonGallery::AddSubItem.md)|Agrega un nuevo elemento de menú al menú desplegable.|  
|[CMFCRibbonGallery::Clear](../Topic/CMFCRibbonGallery::Clear.md)|borra el contenido de la galería.|  
|[CMFCRibbonGallery::EnableMenuResize](../Topic/CMFCRibbonGallery::EnableMenuResize.md)|Habilita o deshabilita el tamaño del panel del menú.|  
|[CMFCRibbonGallery::EnableMenuSideBar](../Topic/CMFCRibbonGallery::EnableMenuSideBar.md)|Habilita o deshabilita la barra lateral a la izquierda del elemento emergente.|  
|[CMFCRibbonGallery::GetCompactSize](../Topic/CMFCRibbonGallery::GetCompactSize.md)|\(Reemplaza [CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md).\)|  
|[CMFCRibbonGallery::GetDroppedDown](../Topic/CMFCRibbonGallery::GetDroppedDown.md)|\(Reemplaza [CMFCRibbonBaseElement::GetDroppedDown](../Topic/CMFCRibbonBaseElement::GetDroppedDown.md).\)|  
|[CMFCRibbonGallery::GetGroupName](../Topic/CMFCRibbonGallery::GetGroupName.md)|Devuelve el nombre del grupo que se encuentra en el índice especificado.|  
|[CMFCRibbonGallery::GetGroupOffset](../Topic/CMFCRibbonGallery::GetGroupOffset.md)||  
|[CMFCRibbonGallery::GetIconsInRow](../Topic/CMFCRibbonGallery::GetIconsInRow.md)|Devuelve el número de elementos en una fila de la galería de la cinta de opciones.|  
|[CMFCRibbonGallery::GetItemToolTip](../Topic/CMFCRibbonGallery::GetItemToolTip.md)|Devuelve el texto de información sobre herramientas que está asociado a un elemento en la galería.|  
|[CMFCRibbonGallery::GetLastSelectedItem](../Topic/CMFCRibbonGallery::GetLastSelectedItem.md)|Devuelve el índice del último elemento de la galería que el usuario seleccionado.|  
|[CMFCRibbonGallery::GetPaletteID](../Topic/CMFCRibbonGallery::GetPaletteID.md)|Devuelve el identificador de comando de la galería actual.|  
|[CMFCRibbonGallery::GetRegularSize](../Topic/CMFCRibbonGallery::GetRegularSize.md)|\(Reemplaza [CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md).\)|  
|[CMFCRibbonGallery::GetSelectedItem](../Topic/CMFCRibbonGallery::GetSelectedItem.md)||  
|[CMFCRibbonGallery::HasMenu](../Topic/CMFCRibbonGallery::HasMenu.md)|\(Reemplaza [CMFCRibbonButton::HasMenu](../Topic/CMFCRibbonButton::HasMenu.md).\)|  
|[CMFCRibbonGallery::IsButtonMode](../Topic/CMFCRibbonGallery::IsButtonMode.md)|especifica si la galería está contenida en un botón de la galería.|  
|[CMFCRibbonGallery::IsMenuResizeEnabled](../Topic/CMFCRibbonGallery::IsMenuResizeEnabled.md)|Especifica si el menú de cambio de tamaño está habilitado o deshabilitado.|  
|[CMFCRibbonGallery::IsMenuResizeVertical](../Topic/CMFCRibbonGallery::IsMenuResizeVertical.md)||  
|[CMFCRibbonGallery::IsMenuSideBar](../Topic/CMFCRibbonGallery::IsMenuSideBar.md)|especifica si la barra lateral está habilitada o deshabilitada.|  
|[CMFCRibbonGallery::OnAfterChangeRect](../Topic/CMFCRibbonGallery::OnAfterChangeRect.md)|\(Reemplaza `CMFCRibbonButton::OnAfterChangeRect`.\)|  
|[CMFCRibbonGallery::OnDraw](../Topic/CMFCRibbonGallery::OnDraw.md)|\(Reemplaza [CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md).\)|  
|[CMFCRibbonGallery::OnEnable](../Topic/CMFCRibbonGallery::OnEnable.md)|\(Reemplaza `CMFCRibbonBaseElement::OnEnable`.\)|  
|[CMFCRibbonGallery::OnRTLChanged](../Topic/CMFCRibbonGallery::OnRTLChanged.md)|\(Reemplaza [CMFCRibbonBaseElement::OnRTLChanged](../Topic/CMFCRibbonBaseElement::OnRTLChanged.md).\)|  
|[CMFCRibbonGallery::RedrawIcons](../Topic/CMFCRibbonGallery::RedrawIcons.md)|Redibuja la galería.|  
|[CMFCRibbonGallery::RemoveItemToolTips](../Topic/CMFCRibbonGallery::RemoveItemToolTips.md)|Quita la información sobre herramientas de todos los elementos en la galería.|  
|[CMFCRibbonGallery::SelectItem](../Topic/CMFCRibbonGallery::SelectItem.md)||  
|[CMFCRibbonGallery::SetACCData](../Topic/CMFCRibbonGallery::SetACCData.md)|\(Reemplaza [CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md).\)|  
|[CMFCRibbonGallery::SetButtonMode](../Topic/CMFCRibbonGallery::SetButtonMode.md)|Especifica si mostrar la galería de la cinta de opciones como botón desplegable o como paleta directamente en la cinta de opciones.|  
|[CMFCRibbonGallery::SetGroupName](../Topic/CMFCRibbonGallery::SetGroupName.md)|establece el nombre de un grupo.|  
|[CMFCRibbonGallery::SetIconsInRow](../Topic/CMFCRibbonGallery::SetIconsInRow.md)|define el número de elementos por fila en la galería.|  
|[CMFCRibbonGallery::SetItemToolTip](../Topic/CMFCRibbonGallery::SetItemToolTip.md)|establece el texto de información sobre herramientas para un elemento en la galería.|  
|[CMFCRibbonGallery::SetPalette](../Topic/CMFCRibbonGallery::SetPalette.md)|Adjunta una paleta una galería de la cinta de opciones.|  
|[CMFCRibbonGallery::SetPaletteID](../Topic/CMFCRibbonGallery::SetPaletteID.md)|Define el identificador de comando que se envía en el mensaje de `WM_COMMAND` cuando un elemento de la galería se ha seleccionado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonGallery::OnDrawPaletteIcon](../Topic/CMFCRibbonGallery::OnDrawPaletteIcon.md)|Llamado por el marco cuando se dibuja un icono de la galería.|  
  
## Comentarios  
 Un botón de la galería se comporta como un botón de menú normal sólo que muestra una galería cuando abre un usuario.  Cuando selecciona un elemento en una galería, el marco envía el mensaje de `WM_COMMAND` así como el identificador de comando del botón.  Cuando se procesa el mensaje, debe llamar a [CMFCRibbonGallery::GetLastSelectedItem](../Topic/CMFCRibbonGallery::GetLastSelectedItem.md) para determinar qué elemento está seleccionado de la galería.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCRibbonGallery` para configurar un objeto de `CMFCRibbonGallery` .  El ejemplo muestra cómo especificar el número de elementos por fila en la galería, habilitar el tamaño del panel de menú, habilita la barra lateral a la izquierda del elemento emergente, y muestra la galería de la cinta de opciones como paleta directamente en la barra de la cinta de opciones.  Este fragmento de código es parte de [Ejemplo de cliente de dibujo](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#6](../../mfc/reference/codesnippet/CPP/cmfcribbongallery-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md) [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
## Requisitos  
 **encabezado:** afxRibbonPaletteGallery.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonGalleryMenuButton Class](../../mfc/reference/cmfcribbongallerymenubutton-class.md)