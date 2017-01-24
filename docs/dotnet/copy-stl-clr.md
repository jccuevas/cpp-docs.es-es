---
title: "copy (STL/CLR) | Microsoft Docs"
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
  - "cliext::copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copy (función) [STL/CLR]"
ms.assetid: f6738535-fde6-446e-a797-bf2b457c2bff
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# copy (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asigna los valores de elementos de un intervalo de origen a un rango de destino, iterando con la secuencia de origen de elementos y asignándoles nuevas posiciones hacia delante.  
  
## Sintaxis  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
```  
  
## Comentarios  
 Esta función se comporta igual que la función `copy`STL.  Para obtener más información, vea [copy](../Topic/copy.md).  
  
## Requisitos  
 cliext \<\/algoritmo de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [algorithm](../dotnet/algorithm-stl-clr.md)