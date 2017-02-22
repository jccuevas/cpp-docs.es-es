---
title: "binary_search (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::binary_search"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_search (función) [STL/CLR]"
ms.assetid: 520869cc-7cd3-4c81-b439-05f042474416
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# binary_search (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si hay un elemento en un intervalo ordenado que sea igual a un valor especificado o equivalente a este del modo especificado por un predicado binario.  
  
## Sintaxis  
  
```  
template<class _FwdIt, class _Ty> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    bool binary_search(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `binary_search`STL.  Para obtener más información, vea [binary\_search](../Topic/binary_search.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)