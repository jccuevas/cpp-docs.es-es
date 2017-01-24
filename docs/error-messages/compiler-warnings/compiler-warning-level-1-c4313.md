---
title: "Advertencia del compilador (nivel 1) C4313 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4313"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4313"
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4313
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': 'format specifier' en cadena de formato entra en conflicto con el número de argumento de tipo 'type'  
  
 Hay un conflicto entre el formato especificado y el valor que está pasando.  Por ejemplo, ha pasado un parámetro de 64 bits a un especificador de formato %d sin calificar, que espera un parámetro de entero de 32 bits.  Esta advertencia solo tiene efecto cuando el código se compila para destinos de 64 bits.  
  
## Ejemplo  
 El ejemplo de código siguiente genera el error C4313 cuando se compila para un destino de 64 bits.  
  
```  
// C4313.cpp  
// Compile by using: cl /W1 C4313.cpp  
#include <stdio.h>  
int main() {  
   int * pI = 0;  
   printf("%d", pI);   // C4313 on 64-bit platform code  
   // Try one of the following lines instead:  
   // printf("%p\n", pI);  
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information  
}  
```