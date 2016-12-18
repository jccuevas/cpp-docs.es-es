---
title: "SRWLockExclusiveTraits (Estructura) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLockExclusiveTraits (estructura)"
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLockExclusiveTraits (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe las características comunes de la clase de SRWLock en modo de bloqueo exclusivo.  
  
## Sintaxis  
  
```  
struct SRWLockExclusiveTraits;  
```  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Type`|Sinónimo de un puntero a la clase de [SRWLOCK](../windows/srwlock-class.md) .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SRWLockExclusiveTraits::GetInvalidValue \(Método\)](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|Recupera un objeto de SRWLockExclusiveTraits que siempre no válido.|  
|[SRWLockExclusiveTraits::Unlock \(Método\)](../windows/srwlockexclusivetraits-unlock-method.md)|Control exclusivo de versiones del objeto especificado de SRWLock.|  
  
## Jerarquía de herencia  
 `SRWLockExclusiveTraits`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits  
  
## Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits \(Espacio de nombres\)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)