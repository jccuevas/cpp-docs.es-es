---
title: "partial_sum (STL/CLR) | Microsoft Docs"
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
  - "cliext::partial_sum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "partial_sum (función) [STL/CLR]"
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# partial_sum (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula una serie de sumas en un rango de entrada del primer elemento a través del elemento th de `i`y almacena el resultado de cada una suma en el elemento th de `i`de un rango de destino o calcula el resultado de un procedimiento general donde la operación de suma se reemplaza por otra operación binaria especificada.  
  
## Sintaxis  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función numérica `partial_sum`STL.  Para obtener más información, vea [partial\_sum](../Topic/partial_sum.md).  
  
## Requisitos  
 cliext \<de**Encabezado:** \/numérico\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [numeric](../dotnet/numeric-stl-clr.md)