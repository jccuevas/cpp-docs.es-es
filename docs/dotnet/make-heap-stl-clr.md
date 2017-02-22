---
title: "make_heap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::make_heap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_heap (función) [STL/CLR]"
ms.assetid: bc1bed28-7a26-4540-901d-5584cd117ea1
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# make_heap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Convierte los elementos de un intervalo especificado en una pila del primer elemento es el mayor y para el que se puede especificar un criterio de ordenación con un predicado binario.  
  
## Sintaxis  
  
```  
template<class _RanIt> inline  
    void make_heap(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void make_heap(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `make_heap`STL.  Para obtener más información, vea [make\_heap](../Topic/make_heap.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)