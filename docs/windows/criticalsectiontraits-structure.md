---
title: "CriticalSectionTraits (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CriticalSectionTraits (estructura)"
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# CriticalSectionTraits (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especial un objeto de CriticalSection para admitir una sección crítica no válida o a una función que libere una sección crítica.  
  
## Sintaxis  
  
```  
struct CriticalSectionTraits;  
```  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`Type`|`typedef` que define un puntero a una sección crítica.  `Type` se define como `typedef CRITICAL_SECTION* Type;`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CriticalSectionTraits::GetInvalidValue \(Método\)](../windows/criticalsectiontraits-getinvalidvalue-method.md)|Especial una plantilla de CriticalSection de modo que la plantilla es siempre no válida.|  
|[CriticalSectionTraits::Unlock \(Método\)](../Topic/CriticalSectionTraits::Unlock%20Method.md)|Especial una plantilla de CriticalSection de modo que admita liberar la propiedad del objeto especificado de sección crítica.|  
  
## Jerarquía de herencia  
 `CriticalSectionTraits`  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::HandleTraits  
  
## Vea también  
 [Microsoft::WRL::Wrappers::HandleTraits \(Espacio de nombres\)](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)