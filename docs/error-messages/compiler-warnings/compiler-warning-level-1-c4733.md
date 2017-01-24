---
title: "Advertencia del compilador (nivel 1) C4733 | Microsoft Docs"
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
  - "C4733"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4733"
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4733
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Inline asm que asigna a 'FS:0' : el controlador no está registrado como controlador seguro  
  
 Es posible que una función que modifique el valor en FS:0 para agregar un nuevo controlador de excepciones no funcione con las excepciones seguras, porque puede que dicho controlador no esté registrado como controlador de excepciones válido \(vea [\/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)\).  
  
 Para corregir esta advertencia, quite la definición FS:0 o desactive esta advertencia y utilice [.SAFESEH](../../assembler/masm/dot-safeseh.md) para especificar los controladores de excepciones seguros.  
  
 El código siguiente genera el error C4733:  
  
```  
// C4733.cpp  
// compile with: /W1 /c  
// processor: x86  
#include "stdlib.h"  
#include "stdio.h"  
void my_handler()  
{  
   printf("Hello from my_handler\n");  
   exit(1);  
}  
  
int main()  
{  
   _asm {  
      push    my_handler  
      mov     eax, DWORD PTR fs:0  
      push    eax  
      mov     DWORD PTR fs:0, esp   // C4733  
   }  
  
   *(int*)0 = 0;  
}  
```