---
title: "stable_sort (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stable_sort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stable_sort (función) [STL/CLR]"
ms.assetid: c28fc2df-c68b-4923-ac16-9f8edd926fbb
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# stable_sort (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Organiza los elementos en un intervalo especificado en nondescending petición o según un criterio de ordenación especificado por un predicado binario y conserva el orden relativo de elementos equivalentes.  
  
## Sintaxis  
  
```  
template<class _BidIt> inline  
    void stable_sort(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `stable_sort`STL.  Para obtener más información, vea [stable\_sort](../Topic/stable_sort.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)