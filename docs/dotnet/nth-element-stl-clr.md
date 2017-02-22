---
title: "nth_element (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::nth_element"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nth_element (función) [STL/CLR]"
ms.assetid: 19fc1695-62a9-4f85-9920-d153c1c6481f
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# nth_element (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las particiones un intervalo de elementos, correctamente situando el elemento th de `n`de la secuencia en el intervalo de modo que todos los elementos delante de menor o igual que él y todos los elementos que lo siguen en la secuencia se mayor o igual que.  
  
## Sintaxis  
  
```  
template<class _RanIt> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last);  
template<class _RanIt, class _Pr> inline  
    void nth_element(_RanIt _First, _RanIt _Nth, _RanIt _Last,  
        _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `nth_element`STL.  Para obtener más información, vea [nth\_element](../Topic/nth_element.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)