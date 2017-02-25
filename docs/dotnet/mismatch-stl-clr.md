---
title: "mismatch (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::mismatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mismatch (función) [STL/CLR]"
ms.assetid: 77876875-44bb-4476-afd9-390da4eaac16
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# mismatch (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Compara el elemento de dos intervalos para el elemento de igualdad o su equivalente en cierto modo especificado por un predicado binario y busque la primera posición donde una diferencia aparece.  
  
## Sintaxis  
  
```  
template<class _InIt1, class _InIt2> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
            _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `mismatch`STL.  Para obtener más información, vea [mismatch](../Topic/mismatch.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)