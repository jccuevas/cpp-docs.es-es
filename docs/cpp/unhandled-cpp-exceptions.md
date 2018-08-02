---
title: Las excepciones de C++ no controladas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- event handlers [C++], unhandled exceptions
- catch keyword [C++], handler not found
- exceptions [C++], unhandled
- C++ exception handling, unhandled exceptions
- unhandled exceptions [C++]
ms.assetid: 13f09c53-9254-4407-9db9-14e730e047cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e2162034b3e9ff93ebccca0f7eb53299b19c648
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467983"
---
# <a name="unhandled-c-exceptions"></a>Excepciones de C++ no controladas
Si un controlador coincidente (o botón de puntos suspensivos **catch** controlador) no se encuentra para la excepción actual, predefinida `terminate` se llama a la función de tiempo de ejecución. (También puede llamar explícitamente a `terminate` en cualquiera de sus controladores). La acción predeterminada de `terminate` es llamar a `abort`. Si desea que `terminate` llame a otra función del programa antes de salir de la aplicación, llame a la función `set_terminate` con el nombre de la función que se va a llamar como argumento único. Puede llamar a `set_terminate` en cualquier punto del programa. El `terminate` rutina siempre llama a la última función especificada como argumento a `set_terminate`.  
  
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
  
## <a name="output"></a>Salida  
  
```Output  
term_func was called by terminate.  
```  
  
 La función `term_func` debe finalizar el programa o el subproceso actual, idealmente mediante una llamada a `exit`. Si no lo hace y, en su lugar, regresa a su llamador, se llama a `abort`.  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones de C++](../cpp/cpp-exception-handling.md)