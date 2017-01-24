---
title: "CD2DSolidColorBrush Class | Microsoft Docs"
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
  - "CD2DSolidColorBrush"
  - "afxrendertarget/CD2DSolidColorBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DSolidColorBrush (clase)"
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DSolidColorBrush Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1SolidColorBrush.  
  
## Sintaxis  
  
```  
class CD2DSolidColorBrush : public CD2DBrush;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DSolidColorBrush::CD2DSolidColorBrush](../Topic/CD2DSolidColorBrush::CD2DSolidColorBrush.md)|Sobrecargado.  Construye un objeto CD2DSolidColorBrush.|  
|[CD2DSolidColorBrush::~CD2DSolidColorBrush](../Topic/CD2DSolidColorBrush::~CD2DSolidColorBrush.md)|El destructor.  Se llama cuando se destruye un objeto Brush sólido D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DSolidColorBrush::Attach](../Topic/CD2DSolidColorBrush::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DSolidColorBrush::Create](../Topic/CD2DSolidColorBrush::Create.md)|Crea un CD2DSolidColorBrush.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DSolidColorBrush::Destroy](../Topic/CD2DSolidColorBrush::Destroy.md)|Destruye un objeto CD2DSolidColorBrush.  \(Invalida [CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md).\)|  
|[CD2DSolidColorBrush::Detach](../Topic/CD2DSolidColorBrush::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DSolidColorBrush::Get](../Topic/CD2DSolidColorBrush::Get.md)|Devuelve la interfaz ID2D1SolidColorBrush|  
|[CD2DSolidColorBrush::GetColor](../Topic/CD2DSolidColorBrush::GetColor.md)|Recupera el color del pincel de color sólido|  
|[CD2DSolidColorBrush::SetColor](../Topic/CD2DSolidColorBrush::SetColor.md)|Especifica el color de este pincel de color sólido|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush\*](../Topic/CD2DSolidColorBrush::operator%20ID2D1SolidColorBrush*.md)|Devuelve la interfaz ID2D1SolidColorBrush|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DSolidColorBrush::m\_colorSolid](../Topic/CD2DSolidColorBrush::m_colorSolid.md)|Color sólido del pincel.|  
|[CD2DSolidColorBrush::m\_pSolidColorBrush](../Topic/CD2DSolidColorBrush::m_pSolidColorBrush.md)|Almacena un puntero a un objeto ID2D1SolidColorBrush.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)