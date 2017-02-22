---
title: "CD2DRadialGradientBrush Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DRadialGradientBrush"
  - "afxrendertarget/CD2DRadialGradientBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DRadialGradientBrush (clase)"
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DRadialGradientBrush Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1RadialGradientBrush.  
  
## Sintaxis  
  
```  
class CD2DRadialGradientBrush : public CD2DGradientBrush;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](../Topic/CD2DRadialGradientBrush::CD2DRadialGradientBrush.md)|Construye un objeto CD2DLinearGradientBrush.|  
|[CD2DRadialGradientBrush::~CD2DRadialGradientBrush](../Topic/CD2DRadialGradientBrush::~CD2DRadialGradientBrush.md)|El destructor.  Se llama cuando se destruye un objeto Brush de degradado radial D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::Attach](../Topic/CD2DRadialGradientBrush::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DRadialGradientBrush::Create](../Topic/CD2DRadialGradientBrush::Create.md)|Crea un CD2DRadialGradientBrush.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DRadialGradientBrush::Destroy](../Topic/CD2DRadialGradientBrush::Destroy.md)|Destruye un objeto CD2DRadialGradientBrush.  \(Invalida [CD2DGradientBrush::Destroy](../Topic/CD2DGradientBrush::Destroy.md).\)|  
|[CD2DRadialGradientBrush::Detach](../Topic/CD2DRadialGradientBrush::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DRadialGradientBrush::Get](../Topic/CD2DRadialGradientBrush::Get.md)|Devuelve la interfaz ID2D1RadialGradientBrush|  
|[CD2DRadialGradientBrush::GetCenter](../Topic/CD2DRadialGradientBrush::GetCenter.md)|Recupera el centro de la elipse del degradado|  
|[CD2DRadialGradientBrush::GetGradientOriginOffset](../Topic/CD2DRadialGradientBrush::GetGradientOriginOffset.md)|Recupera el desplazamiento del origen del degradado relativo al centro de la elipse del degradado|  
|[CD2DRadialGradientBrush::GetRadiusX](../Topic/CD2DRadialGradientBrush::GetRadiusX.md)|Recupera el radio X de la elipse del degradado|  
|[CD2DRadialGradientBrush::GetRadiusY](../Topic/CD2DRadialGradientBrush::GetRadiusY.md)|Recupera el radio Y de la elipse del degradado|  
|[CD2DRadialGradientBrush::SetCenter](../Topic/CD2DRadialGradientBrush::SetCenter.md)|Especifica el centro de la elipse del degradado en el espacio de la coordenada del pincel|  
|[CD2DRadialGradientBrush::SetGradientOriginOffset](../Topic/CD2DRadialGradientBrush::SetGradientOriginOffset.md)|Especifica el desplazamiento del origen del degradado relativo al centro de la elipse del degradado|  
|[CD2DRadialGradientBrush::SetRadiusX](../Topic/CD2DRadialGradientBrush::SetRadiusX.md)|Especifica el radio X de la elipse del degradado, en el espacio de la coordenada del pincel|  
|[CD2DRadialGradientBrush::SetRadiusY](../Topic/CD2DRadialGradientBrush::SetRadiusY.md)|Especifica el radio Y de la elipse del degradado, en el espacio de la coordenada del pincel|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush\*](../Topic/CD2DRadialGradientBrush::operator%20ID2D1RadialGradientBrush*.md)|Devuelve la interfaz ID2D1RadialGradientBrush|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DRadialGradientBrush::m\_pRadialGradientBrush](../Topic/CD2DRadialGradientBrush::m_pRadialGradientBrush.md)|Puntero a ID2D1RadialGradientBrush.|  
|[CD2DRadialGradientBrush::m\_RadialGradientBrushProperties](../Topic/CD2DRadialGradientBrush::m_RadialGradientBrushProperties.md)|El centro, desplazamiento del origen del degradado, además del radio X y el radio Y del degradado del pincel.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 [CD2DRadialGradientBrush](../../mfc/reference/cd2dradialgradientbrush-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)