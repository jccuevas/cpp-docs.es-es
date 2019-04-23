---
title: function (C/C++)
ms.date: 11/04/2016
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: c57ff2053b3c1fd52474c7eb0dd598641632f789
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027264"
---
# <a name="function-cc"></a>function (C/C++)
Especifica que se generen llamadas a funciones especificadas en la lista de argumentos de pragma.

## <a name="syntax"></a>Sintaxis

```
#pragma function( function1 [, function2, ...] )
```

## <a name="remarks"></a>Comentarios

Si usas el `intrinsic` pragma (u /Oi) para indicar al compilador que genere funciones intrínsecas (funciones intrínsecas se generan como código en línea, no como llamadas a funciones), puede usar el **función** pragma para forzar explícitamente una llamada de función. Una vez vista una directiva pragma function, se aplica a la primera definición de función que contenga una función intrínseca especificada. El efecto continúa hasta el final del archivo de origen o a la apariencia de un `intrinsic` pragma especificando la misma función intrínseca. El **función** pragma puede utilizarse solo fuera de una función, en el nivel global.

Para obtener listas de las funciones que tienen formas intrínsecas, vea [intrínseco #pragma](../preprocessor/intrinsic.md).

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

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)