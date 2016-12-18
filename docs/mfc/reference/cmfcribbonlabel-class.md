---
title: "CMFCRibbonLabel Class | Microsoft Docs"
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
  - "CMFCRibbonLabel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonLabel class"
ms.assetid: 0346c891-83bf-4f20-b8a1-c84cf2aadced
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonLabel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una etiqueta de texto no\-clickable con una cinta.  
  
## Sintaxis  
  
```  
class CMFCRibbonLabel : public CMFCRibbonButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonLabel::CMFCRibbonLabel](../Topic/CMFCRibbonLabel::CMFCRibbonLabel.md)|Las construcciones e inicializan un objeto de `CMFCRibbonLabel` con la cadena de texto especificada.|  
|`CMFCRibbonLabel::~CMFCRibbonLabel`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonLabel::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonLabel::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCRibbonLabel::SetACCData](../Topic/CMFCRibbonLabel::SetACCData.md)|Determina los datos de accesibilidad para el elemento actual de la etiqueta de cinta.  \(Reemplaza [CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md).\)|  
  
### Comentarios  
 Después de crear una etiqueta de cinta, agréguela a un panel llamando a [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md).  
  
 No puede agregar una etiqueta de cinta de opciones a la barra de herramientas de acceso rápido.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md)  
  
## Requisitos  
 **encabezado:** afxRibbonLabel.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)