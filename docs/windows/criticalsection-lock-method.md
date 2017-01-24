---
title: "CriticalSection::Lock (M&#233;todo) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Lock (método)"
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSection::Lock (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Espera la propiedad del objeto especificado de sección crítica.  La función devuelve cuando el subproceso de la llamada tiene su propiedad.  
  
## Sintaxis  
  
```  
SyncLock Lock();  
  
   static SyncLock Lock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### Parámetros  
 `cs`  
 Un objeto definido por el usuario de la sección crítica.  
  
## Valor devuelto  
 Un objeto de bloqueo que se puede utilizar para desbloquear la sección crítica actual.  
  
## Comentarios  
 La primera función de **Lock** afecta al objeto actual de sección crítica.  La segunda función de **Lock** afecta a una sección crítica definida por el usuario.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [CriticalSection \(Clase\)](../Topic/CriticalSection%20Class.md)