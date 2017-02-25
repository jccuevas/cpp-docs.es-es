---
title: "CD2DBrush (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DBrush"
  - "afxrendertarget/CD2DBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DBrush (clase)"
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DBrush (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1Brush.  
  
## Sintaxis  
  
```  
class CD2DBrush : public CD2DResource;  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBrush::CD2DBrush](../Topic/CD2DBrush::CD2DBrush.md)|Construye un objeto CD2DBrush.|  
|[CD2DBrush::~CD2DBrush](../Topic/CD2DBrush::~CD2DBrush.md)|El destructor.  Se llama cuando se destruye un objeto Brush D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBrush::Attach](../Topic/CD2DBrush::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md)|Destruye un objeto CD2DBrush.  \(Invalida [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md).\)|  
|[CD2DBrush::Detach](../Topic/CD2DBrush::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DBrush::Get](../Topic/CD2DBrush::Get.md)|Devuelve la interfaz ID2D1Brush|  
|[CD2DBrush::GetOpacity](../Topic/CD2DBrush::GetOpacity.md)|Obtiene el grado de opacidad de este pincel|  
|[CD2DBrush::GetTransform](../Topic/CD2DBrush::GetTransform.md)|Obtiene la transformación actual del destino de representación|  
|[CD2DBrush::IsValid](../Topic/CD2DBrush::IsValid.md)|Comprueba la validez del recurso \(invalida [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\).|  
|[CD2DBrush::SetOpacity](../Topic/CD2DBrush::SetOpacity.md)|Establece el grado de opacidad de este pincel|  
|[CD2DBrush::SetTransform](../Topic/CD2DBrush::SetTransform.md)|Aplica la transformación especificada al destino de representación, reemplazando la transformación existente.  Todas las operaciones de dibujo posteriores se producen en el espacio transformado|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBrush::operator ID2D1Brush\*](../Topic/CD2DBrush::operator%20ID2D1Brush*.md)|Devuelve la interfaz ID2D1Brush|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBrush::m\_pBrush](../Topic/CD2DBrush::m_pBrush.md)|Almacena un puntero a un objeto ID2D1Brush.|  
|[CD2DBrush::m\_pBrushProperties](../Topic/CD2DBrush::m_pBrushProperties.md)|Propiedades de pincel.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)