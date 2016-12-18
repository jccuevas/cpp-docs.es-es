---
title: "CD2DLinearGradientBrush (Clase) | Microsoft Docs"
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
  - "afxrendertarget/CD2DLinearGradientBrush"
  - "CD2DLinearGradientBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DLinearGradientBrush (clase)"
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DLinearGradientBrush (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1LinearGradientBrush.  
  
## Sintaxis  
  
```  
class CD2DLinearGradientBrush : public CD2DGradientBrush;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](../Topic/CD2DLinearGradientBrush::CD2DLinearGradientBrush.md)|Construye un objeto CD2DLinearGradientBrush.|  
|[CD2DLinearGradientBrush::~CD2DLinearGradientBrush](../Topic/CD2DLinearGradientBrush::~CD2DLinearGradientBrush.md)|El destructor.  Se llama cuando se destruye un objeto Brush de degradado lineal D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::Attach](../Topic/CD2DLinearGradientBrush::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DLinearGradientBrush::Create](../Topic/CD2DLinearGradientBrush::Create.md)|Crea un CD2DLinearGradientBrush.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DLinearGradientBrush::Destroy](../Topic/CD2DLinearGradientBrush::Destroy.md)|Destruye un objeto CD2DLinearGradientBrush.  \(Invalida [CD2DGradientBrush::Destroy](../Topic/CD2DGradientBrush::Destroy.md).\)|  
|[CD2DLinearGradientBrush::Detach](../Topic/CD2DLinearGradientBrush::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DLinearGradientBrush::Get](../Topic/CD2DLinearGradientBrush::Get.md)|Devuelve la interfaz ID2D1LinearGradientBrush|  
|[CD2DLinearGradientBrush::GetEndPoint](../Topic/CD2DLinearGradientBrush::GetEndPoint.md)|Recupera las coordenadas finales del degradado lineal.|  
|[CD2DLinearGradientBrush::GetStartPoint](../Topic/CD2DLinearGradientBrush::GetStartPoint.md)|Recupera las coordenadas iniciales del degradado lineal.|  
|[CD2DLinearGradientBrush::SetEndPoint](../Topic/CD2DLinearGradientBrush::SetEndPoint.md)|Establece las coordenadas finales del degradado lineal en el espacio de la coordenada del pincel|  
|[CD2DLinearGradientBrush::SetStartPoint](../Topic/CD2DLinearGradientBrush::SetStartPoint.md)|Establece las coordenadas iniciales del degradado lineal en el espacio de la coordenada del pincel|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush\*](../Topic/CD2DLinearGradientBrush::operator%20ID2D1LinearGradientBrush*.md)|Devuelve la interfaz ID2D1LinearGradientBrush|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLinearGradientBrush::m\_LinearGradientBrushProperties](../Topic/CD2DLinearGradientBrush::m_LinearGradientBrushProperties.md)|El extremo final e inicial del degradado.|  
|[CD2DLinearGradientBrush::m\_pLinearGradientBrush](../Topic/CD2DLinearGradientBrush::m_pLinearGradientBrush.md)|Puntero a ID2D1LinearGradientBrush.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 [CD2DLinearGradientBrush](../../mfc/reference/cd2dlineargradientbrush-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)