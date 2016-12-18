---
title: "accumulate (STL/CLR) | Microsoft Docs"
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
  - "cliext::accumulate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accumulate (función) [STL/CLR]"
ms.assetid: b80e1ef1-1858-4c1d-817b-c42ad1f17a2f
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# accumulate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calcula la suma de todos los elementos en un intervalo especificado como un valor inicial calcular sumas parciales sucesivas o calcula el resultado de los resultados parciales sucesivos obtenidos de igual forma de utilizar una operación binaria especificada distinto de la suma.  
  
## Sintaxis  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función numérica `accumulate`STL.  Para obtener más información, vea [accumulate](../Topic/accumulate.md).  
  
## Requisitos  
 cliext \<de**Encabezado:** \/numérico\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [numeric](../dotnet/numeric-stl-clr.md)