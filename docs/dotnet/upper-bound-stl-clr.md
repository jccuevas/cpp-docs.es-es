---
title: "upper_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound (función) [STL/CLR]"
ms.assetid: a377a77b-8005-496e-85ae-b431a9b2f0b9
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encuentra la posición del primer elemento en un intervalo ordenado que tiene un valor mayor que un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.  
  
## Sintaxis  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt upper_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `upper_bound`STL.  Para obtener más información, vea [upper\_bound](../Topic/upper_bound.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)