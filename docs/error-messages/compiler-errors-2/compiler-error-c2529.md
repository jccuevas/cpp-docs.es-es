---
title: "Error del compilador C2529 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2529"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2529"
ms.assetid: 73a99e55-b91e-488d-9b72-cc80faaeb436
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2529
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre' : la referencia a la referencia no es válida  
  
 Este error se puede corregir mediante la sintaxis de puntero y declarando una referencia a un puntero.  
  
 El código siguiente genera el error C2529:  
  
```  
// C2529.cpp  
// compile with: /c  
int i;  
int &ri = i;  
int &(&rri) = ri;   // C2529  
```