---
title: "Error del evaluador de expresiones CXX0045 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0045"
  - "CXX0045"
ms.assetid: 32181bc8-e79c-4ad7-a82f-47c62ec06d7d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del evaluador de expresiones CXX0045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no es una función  
  
 Se proporcionó una lista de argumentos para un símbolo del programa que no es el nombre de una función.  
  
## Ejemplo  
  
```  
queue( alpha, beta )  
```  
  
 donde `queue` no es una función.  
  
 Este error es idéntico a CAN00045.