---
title: "Error del compilador C2710 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2710"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2710"
ms.assetid: a2a6bb5b-86ad-4a6c-acd0-e2bef8464e0e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2710
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'construcción' : '\_\_declspec \(modificador\)' solamente se puede aplicar a una función que devuelve un puntero  
  
 Una función cuyo valor devuelto es un puntero es la única construcción a la que se puede aplicar `modifier`.  
  
 El código siguiente genera el error C2710:  
  
```  
// C2710.cpp  
__declspec(restrict) void f();   // C2710  
// try the following line instead  
__declspec(restrict) int * g();  
```