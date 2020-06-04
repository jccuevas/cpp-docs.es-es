---
title: Excepciones de C++ no controladas
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
ms.openlocfilehash: f42a4e2af46ab7690d6f4bc9641c09f3757eb6b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160559"
---
# <a name="unhandled-c-exceptions"></a>Excepciones de C++ no controladas

Si no se encuentra un controlador coincidente (o un controlador **catch** de puntos suspensivos) para la excepción actual, se llama a la función predefinida `terminate` en tiempo de ejecución. (También puede llamar a `terminate` explícitamente en cualquiera de los controladores). La acción predeterminada de `terminate` es llamar a `abort`. Si desea que `terminate` llame a otra función del programa antes de salir de la aplicación, llame a la función `set_terminate` con el nombre de la función que se va a llamar como argumento único. Puede llamar a `set_terminate` en cualquier punto del programa. La rutina `terminate` siempre llama a la última función especificada como argumento para `set_terminate`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se inicia una excepción `char *`, pero no contiene un controlador designado para detectar excepciones de tipo `char *`. La llamada a `set_terminate` indica a `terminate` que llame a `term_func`.

```cpp
// exceptions_Unhandled_Exceptions.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
void term_func() {
   cout << "term_func was called by terminate." << endl;
   exit( -1 );
}
int main() {
   try
   {
      set_terminate( term_func );
      throw "Out of memory!"; // No catch handler for this exception
   }
   catch( int )
   {
      cout << "Integer exception raised." << endl;
   }
   return 0;
}
```

## <a name="output"></a>Output

```Output
term_func was called by terminate.
```

La función `term_func` debe finalizar el programa o el subproceso actual, idealmente mediante una llamada a `exit`. Si no lo hace y, en su lugar, regresa a su llamador, se llama a `abort`.

## <a name="see-also"></a>Consulte también

[Prácticas C++ recomendadas modernas para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md)
