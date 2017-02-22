---
title: "pop_macro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.pop_macro"
  - "pop_macro_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pop_macro (pragma)"
  - "pragma (directivas), pop_macro"
ms.assetid: 3b5489d0-69ba-4c66-b572-2748af0f12bb
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# pop_macro
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Establece el valor de la macro *macro\_name* en el valor de la parte superior de la pila para esta macro.  
  
## Sintaxis  
  
```  
  
#pragma pop_macro("  
macro_name  
")  
  
```  
  
## Comentarios  
 Primero debe emitir [push\_macro](../preprocessor/push-macro.md) para *macro\_name* para poder usar **pop\_macro**.  
  
## Ejemplo  
  
```  
// pragma_directives_pop_macro.cpp  
// compile with: /W1  
#include <stdio.h>  
#define X 1  
#define Y 2  
  
int main() {  
   printf("%d",X);  
   printf("\n%d",Y);  
   #define Y 3   // C4005  
   #pragma push_macro("Y")  
   #pragma push_macro("X")  
   printf("\n%d",X);  
   #define X 2   // C4005  
   printf("\n%d",X);  
   #pragma pop_macro("X")  
   printf("\n%d",X);  
   #pragma pop_macro("Y")  
   printf("\n%d",Y);  
}  
```  
  
  **1**  
**2**  
**1**  
**2**  
**1**  
**3**   
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)