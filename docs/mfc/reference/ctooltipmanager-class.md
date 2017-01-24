---
title: "CTooltipManager Class | Microsoft Docs"
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
  - "CTooltipManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTooltipManager class"
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTooltipManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Mantiene información de tiempo de ejecución sobre información sobre herramientas.  La clase `CTooltipManager` se crea una vez por cada aplicación.  
  
## Sintaxis  
  
```  
class CTooltipManager : public CObject  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](../Topic/CTooltipManager::CreateToolTip.md)|Crea un control de información sobre herramientas para el tipo de control de Windows especificado.|  
|[CTooltipManager::DeleteToolTip](../Topic/CTooltipManager::DeleteToolTip.md)|Elimina el control de información sobre herramientas.|  
|[CTooltipManager::SetTooltipParams](../Topic/CTooltipManager::SetTooltipParams.md)|Personaliza la apariencia visual del control de información sobre herramientas para el tipo de control de Windows especificado.|  
|[CTooltipManager::SetTooltipText](../Topic/CTooltipManager::SetTooltipText.md)|Establece el texto y la descripción para un control de información sobre herramientas.|  
|[CTooltipManager::UpdateTooltips](../Topic/CTooltipManager::UpdateTooltips.md)||  
  
## Comentarios  
 Utilice [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo` y `CTooltipManager` juntos para implementar información sobre herramientas personalizada en su aplicación.  Para ver un ejemplo de cómo usar estas clases de información sobre herramientas, vea el tema [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## Requisitos  
 **Encabezado:** afxtooltipmanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo Class](../../mfc/reference/cmfctooltipinfo-class.md)