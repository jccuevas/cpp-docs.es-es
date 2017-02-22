---
title: "CD2DLayer (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DLayer"
  - "CD2DLayer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DLayer (clase)"
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DLayer (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1Layer.  
  
## Sintaxis  
  
```  
class CD2DLayer : public CD2DResource;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLayer::CD2DLayer](../Topic/CD2DLayer::CD2DLayer.md)|Construye un objeto CD2DLayer.|  
|[CD2DLayer::~CD2DLayer](../Topic/CD2DLayer::~CD2DLayer.md)|El destructor.  Se llama cuando se destruye un objeto en capas D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLayer::Attach](../Topic/CD2DLayer::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DLayer::Create](../Topic/CD2DLayer::Create.md)|Crea un CD2DLayer.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DLayer::Destroy](../Topic/CD2DLayer::Destroy.md)|Destruye un objeto CD2DLayer.  \(Invalida [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md).\)|  
|[CD2DLayer::Detach](../Topic/CD2DLayer::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DLayer::Get](../Topic/CD2DLayer::Get.md)|Devuelve la interfaz ID2D1Layer|  
|[CD2DLayer::GetSize](../Topic/CD2DLayer::GetSize.md)|Devuelve el tamaño del destino de representación en píxeles independientes del dispositivo|  
|[CD2DLayer::IsValid](../Topic/CD2DLayer::IsValid.md)|Comprueba la validez del recurso \(invalida [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\).|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLayer::operator ID2D1Layer\*](../Topic/CD2DLayer::operator%20ID2D1Layer*.md)|Devuelve la interfaz ID2D1Layer|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DLayer::m\_pLayer](../Topic/CD2DLayer::m_pLayer.md)|Almacena un puntero a un objeto ID2D1Layer.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DLayer](../../mfc/reference/cd2dlayer-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)