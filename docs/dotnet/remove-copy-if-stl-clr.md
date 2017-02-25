---
title: "remove_copy_if (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::remove_copy_if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_copy_if (función) [STL/CLR]"
ms.assetid: 5307f5fe-b6bb-4968-8da1-fea84ab96655
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# remove_copy_if (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia los elementos de un intervalo de origen a un rango de destino, salvo que satisfaciendo un predicado no se copian, sin perturbar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.  
  
## Sintaxis  
  
```  
template<class _InIt, class _OutIt, class _Pr> inline  
    _OutIt remove_copy_if(_InIt _First, _InIt _Last, _OutIt _Dest,  
        _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `remove_copy_if`STL.  Para obtener más información, vea [remove\_copy\_if](../Topic/remove_copy_if.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)