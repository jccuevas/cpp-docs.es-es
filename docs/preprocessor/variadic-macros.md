---
title: Macros Variádicas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5918c7d91a3568799f361fcb42edb2e9c7b1445e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="variadic-macros"></a>Macros variádicas
Las macros variádicas son macros estilo funciones que contienen un número variable de argumentos.  
  
## <a name="remarks"></a>Comentarios  
 Para usar macros variádicas, se pueden especificar los puntos suspensivos como argumento formal final en una definición de macro y el identificador de reemplazo `__VA_ARGS__` puede utilizarse en la definición para insertar los argumentos adicionales.  `__VA_ARGS__` se reemplaza por todos los argumentos que coinciden con los puntos suspensivos, incluyendo comas entre ellos.  
  
 El estándar de C especifica que se debe pasar al menos un argumento a los puntos suspensivos para garantizar que la macro no se resuelva en una expresión con una coma final.  La implementación de Visual C++ suprimirá una coma final si no se pasa ningún argumento a los puntos suspensivos.  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="output"></a>Salida  
  
```  
here are some varargs1(1)  
here are some varargs2(4)  
here are some varargs3(5)  
hello, world  
error  
```  
  
## <a name="see-also"></a>Vea también  
 [Macros (C/C++)](../preprocessor/macros-c-cpp.md)