---
title: "random_shuffle (STL/CLR) | Microsoft Docs"
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
  - "cliext::random_shuffle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "random_shuffle (función) [STL/CLR]"
ms.assetid: 0f9d93e2-f50f-40e6-bbe4-2ca3231a895e
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# random_shuffle (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

¡Reorganiza una secuencia de elementos de `N` en un intervalo en uno de `N`\! organizaciones posibles seleccionadas al azar.  
  
## Sintaxis  
  
```  
template<class _RanIt> inline  
    void random_shuffle(_RanIt _First, _RanIt _Last);  
template<class _RanIt, class _Fn1> inline  
    void random_shuffle(_RanIt _First, _RanIt _Last, _Fn1% _Func);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `random_shuffle`STL.  Para obtener más información, vea [random\_shuffle](../Topic/random_shuffle.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)