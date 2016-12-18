---
title: "stable_partition (STL/CLR) | Microsoft Docs"
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
  - "cliext::stable_partition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stable_partition (función) [STL/CLR]"
ms.assetid: b82c194c-ae38-4afb-b255-a95a4c2b3101
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stable_partition (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ordena elementos en un intervalo en dos conjuntos disjuntos, con los elementos satisfaciendo un predicado unario que precede a los que no puedan para satisfacerlo, conservando el orden relativo de elementos equivalentes.  
  
## Sintaxis  
  
```  
template<class _BidIt, class _Pr> inline  
    _BidIt stable_partition(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `stable_partition`STL.  Para obtener más información, vea [stable\_partition](../Topic/stable_partition.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)