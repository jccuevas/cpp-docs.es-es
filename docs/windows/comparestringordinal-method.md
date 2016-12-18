---
title: "CompareStringOrdinal (M&#233;todo) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal"
dev_langs: 
  - "C++"
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CompareStringOrdinal (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```cpp  
  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
#### Parámetros  
 `lhs`  
 El primer HSTRING a comparar.  
  
 `rhs`  
 El segundo HSTRING a comparar.  
  
## Valor devuelto  
  
|Valor|Condition|  
|-----------|---------------|  
|\-1|`lhs` es menor que `rhs`.|  
|0|`lhs` es igual a `rhs`.|  
|1|`lhs` es mayor que `rhs`.|  
  
## Comentarios  
 Compara dos objetos especificados de HSTRING y devuelve un entero que indica la posición relativa en un criterio de ordenación.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::Details  
  
## Vea también  
 [Microsoft::WRL::Wrappers::Details \(Espacio de nombres\)](../windows/microsoft-wrl-wrappers-details-namespace.md)