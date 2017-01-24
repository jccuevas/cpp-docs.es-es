---
title: "Clase CMFCRibbonColorButton | Microsoft Docs"
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
  - "CMFCRibbonColorButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonColorButton (clase)"
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
caps.latest.revision: 36
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clase CMFCRibbonColorButton
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCRibbonColorButton` implementa un botón en color que puede agregar a una barra de la cinta. El botón de color de la cinta muestra un menú desplegable que contiene una o varias paletas de colores.  
  
## Sintaxis  
  
```  
class CMFCRibbonColorButton : public CMFCRibbonGallery  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCRibbonColorButton::CMFCRibbonColorButton](../Topic/CMFCRibbonColorButton::CMFCRibbonColorButton.md)||  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCRibbonColorButton::AddColorsGroup](../Topic/CMFCRibbonColorButton::AddColorsGroup.md)|Agrega un grupo de colores al área de color normal.|  
|[CMFCRibbonColorButton::EnableAutomaticButton](../Topic/CMFCRibbonColorButton::EnableAutomaticButton.md)|Especifica si el botón **Automático** está habilitado.|  
|[CMFCRibbonColorButton::EnableOtherButton](../Topic/CMFCRibbonColorButton::EnableOtherButton.md)|Habilita el botón **Otros**.|  
|[CMFCRibbonColorButton::GetAutomaticColor](../Topic/CMFCRibbonColorButton::GetAutomaticColor.md)||  
|[CMFCRibbonColorButton::GetColor](../Topic/CMFCRibbonColorButton::GetColor.md)|Devuelve el color actualmente seleccionado.|  
|[CMFCRibbonColorButton::GetColorBoxSize](../Topic/CMFCRibbonColorButton::GetColorBoxSize.md)|Devuelve el tamaño de los elementos de color que aparecen en la barra de colores.|  
|[CMFCRibbonColorButton::GetColumns](../Topic/CMFCRibbonColorButton::GetColumns.md)||  
|[CMFCRibbonColorButton::GetHighlightedColor](../Topic/CMFCRibbonColorButton::GetHighlightedColor.md)|Devuelve el color del elemento actualmente seleccionado en la paleta de colores emergente.|  
|[CMFCRibbonColorButton::RemoveAllColorGroups](../Topic/CMFCRibbonColorButton::RemoveAllColorGroups.md)|Quita todos los grupos de colores del área de color normal.|  
|[CMFCRibbonColorButton::SetColor](../Topic/CMFCRibbonColorButton::SetColor.md)|Selecciona un color del área de color normal.|  
|[CMFCRibbonColorButton::SetColorBoxSize](../Topic/CMFCRibbonColorButton::SetColorBoxSize.md)|Establece el tamaño de los elementos de color que aparecen en la barra de colores.|  
|[CMFCRibbonColorButton::SetColorName](../Topic/CMFCRibbonColorButton::SetColorName.md)||  
|[CMFCRibbonColorButton::SetColumns](../Topic/CMFCRibbonColorButton::SetColumns.md)||  
|[CMFCRibbonColorButton::SetDocumentColors](../Topic/CMFCRibbonColorButton::SetDocumentColors.md)|Especifica una lista de valores RGB para mostrar en el área de color del documento.|  
|[CMFCRibbonColorButton::SetPalette](../Topic/CMFCRibbonColorButton::SetPalette.md)||  
|[CMFCRibbonColorButton::UpdateColor](../Topic/CMFCRibbonColorButton::UpdateColor.md)||  
  
## Comentarios  
 El botón de color de la cinta muestra una barra de color cuando un usuario lo pulsa. De forma predeterminada, esta barra de colores contiene una paleta de selección de color denominada área de color normal. Si lo desea, la barra de colores puede mostrar un botón **Automático**, que permite al usuario seleccionar un color predeterminado, y un botón **Otros**, que muestra una paleta de colores emergente que contiene colores adicionales.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonColorButton`. En el ejemplo se muestra cómo construir un objeto `CMFCRibbonColorButton`, establecer la imagen de gran tamaño, habilitar el botón **Automático**, habilitar el botón **Otros**, establecer el número de columnas, establecer el tamaño de todos los elementos de color que aparecen en la barra de colores, agregar un grupo de colores al área de color normal y especificar una lista de los valores RGB para mostrar en el área de color del documento. Este fragmento de código forma parte del [Ejemplo de cliente de dibujo](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/CPP/cmfcribboncolorbutton-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)  
  
 [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)  
  
## Requisitos  
 **Encabezado:** afxribboncolorbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonGallery Class](../../mfc/reference/cmfcribbongallery-class.md)