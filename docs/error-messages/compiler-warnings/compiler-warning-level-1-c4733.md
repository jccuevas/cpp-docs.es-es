---
title: Compilador advertencia (nivel 1) C4733 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4733
dev_langs:
- C++
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 480092a003c90164157f29d2445029a31387a225
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4733"></a>Advertencia del compilador (nivel 1) C4733
Inline asm que asigna a 'FS: 0': controlador no está registrado como controlador seguro  
  
 Una función que modifique el valor en FS: 0 para agregar un nuevo controlador de excepción no funcionen con las excepciones seguras, porque no se puede registrar el controlador como un controlador de excepciones válido (vea [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).  
  
 Para resolver esta advertencia, quite la definición FS: 0 o desactivar esta advertencia y usar [. SAFESEH](../../assembler/masm/dot-safeseh.md) para especificar los controladores de excepciones seguros.  
  
 El ejemplo siguiente genera C4733:  
  
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