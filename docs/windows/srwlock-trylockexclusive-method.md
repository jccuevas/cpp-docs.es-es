---
title: "SRWLock::TryLockExclusive (M&#233;todo) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryLockExclusive (método)"
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLock::TryLockExclusive (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Intenta adquirir un objeto de SRWLock en modo exclusivo para la actual o el objeto especificado de SRWLock.  Si la llamada se realiza correctamente, el subproceso de llamada toma la propiedad del bloqueo.  
  
## Sintaxis  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### Parámetros  
 `lock`  
 Puntero a un objeto de SRWLock.  
  
## Valor devuelto  
 Si es correcto, un objeto de SRWLock en modo exclusivo y el subproceso de llamada toma la propiedad del bloqueo.  Si no, un objeto de SRWLock cuyo estado no es válida.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [SRWLock \(Clase\)](../windows/srwlock-class.md)