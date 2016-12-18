---
title: "Advertencia del compilador (nivel 4) C4703 | Microsoft Docs"
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
  - "C4703"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4703"
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4703
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Variable de puntero local potencialmente “nombre” sin utilizado  
  
 La variable de puntero local *name* puede haberse utilizado sin asignarle un valor.  Esto puede provocar resultados imprevisibles.  
  
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
 [Advertencia del compilador \(nivel 4\) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)   
 [Advertencias, \/sdl, y mejorar la detección variable no inicializada](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)