---
title: "SRWLock::TryLockShared (M&#233;todo) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryLockShared (método)"
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLock::TryLockShared (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Intenta adquirir un objeto de SRWLock en modo compartido para la actual o el objeto especificado de SRWLock.  
  
## Sintaxis  
  
```  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### Parámetros  
 `lock`  
 Puntero a un objeto de SRWLock.  
  
## Valor devuelto  
 Si es correcto, un objeto de SRWLock en modo compartido y el subproceso de llamada toma la propiedad del bloqueo.  Si no, un objeto de SRWLock cuyo estado no es válida.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers  
  
## Vea también  
 [SRWLock \(Clase\)](../windows/srwlock-class.md)