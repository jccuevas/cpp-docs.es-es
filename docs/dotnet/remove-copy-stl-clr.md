---
title: "remove_copy (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::remove_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_copy (función) [STL/CLR]"
ms.assetid: 602fd8e3-26f7-491f-bf2c-cddf269f9807
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# remove_copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia los elementos de un intervalo de origen a un rango de destino, excepto en que los elementos del valor especificado no se copian, sin perturbar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.  
  
## Sintaxis  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt remove_copy(_InIt _First, _InIt _Last,  
        _OutIt _Dest, const _Ty% _Val);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `remove_copy`STL.  Para obtener más información, vea [remove\_copy](../Topic/remove_copy.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)