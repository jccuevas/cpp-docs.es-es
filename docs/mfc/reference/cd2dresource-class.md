---
title: "CD2DResource (Clase) | Microsoft Docs"
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
  - "afxrendertarget/CD2DResource"
  - "CD2DResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DResource (clase)"
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DResource (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase abstracta que proporciona una interfaz para crear y administrar recursos de D2D como pinceles, capas y textos.  
  
## Sintaxis  
  
```  
class CD2DResource : public CObject;  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DResource::CD2DResource](../Topic/CD2DResource::CD2DResource.md)|Construye un objeto CD2DResource.|  
|[CD2DResource::~CD2DResource](../Topic/CD2DResource::~CD2DResource.md)|El destructor.  Se llama cuando se destruye un objeto de recursos D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DResource::Create](../Topic/CD2DResource::Create.md)|Crea un CD2DResource.|  
|[CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)|Destruye un objeto CD2DResource.|  
|[CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)|Comprueba la validez del recurso|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DResource::IsAutoDestroy](../Topic/CD2DResource::IsAutoDestroy.md)|Compruebe la marca de destruir automática.|  
|[CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md)|Vuelve a crear un CD2DResource.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DResource::m\_bIsAutoDestroy](../Topic/CD2DResource::m_bIsAutoDestroy.md)|El propietario \(CRenderTarget\) destruirá el recurso|  
|[CD2DResource::m\_pParentTarget](../Topic/CD2DResource::m_pParentTarget.md)|Puntero al CRenderTarget primario|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)