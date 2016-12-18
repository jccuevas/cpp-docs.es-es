---
title: "break (Instrucci&#243;n) (C) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "break"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "break (palabra clave) [C]"
ms.assetid: 015627c7-0924-49b2-a4d1-c77edf5eae6a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# break (Instrucci&#243;n) (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La instrucción `break` finaliza la ejecución de la instrucción `do`, `for`, `switch` o `while` más próxima que la incluya.  El control pasa a la instrucción que hay a continuación de la instrucción finalizada.  
  
## Sintaxis  
 *jump\-statement*:  
 `break;`  
  
 La instrucción `break` se usa con frecuencia para finalizar el procesamiento de un caso concreto en una instrucción `switch`.  Si no existe una instrucción iterativa o una instrucción `switch` incluyente, se genera un error.  
  
 Dentro de las instrucciones anidadas, la instrucción `break` finaliza solo la instrucción `do`, `for`, `switch` o `while` que la incluye de forma inmediata.  Puede usar una instrucción `return` o `goto` para transferir el control fuera de la estructura anidada.  
  
 En este ejemplo se ilustra la instrucción `break`:  
  
```  
#include <stdio.h>  
int main() {  
   char c;  
   for(;;) {  
      printf_s( "\nPress any key, Q to quit: " );  
  
      // Convert to character value  
      scanf_s("%c", &c);  
      if (c == 'Q')  
          break;  
   }  
} // Loop exits only when 'Q' is pressed  
```  
  
## Vea también  
 [break \(Instrucción\)](../cpp/break-statement-cpp.md)