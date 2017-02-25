---
title: "CMFCImagePaintArea Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCImagePaintArea"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCImagePaintArea class"
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CMFCImagePaintArea Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona el área de imagen que se utiliza para modificar una imagen en un cuadro de diálogo del editor de imágenes.  
  
## Sintaxis  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCImagePaintArea::CMFCImagePaintArea](../Topic/CMFCImagePaintArea::CMFCImagePaintArea.md)|Crea un objeto `CMFCImagePaintArea`.|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCImagePaintArea::GetMode](../Topic/CMFCImagePaintArea::GetMode.md)|Recupera el modo actual del gráfico.|  
|[CMFCImagePaintArea::SetBitmap](../Topic/CMFCImagePaintArea::SetBitmap.md)|establece la imagen de mapa de bits para el área de imagen.|  
|[CMFCImagePaintArea::SetColor](../Topic/CMFCImagePaintArea::SetColor.md)|establece el gráfico color actual.|  
|[CMFCImagePaintArea::SetMode](../Topic/CMFCImagePaintArea::SetMode.md)|Establece el modo actual del gráfico.|  
  
### Comentarios  
 Esta clase no está pensada para utilizarla directamente desde el código.  
  
 El marco de trabajo usa esta clase para mostrar el área de imagen en un cuadro de diálogo del editor de imágenes.  Para obtener más información sobre el cuadro de diálogo editor de imágenes, vea [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de clase de `CMFCImagePaintArea` , establece el gráfico color actual, establece el modo actual de dibujo, y establece la imagen de mapa de bits para el área de imagen.  
  
 [!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/CPP/cmfcimagepaintarea-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## Requisitos  
 **encabezado:** afximagepaintarea.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)