---
title: "CMFCRibbonContextCaption Class | Microsoft Docs"
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
  - "CMFCRibbonContextCaption"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonContextCaption class"
ms.assetid: cce2c0a2-8370-4266-997e-f8d0eeb3d616
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonContextCaption Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una leyenda coloreada que aparece en la parte superior de una categoría de la cinta o de una categoría de contexto.  
  
## Sintaxis  
  
```  
class CMFCRibbonContextCaption : public CMFCRibbonButton  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonContextCaption::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCRibbonContextCaption::GetColor](../Topic/CMFCRibbonContextCaption::GetColor.md)|Devuelve el color del título.|  
|[CMFCRibbonContextCaption::GetRightTabX](../Topic/CMFCRibbonContextCaption::GetRightTabX.md)||  
|`CMFCRibbonContextCaption::GetThisClass`|Usado por el marco para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|  
  
## Comentarios  
 No se puede crear una instancia de esta clase directamente.  La clase [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md) usa esta clase internamente para agregar color a las categorías de la cinta de opciones.  
  
 Para establecer el color de las categorías de la cinta de opciones, llame a [CMFCRibbonCategory::SetTabColor](../Topic/CMFCRibbonCategory::SetTabColor.md).  Para establecer el color de las categorías de contexto, llame a [CMFCRibbonBar::AddContextCategory](../Topic/CMFCRibbonBar::AddContextCategory.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonContextCaption](../../mfc/reference/cmfcribboncontextcaption-class.md)  
  
## Requisitos  
 **Encabezado:** afxRibbonBar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonCategory Class](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)