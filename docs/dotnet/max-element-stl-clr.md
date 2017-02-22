---
title: "max_element (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::max_element"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "max_element (función) [STL/CLR]"
ms.assetid: c6274bae-1216-4285-b395-254280253dae
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# max_element (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Busca la primera aparición del elemento mayor en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.  
  
## Sintaxis  
  
```  
template<class _FwdIt> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `max_element`STL.  Para obtener más información, vea [max\_element](../Topic/max_element.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)