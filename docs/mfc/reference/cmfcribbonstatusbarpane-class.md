---
title: "CMFCRibbonStatusBarPane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonStatusBarPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonStatusBarPane class"
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCRibbonStatusBarPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCRibbonStatusBarPane` implementa un elemento cinta que puede agregar a una barra de estado de la cinta de opciones.  
  
## Sintaxis  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](../Topic/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane.md)|Las construcciones e inicializan un objeto de `CMFCRibbonStatusBarPane` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](../Topic/CMFCRibbonStatusBarPane::GetAlmostLargeText.md)|Devuelve la cadena que define la cadena de texto más larga que se puede mostrar en el panel sin truncación.|  
|[CMFCRibbonStatusBarPane::GetTextAlign](../Topic/CMFCRibbonStatusBarPane::GetTextAlign.md)|Devuelve la configuración actual de la alineación del texto.|  
|[CMFCRibbonStatusBarPane::IsAnimation](../Topic/CMFCRibbonStatusBarPane::IsAnimation.md)|Determina si la animación está en curso.|  
|[CMFCRibbonStatusBarPane::IsExtended](../Topic/CMFCRibbonStatusBarPane::IsExtended.md)|Determina si el panel se encuentra en el área extendida de la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](../Topic/CMFCRibbonStatusBarPane::OnDrawBorder.md)|\(Reemplaza [CMFCRibbonButton::OnDrawBorder](../Topic/CMFCRibbonButton::OnDrawBorder.md).\)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](../Topic/CMFCRibbonStatusBarPane::OnFillBackground.md)|\(Reemplaza [CMFCRibbonButton::OnFillBackground](../Topic/CMFCRibbonButton::OnFillBackground.md).\)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](../Topic/CMFCRibbonStatusBarPane::SetAlmostLargeText.md)|Define la cadena de texto más larga que se puede mostrar en el panel sin truncación.|  
|[CMFCRibbonStatusBarPane::SetAnimationList](../Topic/CMFCRibbonStatusBarPane::SetAnimationList.md)|Asignaciones del panel que una imagen muestra que se puede utilizar para la animación.|  
|[CMFCRibbonStatusBarPane::SetTextAlign](../Topic/CMFCRibbonStatusBarPane::SetTextAlign.md)|Establece la alineación del texto.|  
|[CMFCRibbonStatusBarPane::StartAnimation](../Topic/CMFCRibbonStatusBarPane::StartAnimation.md)|Inicia la animación que se asigna al panel.|  
|[CMFCRibbonStatusBarPane::StopAnimation](../Topic/CMFCRibbonStatusBarPane::StopAnimation.md)|Detiene la animación que se asigna al panel.  .|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](../Topic/CMFCRibbonStatusBarPane::OnFinishAnimation.md)|Llamado por el marco cuando la animación que se asigna al panel detiene.|  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar los distintos métodos en la clase de `CMFCRibbonStatusBarPane` .  El ejemplo muestra cómo construir un objeto de `CMFCRibbonStatusBarPane` , establece la alineación del texto de la etiqueta del panel de barra de estado, define el texto más largo que se puede mostrar en el panel de barra de estado sin truncación, asociada al panel de barra de estado una imagen de lista que se puede utilizar para la animación, e inicia la animación.  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## Requisitos  
 **encabezado:** afxribbonstatusbarpane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar Class](../../mfc/reference/cmfcribbonstatusbar-class.md)