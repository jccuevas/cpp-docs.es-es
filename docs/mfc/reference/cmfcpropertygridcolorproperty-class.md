---
title: "CMFCPropertyGridColorProperty Class | Microsoft Docs"
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
  - "CMFCPropertyGridColorProperty"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPropertyGridColorProperty class"
  - "CMFCPropertyGridColorProperty::FormatProperty method"
  - "CMFCPropertyGridColorProperty::OnClickButton method"
  - "CMFCPropertyGridColorProperty::OnDrawValue method"
  - "CMFCPropertyGridColorProperty::OnEdit method"
  - "CMFCPropertyGridColorProperty::OnUpdateValue method"
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPropertyGridColorProperty Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCPropertyGridColorProperty` admite un elemento de control de la lista de propiedades que abre un cuadro de diálogo de selección de color.  
  
## Sintaxis  
  
```  
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](../Topic/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty.md)|Construye un objeto `CMFCPropertyGridColorProperty`.|  
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|Destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](../Topic/CMFCPropertyGridColorProperty::EnableAutomaticButton.md)|Habilita el botón *automático* botón en el cuadro de diálogo de selección de color.  \(El botón automático estándar tiene la etiqueta **Automático**\).|  
|[CMFCPropertyGridColorProperty::EnableOtherButton](../Topic/CMFCPropertyGridColorProperty::EnableOtherButton.md)|Habilita el botón *otros* en el cuadro de diálogo de selección de color.  \(El botón estándar otros tiene la etiqueta **Más colores...**\).|  
|`CMFCPropertyGridColorProperty::FormatProperty`|Da formato a la representación de texto de un valor de propiedad.  \(Invalida [CMFCPropertyGridProperty::FormatProperty](../Topic/CMFCPropertyGridProperty::FormatProperty.md)\).|  
|[CMFCPropertyGridColorProperty::GetColor](../Topic/CMFCPropertyGridColorProperty::GetColor.md)|Obtiene el color actual de la propiedad.|  
|`CMFCPropertyGridColorProperty::GetThisClass`|Lo usa el marco para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|  
|`CMFCPropertyGridColorProperty::OnClickButton`|Lo llama el marco cuando el usuario hace clic en un botón que se encuentra en una propiedad.  \(Invalida [CMFCPropertyGridProperty::OnClickButton](../Topic/CMFCPropertyGridProperty::OnClickButton.md)\).|  
|`CMFCPropertyGridColorProperty::OnDrawValue`|Lo llama el marco para mostrar el valor de la propiedad.  \(Invalida [CMFCPropertyGridProperty::OnDrawValue](../Topic/CMFCPropertyGridProperty::OnDrawValue.md)\).|  
|`CMFCPropertyGridColorProperty::OnEdit`|Lo llama el marco cuando el usuario está a punto de modificar un valor de propiedad.  \(Invalida [CMFCPropertyGridProperty::OnEdit](../Topic/CMFCPropertyGridProperty::OnEdit.md)\).|  
|`CMFCPropertyGridColorProperty::OnUpdateValue`|Lo llama el marco cuando el valor de una propiedad editable ha cambiado.  \(Invalida [CMFCPropertyGridProperty::OnUpdateValue](../Topic/CMFCPropertyGridProperty::OnUpdateValue.md)\).|  
|[CMFCPropertyGridColorProperty::SetColor](../Topic/CMFCPropertyGridColorProperty::SetColor.md)|Establece un nuevo color para la propiedad.|  
|[CMFCPropertyGridColorProperty::SetColumnsNumber](../Topic/CMFCPropertyGridColorProperty::SetColumnsNumber.md)|Especifica el número de columnas de la cuadrícula de propiedades de color actual.|  
|[CMFCPropertyGridColorProperty::SetOriginalValue](../Topic/CMFCPropertyGridColorProperty::SetOriginalValue.md)|Establece el valor original de una propiedad editable.|  
  
## Comentarios  
 La clase `CMFCPropertyGridColorProperty` admite una propiedad de color que puede agregarse a un control de lista de propiedades.  Para obtener más información, consulte [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la clase `CMFCPropertyGridColorProperty` y configurarlo con varios métodos de la clase `CMFCPropertyGridColorProperty`.  El código explica cómo habilitar los botones automáticos y otros botones, y cómo establecer el color y el número de columnas.  Este ejemplo forma parte del [ejemplo de controles nuevos](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/CPP/cmfcpropertygridcolorproperty-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)  
  
## Requisitos  
 **Encabezado:** afxpropertygridctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty Class](../../mfc/reference/cmfcpropertygridproperty-class.md)