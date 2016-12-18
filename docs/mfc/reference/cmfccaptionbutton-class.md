---
title: "CMFCCaptionButton Class | Microsoft Docs"
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
  - "CMFCCaptionButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCCaptionButton class"
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCCaptionButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCCaptionButton` implementa un botón que se muestra en la barra de título de un panel acoplable o una ventana de marco recudido.  Normalmente, el marco de trabajo crea botones de título automáticamente.  
  
## Sintaxis  
  
```  
class CMFCCaptionButton : public CObject  
```  
  
## Members  
  
### Constructores  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCCaptionButton::CMFCCaptionButton](../Topic/CMFCCaptionButton::CMFCCaptionButton.md)|construye un objeto de CMFCCaptionButton.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCCaptionButton::GetHit](../Topic/CMFCCaptionButton::GetHit.md)|devuelve el comando representado por el botón.|  
|[CMFCCaptionButton::GetIconID](../Topic/CMFCCaptionButton::GetIconID.md)|Devuelve el identificador de la imagen asociado al botón.|  
|[CMFCCaptionButton::GetRect](../Topic/CMFCCaptionButton::GetRect.md)|devuelve el rectángulo ocupado por el botón.|  
|[CMFCCaptionButton::GetSize](../Topic/CMFCCaptionButton::GetSize.md)|Devuelve el ancho y el alto del botón.|  
|[CMFCCaptionButton::IsMiniFrameButton](../Topic/CMFCCaptionButton::IsMiniFrameButton.md)|Indica si el alto de la barra de título está establecido en mini tamaño.|  
|[CMFCCaptionButton::Move](../Topic/CMFCCaptionButton::Move.md)|Establece el estado de la ubicación de dibujo de botón y de presentación de la ventana.|  
|[CMFCCaptionButton::OnDraw](../Topic/CMFCCaptionButton::OnDraw.md)|Dibuja el botón de título.|  
|[CMFCCaptionButton::SetMiniFrameButton](../Topic/CMFCCaptionButton::SetMiniFrameButton.md)|Establece es el mínimo tamaño de la barra de título.|  
  
## Comentarios  
 Puede derivar una clase de [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md) y utilizar el método protegido, `AddButton`, para agregar botones de título a una mini ventana de marco.  
  
 CPaneFrameWnd.h define los id. de comando para dos tipos de botones de título:  
  
-   `AFX_CAPTION_BTN_PIN`, que muestra un botón de alfiler cuando el panel acoplable admite oculta automáticamente el modo.  
  
-   `AFX_CAPTION_BTN_CLOSE`, que muestra un botón de **Cerrar** cuando el panel puede cerrarse u ocultar.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de `CMFCCaptionButton` y establecer es el mínimo tamaño de la barra de título.  
  
 [!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/CPP/cmfccaptionbutton-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)  
  
## Requisitos  
 **encabezado:** afxcaptionbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)