---
title: "CMFCPropertyGridFontProperty Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPropertyGridFontProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridFontProperty class"
  - "CMFCPropertyGridFontProperty::FormatProperty method"
  - "CMFCPropertyGridFontProperty::OnClickButton method"
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMFCPropertyGridFontProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCPropertyGridFileProperty` admite un elemento de control de la lista de propiedades que abre un cuadro de diálogo de selección de fuente.  
  
## Sintaxis  
  
```  
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty](../Topic/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty.md)|Crea un objeto `CMFCPropertyGridFontProperty`.|  
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCPropertyGridFontProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad.  \(Reemplaza [CMFCPropertyGridProperty::FormatProperty](../Topic/CMFCPropertyGridProperty::FormatProperty.md).\)|  
|[CMFCPropertyGridFontProperty::GetColor](../Topic/CMFCPropertyGridFontProperty::GetColor.md)|Recupera el color de fuente que el usuario selecciona en el cuadro de diálogo fuente.|  
|[CMFCPropertyGridFontProperty::GetLogFont](../Topic/CMFCPropertyGridFontProperty::GetLogFont.md)|Recuperar la fuente que el usuario selecciona en el cuadro de diálogo fuente.|  
|`CMFCPropertyGridFontProperty::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|`CMFCPropertyGridFontProperty::OnClickButton`|Llamado por el marco cuando el usuario hace clic en un botón incluido en una propiedad.  \(Reemplaza [CMFCPropertyGridProperty::OnClickButton](../Topic/CMFCPropertyGridProperty::OnClickButton.md).\)|  
  
## Comentarios  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)  
  
## Requisitos  
 **encabezado:** afxpropertygridctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)