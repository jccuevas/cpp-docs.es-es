---
title: "adjacent_difference (STL/CLR) | Microsoft Docs"
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
  - "cliext::adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "adjacent_difference (función)"
ms.assetid: 2b462e2e-b8f2-4b2e-9b87-5f688d8da9f4
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# adjacent_difference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula las diferencias sucesivas entre cada elemento y su predecesor en un rango de entrada y produce resultados a un rango de destino o calcula el resultado de un procedimiento general donde la operación de la diferencia se reemplaza por otro, operación binaria especificada.  
  
## Sintaxis  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función numérica `adjacent_difference`STL.  Para obtener más información, vea [adjacent\_difference](../Topic/adjacent_difference.md).  
  
## Requisitos  
 cliext \<de**Encabezado:** \/numérico\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [numeric](../dotnet/numeric-stl-clr.md)