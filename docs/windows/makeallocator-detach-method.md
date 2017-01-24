---
title: "MakeAllocator::Detach (M&#233;todo) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::MakeAllocator::Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach (método)"
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MakeAllocator::Detach (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
__forceinline void Detach();  
```  
  
## Comentarios  
 Desasocia la memoria asignada por el método de [Asigna](../Topic/MakeAllocator::Allocate%20Method.md) del objeto actual de MakeAllocator.  
  
 Si llama a Detach\(\), es responsable de eliminar memoria del método de Allocate.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [MakeAllocator \(Clase\)](../windows/makeallocator-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)