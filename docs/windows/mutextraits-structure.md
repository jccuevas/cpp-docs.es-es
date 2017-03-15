---
title: "MutexTraits (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MutexTraits (estructura)"
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# MutexTraits (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define las características comunes de la clase de [Mutex](../Topic/Mutex%20Class1.md) .  
  
## Sintaxis  
  
```  
struct MutexTraits : HANDLENullTraits;  
  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[MutexTraits::Unlock \(Método\)](../windows/mutextraits-unlock-method.md)|Control exclusivo de un recurso compartido.|  
  
## Jerarquía de herencia  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits  
  
## Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits \(Espacio de nombres\)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)