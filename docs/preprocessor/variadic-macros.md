---
title: "Macros vari&#225;dicas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros variádicas [C++]"
  - "__VA_ARGS__ (especificador de macro variádica)"
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Macros vari&#225;dicas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las macros variádicas son macros estilo funciones que contienen un número variable de argumentos.  
  
## Comentarios  
 Para utilizar macros variádicas, los puntos suspensivos se pueden especificar como el último argumento formal de una definición de macro y el identificador de reemplazo `__VA_ARGS__` se puede utilizar en la definición para insertar los argumentos adicionales. `__VA_ARGS__` se reemplaza por todos los argumentos que coinciden con los puntos suspensivos, incluidas las comas entre ellos.  
  
 El estándar de C especifica que se debe pasar al menos un argumento a los puntos suspensivos para garantizar que la macro no se resuelva en una expresión con una coma final.  La implementación de Visual C\+\+ suprimirá una coma final si no se pasa ningún argumento a los puntos suspensivos.  
  
## Ejemplo  
  
```cpp  
// variadic_macros.cpp  
#include <stdio.h>  
#define EMPTY  
  
#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }  
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }  
#define CHECK3(...) { printf(__VA_ARGS__); }  
#define MACRO(s, ...) printf(s, __VA_ARGS__)  
  
int main() {  
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");  
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print  
  
    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print  
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");  
  
    // always invokes printf in the macro  
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");  
  
    MACRO("hello, world\n");  
  
    MACRO("error\n", EMPTY); // would cause error C2059, except VC++   
                             // suppresses the trailing comma  
}  
```  
  
## Output  
  
```  
here are some varargs1(1)  
here are some varargs2(4)  
here are some varargs3(5)  
hello, world  
error  
  
```  
  
## Vea también  
 [Macros](../preprocessor/macros-c-cpp.md)