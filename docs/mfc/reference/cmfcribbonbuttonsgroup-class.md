---
title: "CMFCRibbonButtonsGroup (Clase) | Microsoft Docs"
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
  - "CMFCRibbonButtonsGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonButtonsGroup (clase)"
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonButtonsGroup (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCRibbonButtonsGroup` permite organizar un conjunto de botones de la cinta de opciones en un grupo.  Todos los botones en el grupo están directamente adyacente a otro horizontalmente y agregados en un borde.  
  
## Sintaxis  
  
```  
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement  
```  
  
## Members  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](../Topic/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup.md)|Crea un objeto `CMFCRibbonButtonsGroup`.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCRibbonButtonsGroup::AddButton](../Topic/CMFCRibbonButtonsGroup::AddButton.md)|Agrega un botón a un grupo.|  
|[CMFCRibbonButtonsGroup::AddButtons](../Topic/CMFCRibbonButtonsGroup::AddButtons.md)|Agrega una lista de botones a un grupo.|  
|[CMFCRibbonButtonsGroup::GetButton](../Topic/CMFCRibbonButtonsGroup::GetButton.md)|Devuelve un puntero al botón que se encuentra en el índice especificado.|  
|[CMFCRibbonButtonsGroup::GetCount](../Topic/CMFCRibbonButtonsGroup::GetCount.md)|Devuelve el número de botones en el grupo.|  
|[CMFCRibbonButtonsGroup::GetImageSize](../Topic/CMFCRibbonButtonsGroup::GetImageSize.md)|Devuelve el tamaño de imagen de las imágenes normales en el grupo de la cinta \(reemplaza [CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md).\)|  
|[CMFCRibbonButtonsGroup::GetRegularSize](../Topic/CMFCRibbonButtonsGroup::GetRegularSize.md)|Devuelve el tamaño normal del elemento cinta \(reemplaza [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md).\)|  
|[CMFCRibbonButtonsGroup::HasImages](../Topic/CMFCRibbonButtonsGroup::HasImages.md)|Notifica si el objeto de `CMFCRibbonButtonsGroup` contiene imágenes de la barra de herramientas.|  
|[CMFCRibbonButtonsGroup::OnDrawImage](../Topic/CMFCRibbonButtonsGroup::OnDrawImage.md)|Dibuja la imagen adecuada para un botón especificado, dependiendo de si el botón es normal, resaltado o deshabilitado.|  
|[CMFCRibbonButtonsGroup::RemoveAll](../Topic/CMFCRibbonButtonsGroup::RemoveAll.md)|Quita todos los botones del objeto de `CMFCRibbonButtonsGroup`.|  
|[CMFCRibbonButtonsGroup::SetImages](../Topic/CMFCRibbonButtonsGroup::SetImages.md)|Asigna imágenes al grupo.|  
|[CMFCRibbonButtonsGroup::SetParentCategory](../Topic/CMFCRibbonButtonsGroup::SetParentCategory.md)|Establece `CMFCRibbonCategory` primario del objeto de `CMFCRibbonButtonsGroup` y todos los botones dentro de \(reemplaza [CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md).\)|  
  
## Comentarios  
 Derivan de [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) y se puede manipular el grupo como una entidad única.  Puede colocar el grupo en cualquier panel o menú emergente.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCRibbonButtonsGroup`.  El ejemplo muestra cómo construir un objeto de `CMFCRibbonButtonsGroup`, asignar imágenes al grupo de botones de la cinta de opciones, y agregar un botón al grupo de botones de la cinta de opciones.  Este fragmento de código es parte de [Ejemplo de cliente de dibujo](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/CPP/cmfcribbonbuttonsgroup-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)  
  
## Requisitos  
 **Encabezado:** afxribbonbuttonsgroup.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)