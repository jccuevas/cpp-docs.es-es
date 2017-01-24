---
title: "CMFCImagePaintArea::IMAGE_EDIT_MODE (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IMAGE_EDIT_MODE Enumeration"
  - "CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration"
  - "CMFCImagePaintArea.IMAGE_EDIT_MODE Enumeration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IMAGE_EDIT_MODE Enumeration (método)"
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCImagePaintArea::IMAGE_EDIT_MODE (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica un modo del gráfico que utilizará para modificar una imagen en un cuadro de diálogo del editor de imágenes.  
  
## Sintaxis  
  
```  
enum IMAGE_EDIT_MODE  
{  
   IMAGE_EDIT_MODE_PEN = 0,  
   IMAGE_EDIT_MODE_FILL,  
   IMAGE_EDIT_MODE_LINE,  
   IMAGE_EDIT_MODE_RECT,  
   IMAGE_EDIT_MODE_ELLIPSE,  
   IMAGE_EDIT_MODE_COLOR  
};  
```  
  
## Miembros  
  
|||  
|-|-|  
|Name|Descripción|  
|`IMAGE_EDIT_MODE_PEN`|Utilizado para dibujar los píxeles individuales.|  
|`IMAGE_EDIT_MODE_FILL`|Utilizado para rellenar todas las partes adyacentes que contienen color en la ubicación actual del cursor.|  
|`IMAGE_EDIT_MODE_LINE`|Se utiliza para dibujar una línea.|  
|`IMAGE_EDIT_MODE_RECT`|Utilizado para dibujar un rectángulo.|  
|`IMAGE_EDIT_MODE_ELLIPSE`|Se utiliza para dibujar una elipse.|  
|`IMAGE_EDIT_MODE_COLOR`|Se utiliza para establecer el color actual al color en la ubicación actual del cursor.|  
  
### Comentarios  
 Las clases de `CMFCImagePaintArea` y de `CMFCImageEditorDialog` utilizan esta enumeración para establecer el modo actual del gráfico.  Utilizan el modo y el valor current color de dibujo para modificar el área de imagen en un cuadro de diálogo del editor de imágenes.  Para obtener más información acerca de `CMFCImagePaintArea` y `CMFCImageEditorDialog`, vea [CMFCImagePaintArea Class](../../mfc/reference/cmfcimagepaintarea-class.md) y [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
 Cuando se selecciona un color de una imagen utilizando `IMAGE_EDIT_MODE_COLOR` que drenaba el modo, el marco establece el modo actual del gráfico a `IMAGE_EDIT_MODE_PEN`.  
  
## Requisitos  
 **Encabezado:** afximagepaintarea.h  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCImagePaintArea Class](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)