---
title: "equal_range (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::equal_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal_range (función) [STL/CLR]"
ms.assetid: 1b2e76c3-6b52-486d-9785-2639b54277fd
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# equal_range (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encuentra un par de posiciones en un intervalo petición, el primer o menor que el equivalente a la posición de un elemento especificado y el segundo mayor que la posición del elemento, donde el sentido de equivalencia o de ordenación utilizado para establecer las posiciones de la secuencia se puede especificar por un predicado binario.  
  
## Sintaxis  
  
```  
template<class _FwdIt, class _Ty> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _PAIR_TYPE(_FwdIt) equal_range(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `equal_range`STL.  Para obtener más información, vea [equal\_range](../Topic/equal_range.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)