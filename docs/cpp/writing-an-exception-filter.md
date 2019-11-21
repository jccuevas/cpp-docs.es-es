---
title: Escribir un filtro de excepciones
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: aaf0dc77207399d7c6be86127d7decf03895ced5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245985"
---
# <a name="writing-an-exception-filter"></a>Escribir un filtro de excepciones

Para controlar una excepción puede saltar al nivel del controlador de la excepción o puede continuar la ejecución. Instead of using the exception handler code to handle the exception and falling through, you can use *filter* to clean up the problem and then, by returning -1, resume normal flow without clearing the stack.

> [!NOTE]
>  Algunas excepciones impiden que continúe el flujo. If *filter* evaluates to -1 for such an exception, the system raises a new exception. When you call [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception), you determine whether the exception will continue.

For example, the following code uses a function call in the *filter* expression: this function handles the problem and then returns -1 to resume normal flow of control:

```cpp
// exceptions_Writing_an_Exception_Filter.cpp
#include <windows.h>
int main() {
   int Eval_Exception( int );

   __try {}

   __except ( Eval_Exception( GetExceptionCode( ))) {
      ;
   }

}
void ResetVars( int ) {}
int Eval_Exception ( int n_except ) {
   if ( n_except != STATUS_INTEGER_OVERFLOW &&
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions
   return EXCEPTION_CONTINUE_SEARCH;

   // Execute some code to clean up problem
   ResetVars( 0 );   // initializes data to 0
   return EXCEPTION_CONTINUE_EXECUTION;
}
```

It is a good idea to use a function call in the *filter* expression whenever *filter* needs to do anything complex. La evaluación de la expresión hace que se ejecute la función (en este caso, `Eval_Exception`).

Note the use of [GetExceptionCode](/windows/win32/Debug/getexceptioncode) to determine the exception. Debe llamar a esta función dentro del propio filtro. `Eval_Exception` cannot call `GetExceptionCode`, but it must have the exception code passed to it.

Este controlador pasa el control a otro controlador a menos que la excepción sea un desbordamiento de números enteros o de punto flotante. En tal caso, el controlador llama a una función (`ResetVars` es solo un ejemplo, no una función API) para restablecer algunas variables globales. *Statement-block-2*, which in this example is empty, can never be executed because `Eval_Exception` never returns EXCEPTION_EXECUTE_HANDLER (1).

El uso de una llamada a una función es una buena técnica de uso general para trabajar con expresiones de filtro complejas. Otras dos características útiles del lenguaje C son:

- El operador condicional

- El operador de coma

El operador condicional es útil en muchas ocasiones, porque se puede utilizar para comprobar un código de retorno concreto y después devolver uno de dos valores diferentes. For example, the filter in the following code recognizes the exception only if the exception is STATUS_INTEGER_OVERFLOW:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

El propósito del operador condicional en este caso es principalmente proporcionar claridad, ya que el código siguiente genera los mismos resultados:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

The conditional operator is more useful in situations where you might want the filter to evaluate to -1, EXCEPTION_CONTINUE_EXECUTION.

El operador de coma permite realizar varias operaciones independientes en una sola expresión. El efecto es prácticamente el mismo que cuando se ejecutan varias instrucciones y después se devuelve el valor de la última expresión. Por ejemplo, el código siguiente almacena el código de excepción en una variable y después lo comprueba:

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>Vea también

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)