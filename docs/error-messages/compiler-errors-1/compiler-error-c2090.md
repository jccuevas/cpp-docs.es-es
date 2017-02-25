---
title: "Error del compilador C2090 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2090"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2090"
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2090
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la función devuelve una matriz  
  
 Una función no puede devolver una matriz.  En su lugar, deberá devolver un puntero a una matriz.  
  
 El código siguiente genera el error C2090:  
  
```  
// C2090.cpp  
int func1(void)[] {}   // C2090  
```  
  
 Posible solución:  
  
```  
// C2090b.cpp  
// compile with: /c  
int* func2(int * i) {  
   return i;  
}  
```