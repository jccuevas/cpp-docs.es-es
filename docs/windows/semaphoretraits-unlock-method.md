---
title: "SemaphoreTraits::Unlock (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SemaphoreTraits::Unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unlock (método)"
ms.assetid: 4e0ea808-b70d-43f7-81ef-998c3b34e3a0
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SemaphoreTraits::Unlock (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Control de versiones desde un recurso compartido.  
  
## Sintaxis  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
#### Parámetros  
 `h`  
 Identificador a un objeto semaphore.  
  
## Comentarios  
 Si la operación de desbloquear es incorrecta, Unlock\(\) emite un error que indica la causa del error.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits  
  
## Vea también  
 [SemaphoreTraits \(Estructura\)](../Topic/SemaphoreTraits%20Structure.md)