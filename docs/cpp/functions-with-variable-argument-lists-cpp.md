---
title: Listas de funciones con argumentos de Variable (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
ms.openlocfilehash: 1f366af6f4058ffb8356017d59a7c176a978b860
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637312"
---
# <a name="functions-with-variable-argument-lists--c"></a>Listas de funciones con argumentos de Variable (C++)

Las declaraciones de función en las que el último miembro son los puntos suspensivos (...) pueden tomar un número variable de argumentos. En estos casos, C++ proporciona comprobación de tipos solo para los argumentos declarados explícitamente. Puede utilizar listas de argumentos variables cuando necesite crear una función tan general que incluso el número y los tipos de argumentos puedan variar. La familia de funciones es un ejemplo de las funciones que usan listas de argumentos variables. `printf` *argument-declaration-list*

## <a name="functions-with-variable-arguments"></a>Funciones con argumentos variables

Para obtener acceso a los argumentos declarados en esas, use las macros incluidas en el archivo de inclusión estándar \<stdarg.h > como se describe a continuación.

**Específicos de Microsoft**

Microsoft C++ permite especificar los puntos suspensivos como argumento si son el último argumento y van precedidos por una coma. Por consiguiente, la declaración `int Func( int i, ... );` es válida, pero `int Func( int i ... );` no lo es.

**FIN de Específicos de Microsoft**

La declaración de una función que toma un número variable de argumentos requiere al menos un argumento de marcador de posición, incluso si no se utiliza. Si no se proporciona este argumento de marcador de posición, no existe ninguna forma de obtener acceso a los argumentos restantes.

Cuando los argumentos de tipo **char** se pasan como argumentos de variable, se convierten al tipo **int**. De forma similar, cuando los argumentos de tipo **float** se pasan como argumentos de variable, se convierten al tipo **doble**. Los argumentos de otros tipos están sujetos a las promociones habituales de entero y de punto flotante. Consulte [conversiones estándar](standard-conversions.md) para obtener más información.

Las funciones que requieren listas de variables se declaran con puntos suspensivos (...) en la lista de argumentos. Usar los tipos y macros que se describen en la \<stdarg.h > archivo de inclusión para el acceso a los argumentos que se pasan por una lista de variables. Para obtener más información sobre estas macros, vea [va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). en la documentación de la biblioteca en tiempo de ejecución de C.

El ejemplo siguiente muestra cómo funcionan las macros junto con el tipo (declarado en \<stdarg.h >):

```cpp
// variable_argument_lists.cpp
#include <stdio.h>
#include <stdarg.h>

//  Declaration, but not definition, of ShowVar.
void ShowVar( char *szTypes, ... );
int main() {
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );
}

//  ShowVar takes a format string of the form
//   "ifcs", where each character specifies the
//   type of the argument in that position.
//
//  i = int
//  f = float
//  c = char
//  s = string (char *)
//
//  Following the format specification is a variable
//  list of arguments. Each argument corresponds to
//  a format character in the format string to which
// the szTypes parameter points
void ShowVar( char *szTypes, ... ) {
   va_list vl;
   int i;

   //  szTypes is the last argument specified; you must access
   //  all others using the variable-argument macros.
   va_start( vl, szTypes );

   // Step through the list.
   for( i = 0; szTypes[i] != '\0'; ++i ) {
      union Printable_t {
         int     i;
         float   f;
         char    c;
         char   *s;
      } Printable;

      switch( szTypes[i] ) {   // Type to expect.
         case 'i':
            Printable.i = va_arg( vl, int );
            printf_s( "%i\n", Printable.i );
         break;

         case 'f':
             Printable.f = va_arg( vl, double );
             printf_s( "%f\n", Printable.f );
         break;

         case 'c':
             Printable.c = va_arg( vl, char );
             printf_s( "%c\n", Printable.c );
         break;

         case 's':
             Printable.s = va_arg( vl, char * );
             printf_s( "%s\n", Printable.s );
         break;

         default:
         break;
      }
   }
   va_end( vl );
}
//Output:
// 32.400002
// a
// Test string
```

En el ejemplo anterior se muestran estos conceptos importantes:

1. Debe establecer un marcador de lista como variable de tipo `va_list` antes de que se tenga acceso a cualquier argumento de variable. En el ejemplo anterior, el marcador se denomina `vl`.

1. Se accede a los argumentos individuales mediante la macro `va_arg`. Debe indicar a la macro `va_arg` el tipo de argumento que debe recuperar para poder transferir el número correcto de bytes desde la pila. Si especifica un tipo incorrecto de un tamaño diferente del proporcionado por el programa de llamada a `va_arg`, los resultados son imprevisibles.

1. Debe convertir explícitamente, mediante la macro `va_arg`, el resultado obtenido al tipo que desee.

Debe llamar a la macro para finalizar el procesamiento del argumento de variable.`va_end`