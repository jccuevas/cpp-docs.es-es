---
title: "CD2DGradientBrush (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DGradientBrush"
  - "afxrendertarget/CD2DGradientBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGradientBrush (clase)"
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DGradientBrush (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base de las clases CD2DRadialGradientBrush y CD2DLinearGradientBrush.  
  
## Sintaxis  
  
```  
class CD2DGradientBrush : public CD2DBrush;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGradientBrush::CD2DGradientBrush](../Topic/CD2DGradientBrush::CD2DGradientBrush.md)|Construye un objeto CD2DGradientBrush.|  
|[CD2DGradientBrush::~CD2DGradientBrush](../Topic/CD2DGradientBrush::~CD2DGradientBrush.md)|El destructor.  Se llama cuando se destruye un objeto Brush de degradado D2D.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGradientBrush::Destroy](../Topic/CD2DGradientBrush::Destroy.md)|Destruye un objeto CD2DGradientBrush.  \(Invalida [CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md).\)|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGradientBrush::m\_arGradientStops](../Topic/CD2DGradientBrush::m_arGradientStops.md)|Matriz de las estructuras D2D1\_GRADIENT\_STOP.|  
|[CD2DGradientBrush::m\_colorInterpolationGamma](../Topic/CD2DGradientBrush::m_colorInterpolationGamma.md)|Se realiza el espacio en el que se detiene la interpolación del color entre el degradado.|  
|[CD2DGradientBrush::m\_extendMode](../Topic/CD2DGradientBrush::m_extendMode.md)|El comportamiento del degradado fuera del rango normalizado \[0,1\].|  
|[CD2DGradientBrush::m\_pGradientStops](../Topic/CD2DGradientBrush::m_pGradientStops.md)|Puntero a una matriz de estructuras D2D1\_GRADIENT\_STOP.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)