---
title: function (pragma)
ms.date: 08/29/2019
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: f99f3c878789a6c47fdb0d48e0a8690d65fa8062
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220139"
---
# <a name="function-pragma"></a>function (pragma)

Indica al compilador que genere llamadas a las funciones especificadas en la lista de argumentos de pragma, en lugar de alinearlas.

## <a name="syntax"></a>Sintaxis

> **función #pragma (** *function1* [ **,** *función2* ...] **)**

## <a name="remarks"></a>Comentarios

Las funciones intrínsecas se generan normalmente como código en línea, no como llamadas a función. Si usa la [pragma intrínseca](intrinsic.md) o la opción del compilador [/OI](../build/reference/oi-generate-intrinsic-functions.md) para indicar al compilador que genere funciones intrínsecas, puede usar la instrucción pragma **function** para forzar explícitamente una llamada de función. Una vez que se ve una instrucción pragma de **función** , se aplica a la primera definición de función que contiene una función intrínseca especificada. El efecto continúa hasta el final del archivo de código fuente o hasta la aparición de una `intrinsic` Directiva pragma que especifica la misma función intrínseca. Solo se puede usar la instrucción pragma **function** fuera de una función, en el nivel global.

Para obtener una lista de las funciones que tienen formas intrínsecas, vea [pragma Intrinsic](intrinsic.md).

## <a name="example"></a>Ejemplo

```cpp
// pragma_directive_function.cpp
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// use intrinsic forms of memset and strlen
#pragma intrinsic(memset, strlen)

// Find first word break in string, and set remaining
// chars in string to specified char value.
char *set_str_after_word(char *string, char ch) {
   int i;
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */

   for(i = 0; i < len; i++) {
      if (isspace(*(string + i)))
         break;
   }

   for(; i < len; i++)
      *(string + i) = ch;

   return string;
}

// do not use strlen intrinsic
#pragma function(strlen)

// Set all chars in string to specified char value.
char *set_str(char *string, char ch) {
   // Uses intrinsic for memset, but calls strlen library function
   return (char *) memset(string, ch, strlen(string));
}

int main() {
   char *str = (char *) malloc(20 * sizeof(char));

   strcpy_s(str, sizeof("Now is the time"), "Now is the time");
   printf("str is '%s'\n", set_str_after_word(str, '*'));
   printf("str is '%s'\n", set_str(str, '!'));
}
```

```Output
str is 'Now************'
str is '!!!!!!!!!!!!!!!'
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
