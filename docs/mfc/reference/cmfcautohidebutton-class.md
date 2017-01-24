---
title: "CMFCAutoHideButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCAutoHideButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAutoHideButton class"
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCAutoHideButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un botón que muestra u oculta una [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) que se configura para ocultar.  
  
## Sintaxis  
  
```  
class CMFCAutoHideButton : public CObject  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAutoHideButton::BringToTop](../Topic/CMFCAutoHideButton::BringToTop.md)||  
|[CMFCAutoHideButton::Create](../Topic/CMFCAutoHideButton::Create.md)|Crea e inicializa el botón de ocultación automática.|  
|[CMFCAutoHideButton::GetAlignment](../Topic/CMFCAutoHideButton::GetAlignment.md)|Recupera la alineación del botón de ocultación automática.|  
|[CMFCAutoHideButton::GetAutoHideWindow](../Topic/CMFCAutoHideButton::GetAutoHideWindow.md)|Devuelve el objeto [CDockablePane](../../mfc/reference/cdockablepane-class.md) asociado con el botón de ocultación automática.|  
|[CMFCAutoHideButton::GetParentToolBar](../Topic/CMFCAutoHideButton::GetParentToolBar.md)||  
|[CMFCAutoHideButton::GetRect](../Topic/CMFCAutoHideButton::GetRect.md)||  
|[CMFCAutoHideButton::GetSize](../Topic/CMFCAutoHideButton::GetSize.md)|Determina el tamaño del botón de ocultación automática.|  
|[CMFCAutoHideButton::GetTextSize](../Topic/CMFCAutoHideButton::GetTextSize.md)|Devuelve el tamaño de la etiqueta de texto para el botón de ocultación automática.|  
|[CMFCAutoHideButton::HighlightButton](../Topic/CMFCAutoHideButton::HighlightButton.md)|Resalta el botón de ocultación automática.|  
|[CMFCAutoHideButton::IsActive](../Topic/CMFCAutoHideButton::IsActive.md)|Indica si el botón de ocultación automática está activo.|  
|[CMFCAutoHideButton::IsHighlighted](../Topic/CMFCAutoHideButton::IsHighlighted.md)|Devuelve el estado de resaltado del botón de ocultación automática.|  
|[CMFCAutoHideButton::IsHorizontal](../Topic/CMFCAutoHideButton::IsHorizontal.md)|Determina si el botón de ocultación automática es horizontal o vertical.|  
|[CMFCAutoHideButton::IsTop](../Topic/CMFCAutoHideButton::IsTop.md)||  
|[CMFCAutoHideButton::IsVisible](../Topic/CMFCAutoHideButton::IsVisible.md)|Indica si el botón está visible.|  
|[CMFCAutoHideButton::Move](../Topic/CMFCAutoHideButton::Move.md)||  
|[CMFCAutoHideButton::OnDraw](../Topic/CMFCAutoHideButton::OnDraw.md)|El marco de trabajo llama a este método cuando dibuja el botón de ocultación automática.|  
|[CMFCAutoHideButton::OnDrawBorder](../Topic/CMFCAutoHideButton::OnDrawBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un botón de ocultación automática.|  
|[CMFCAutoHideButton::OnFillBackground](../Topic/CMFCAutoHideButton::OnFillBackground.md)|El marco de trabajo llama a este método cuando rellena el fondo de un botón de ocultación automática.|  
|[CMFCAutoHideButton::ReplacePane](../Topic/CMFCAutoHideButton::ReplacePane.md)||  
|[CMFCAutoHideButton::ShowAttachedWindow](../Topic/CMFCAutoHideButton::ShowAttachedWindow.md)|Muestra u oculta la [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) asociada.|  
|[CMFCAutoHideButton::ShowButton](../Topic/CMFCAutoHideButton::ShowButton.md)|Muestra u oculta el botón de ocultación automática.|  
|[CMFCAutoHideButton::UnSetAutoHideMode](../Topic/CMFCAutoHideButton::UnSetAutoHideMode.md)||  
  
## Comentarios  
 Durante la creación, el objeto `CMFCAutoHideButton` se adjunta a una [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  El objeto `CDockablePane` se oculta o se muestra cuando el usuario interactúa con el objeto `CMFCAutoHideButton`.  
  
 De forma predeterminada, el marco de trabajo crea automáticamente un `CMFCAutoHideButton` cuando el usuario activa la ocultación automática.  El marco de trabajo puede crear un elemento de una clase de interfaz de usuario personalizada en lugar de la clase `CMFCAutoHideButton`.  Para especificar qué clase de interfaz de usuario personalizada debería utilizar, establezca la variable de miembro estático `CMFCAutoHideBar::m_pAutoHideButtonRTS` igual que la clase de interfaz de usuario personalizada.  De forma predeterminada, esta variable se establece en `CMFCAutoHideButton`.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo construir un objeto `CMFCAutoHideButton` y usar varios métodos en la clase `CMFCAutoHideButton`.  En el ejemplo se muestra cómo inicializar un objeto `CMFCAutoHideButton` mediante su método `Create`, mostrar la clase asociada `CDockablePane` y mostrar el botón de ocultación automática.  
  
 [!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/CPP/cmfcautohidebutton-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)  
  
## Requisitos  
 **Encabezado:** afxautohidebutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCAutoHideBar Class](../../mfc/reference/cmfcautohidebar-class.md)   
 [CAutoHideDockSite Class](../../mfc/reference/cautohidedocksite-class.md)