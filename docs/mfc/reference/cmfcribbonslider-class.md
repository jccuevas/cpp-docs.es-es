---
title: "CMFCRibbonSlider Class | Microsoft Docs"
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
  - "CMFCRibbonSlider"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonSlider class"
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
caps.latest.revision: 43
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonSlider Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCRibbonSlider` implementa un control deslizante que puede agregar a una barra de la cinta de opciones o una barra de estado de la cinta de opciones.  El control deslizante de la cinta de opciones es similar a los controles deslizantes del zoom que aparecen en las aplicaciones de Office 2007.  
  
## Sintaxis  
  
```  
class CMFCRibbonSlider : public CMFCRibbonBaseElement  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonSlider::CMFCRibbonSlider](../Topic/CMFCRibbonSlider::CMFCRibbonSlider.md)|Las construcciones e inicializan un control deslizante de la cinta de opciones.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonSlider::GetPos](../Topic/CMFCRibbonSlider::GetPos.md)|Devuelve la posición actual del control deslizante.|  
|[CMFCRibbonSlider::GetRangeMax](../Topic/CMFCRibbonSlider::GetRangeMax.md)|Devuelve el valor máximo del control deslizante.|  
|[CMFCRibbonSlider::GetRangeMin](../Topic/CMFCRibbonSlider::GetRangeMin.md)|Devuelve el valor mínimo del control deslizante.|  
|[CMFCRibbonSlider::GetRegularSize](../Topic/CMFCRibbonSlider::GetRegularSize.md)|Devuelve el tamaño normal del elemento cinta.  \(Reemplaza [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md).\)|  
|[CMFCRibbonSlider::GetZoomIncrement](../Topic/CMFCRibbonSlider::GetZoomIncrement.md)|Devuelve el tamaño de incremento de zoom para el control deslizante.|  
|[CMFCRibbonSlider::HasZoomButtons](../Topic/CMFCRibbonSlider::HasZoomButtons.md)|Especifica si el control deslizante tiene botones de zoom.|  
|[CMFCRibbonSlider::OnDraw](../Topic/CMFCRibbonSlider::OnDraw.md)|Llamado por el marco para dibujar el elemento cinta.  \(Reemplaza [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md).\)|  
|[CMFCRibbonSlider::SetPos](../Topic/CMFCRibbonSlider::SetPos.md)|Establece la posición actual del control deslizante.|  
|[CMFCRibbonSlider::SetRange](../Topic/CMFCRibbonSlider::SetRange.md)|Especifica el intervalo de control slider estableciendo los valores máximo y mínimo.|  
|[CMFCRibbonSlider::SetZoomButtons](../Topic/CMFCRibbonSlider::SetZoomButtons.md)|Muestra u oculta los botones de zoom.|  
|[CMFCRibbonSlider::SetZoomIncrement](../Topic/CMFCRibbonSlider::SetZoomIncrement.md)|Establece el tamaño de incremento de zoom para el control deslizante.|  
  
## Comentarios  
 Puede utilizar el método de `SetRange` para configurar el intervalo de los incrementos de zoom del control deslizante.  Puede establecer la posición actual del control deslizante utilizando el método de `SetPos` .  
  
 Puede mostrar botones circulares de zoom en el lado izquierdo y derecho del control deslizante utilizando el método de `SetZoomButtons` .  De forma predeterminada, el control deslizante es horizontal, el botón izquierdo de zoom muestra un signo menos y el botón derecho de zoom muestra un signo más.  
  
 El método de `SetZoomIncrement` define el incremento de agregar o para restar de la posición actual cuando un usuario hace clic en los botones de zoom.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCRibbonSlider` para establecer las propiedades del control deslizante.  El ejemplo muestra cómo construir un objeto de `CMFCRibbonSlider` , muestra los botones de zoom, establece la posición actual del control deslizante, y establece el intervalo de valores para el control deslizante.  
  
 [!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/CPP/cmfcribbonslider-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)  
  
## Requisitos  
 **encabezado:** afxribbonslider.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)