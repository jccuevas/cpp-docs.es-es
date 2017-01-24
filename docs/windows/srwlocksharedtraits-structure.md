---
title: "SRWLockSharedTraits (Estructura) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLockSharedTraits (estructura)"
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLockSharedTraits (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe las características comunes de la clase de SRWLock en modo de bloqueo compartido.  
  
## Sintaxis  
  
```  
struct SRWLockSharedTraits;  
```  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Type`|Sinónimo de un puntero a la clase de [SRWLOCK](../windows/srwlock-class.md) .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLockSharedTraits::GetInvalidValue \(Método\)](../Topic/SRWLockSharedTraits::GetInvalidValue%20Method.md)|Recupera un objeto de SRWLockSharedTraits que siempre no válido.|  
|[SRWLockSharedTraits::Unlock \(Método\)](../Topic/SRWLockSharedTraits::Unlock%20Method.md)|Control exclusivo de versiones del objeto especificado de SRWLock.|  
  
## Jerarquía de herencia  
 `SRWLockSharedTraits`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits  
  
## Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits \(Espacio de nombres\)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)