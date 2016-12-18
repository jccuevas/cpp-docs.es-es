---
title: "CDrawingManager Class | Microsoft Docs"
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
  - "CDrawingManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDrawingManager class"
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
caps.latest.revision: 30
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDrawingManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CDrawingManager` implementa algoritmos complejos del gráfico.  
  
## Sintaxis  
  
```  
class CDrawingManager : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDrawingManager::CDrawingManager](../Topic/CDrawingManager::CDrawingManager.md)|Crea un objeto `CDrawingManager`.|  
|`CDrawingManager::~CDrawingManager`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDrawingManager::CreateBitmap\_32](../Topic/CDrawingManager::CreateBitmap_32.md)|Crea un mapa de bits independiente del dispositivo de \(DIB\) 32 bits que las aplicaciones puedan escribir directamente.|  
|[CDrawingManager::DrawAlpha](../Topic/CDrawingManager::DrawAlpha.md)|Muestra los mapas de bits que tienen píxeles transparentes o semitransparentes.|  
|[CDrawingManager::DrawRotated](../Topic/CDrawingManager::DrawRotated.md)|Gira un dentro del contenido de DC de origen el rectángulo especificado por \+\/\- 90 grados|  
|[CDrawingManager::DrawEllipse](../Topic/CDrawingManager::DrawEllipse.md)|Dibuja una elipse con el relleno y los colores del borde proporcionados.|  
|[CDrawingManager::DrawGradientRing](../Topic/CDrawingManager::DrawGradientRing.md)|Dibuja un anillo y lo rellena con un degradado de color.|  
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](../Topic/CDrawingManager::DrawLine,%20CDrawingManager::DrawLineA.md)|Dibuja una línea.|  
|[CDrawingManager::DrawRect](../Topic/CDrawingManager::DrawRect.md)|Dibuja un rectángulo con el relleno y los colores del borde proporcionados.|  
|[CDrawingManager::DrawShadow](../Topic/CDrawingManager::DrawShadow.md)|Dibuja una sombra de un área rectangular.|  
|[CDrawingManager::Fill4ColorsGradient](../Topic/CDrawingManager::Fill4ColorsGradient.md)|rellena un área rectangular con degradados bicolores.|  
|[CDrawingManager::FillGradient](../Topic/CDrawingManager::FillGradient.md)|Rellena un área rectangular con un degradado de color especificado.|  
|[CDrawingManager::FillGradient2](../Topic/CDrawingManager::FillGradient2.md)|Rellena un área rectangular con un degradado de color especificado.  Especifique la dirección del cambio de color de degradado también.|  
|[CDrawingManager::GrayRect](../Topic/CDrawingManager::GrayRect.md)|rellena un rectángulo con un color gris especificado.|  
|[CDrawingManager::HighlightRect](../Topic/CDrawingManager::HighlightRect.md)|Resalta un área rectangular.|  
|[CDrawingManager::HLStoRGB\_ONE](../Topic/CDrawingManager::HLStoRGB_ONE.md)|Convierte un color de una representación de HLS en una representación RGB.|  
|[CDrawingManager::HLStoRGB\_TWO](../Topic/CDrawingManager::HLStoRGB_TWO.md)|Convierte un color de una representación de HLS en una representación RGB.|  
|[CDrawingManager::HSVtoRGB](../Topic/CDrawingManager::HSVtoRGB.md)|Convierte un color de una representación de HSV en una representación RGB.|  
|[CDrawingManager::HuetoRGB](../Topic/CDrawingManager::HuetoRGB.md)|Método auxiliar que convierte un valor de matiz un componente rojo, verde, o azul.|  
|[CDrawingManager::MirrorRect](../Topic/CDrawingManager::MirrorRect.md)|Mueve volteado un área rectangular.|  
|[CDrawingManager::PixelAlpha](../Topic/CDrawingManager::PixelAlpha.md)|Método auxiliar que determina el color final para un píxel semitransparente.|  
|[CDrawingManager::PrepareShadowMask](../Topic/CDrawingManager::PrepareShadowMask.md)|Crea un mapa de bits que se puede utilizar como sombra.|  
|[CDrawingManager::RGBtoHSL](../Topic/CDrawingManager::RGBtoHSL.md)|Convierte un color de una representación RGB a una representación HSL.|  
|[CDrawingManager::RGBtoHSV](../Topic/CDrawingManager::RGBtoHSV.md)|Convierte un color de una representación RGB en una representación de HSV.|  
|[CDrawingManager::SetAlphaPixel](../Topic/CDrawingManager::SetAlphaPixel.md)|Método auxiliar que colores un píxel parcialmente transparente en un mapa de bits.|  
|[CDrawingManager::SetPixel](../Topic/CDrawingManager::SetPixel.md)|Método auxiliar que cambia un único píxel en un mapa de bits al color especificado.|  
|[CDrawingManager::SmartMixColors](../Topic/CDrawingManager::SmartMixColors.md)|Combina dos colores basándose en una proporción ponderada.|  
  
## Comentarios  
 La clase de `CDrawingManager` proporciona funciones para las sombras, de los degradados de color, y los rectángulos resaltado.  También realiza mezcla alfa.  Puede utilizar esta clase para cambiar directamente la interfaz de usuario de la aplicación.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md)  
  
## Requisitos  
 **encabezado:** afxdrawmanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)