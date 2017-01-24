---
title: "Advertencia del compilador (nivel 4) C4701 | Microsoft Docs"
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
  - "C4701"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4701"
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4701
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Variable local potencialmente “nombre” sin utilizado  
  
 La variable local *name* puede haberse utilizado sin asignarle un valor.  Esto puede provocar resultados imprevisibles.  
  
## Ejemplo  
 El código siguiente genera C4701 y C4703.  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr) // C4701 and C4703  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
  **c:\\src\\test.cpp\(10\) : advertencia C4701: variable local potencialmente no inicializada “p” utilizada**  
 **c:\\src\\test.cpp\(10\) : advertencia C4703: variable de puntero local potencialmente no inicializada “p” utilizada** Para corregir esta advertencia, inicialice la variable como se muestra en este ejemplo:  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p = nullptr;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr)  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
## Vea también  
 [Advertencia del compilador \(nivel 4\) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)   
 [Las advertencias, \/sdl, y mejora desinicializaron detección variable](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)