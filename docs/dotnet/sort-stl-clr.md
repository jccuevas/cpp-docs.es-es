---
title: "sort (STL/CLR) | Microsoft Docs"
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
  - "cliext::sort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sort (función) [STL/CLR]"
ms.assetid: e30f3e97-60c4-4a8e-89f1-75ec056f587a
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# sort (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Organiza los elementos en un intervalo especificado en nondescending petición o según un criterio de ordenación especificado por un predicado binario.  
  
## Sintaxis  
  
```  
template<class _RanIt> inline  
    void sort(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void sort(_RanIt _First, _RanIt _Last, _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `sort`STL.  Para obtener más información, vea [ordenar](../Topic/sort.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)