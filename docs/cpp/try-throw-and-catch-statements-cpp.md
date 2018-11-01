---
title: Instrucciones try, throw y catch (C++)
ms.date: 11/04/2016
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
helpviewer_keywords:
- catch keyword [C++]
- keywords [C++], exception handling
- C++ exception handling, statement syntax
- try-catch keyword [C++], about try-catch exception handling
- throw keyword [C++]
- try-catch keyword [C++]
- try-catch keyword [C++], exception handling
- throwing exceptions [C++], throw keyword
- try-catch keyword [C++], throw keyword [C++]s
- throwing exceptions [C++], implementing C++ exception handling
- throwing exceptions [C++]
- throw keyword [C++], throw() vs. throw(...)
ms.assetid: 15e6a87b-b8a5-4032-a7ef-946c644ba12a
ms.openlocfilehash: 81d954b2e757c692bd80604a3f85ffb8c79c4f85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455736"
---
# <a name="try-throw-and-catch-statements-c"></a>Instrucciones try, throw y catch (C++)

Para implementar el control de excepciones en C++, debe utilizar **intente**, **throw**, y **catch** expresiones.

En primer lugar, use un **intente** bloque para incluir una o varias instrucciones que podrían producir una excepción.

Un **throw** expresión indica que una condición excepcional, a menudo, un error: se ha producido en un **intente** bloque. Puede usar un objeto de cualquier tipo como operando de un **throw** expresión. Normalmente, este objeto se emplea para comunicar información sobre el error. En la mayoría de los casos, recomendamos que use el [std:: Exception](../standard-library/exception-class.md) clase o una de las clases derivadas que se definen en la biblioteca estándar. Si no es adecuado usar una de ellas, se recomienda derivar su propia clase de excepción de `std::exception`.

Para controlar las excepciones que se pueden iniciar, implementar uno o varios **catch** bloques inmediatamente después de un **intente** bloque. Cada **catch** bloque especifica el tipo de excepción que puede controlar.

Este ejemplo se muestra un **intente** bloque y sus controladores. Suponga que `GetNetworkResource()` adquiere datos a través de una conexión de red y que los dos tipos de excepción son clases definidas por el usuario que derivan de `std::exception`. Tenga en cuenta que las excepciones se detectan mediante **const** hace referencia en el **catch** instrucción. Se recomienda producir excepciones por valor y detectarlas mediante la referencia const.

## <a name="example"></a>Ejemplo

```cpp
MyData md;
try {
   // Code that could throw an exception
   md = GetNetworkResource();
}
catch (const networkIOException& e) {
   // Code that executes when an exception of type
   // networkIOException is thrown in the try block
   // ...
   // Log error message in the exception object
   cerr << e.what();
}
catch (const myDataFormatException& e) {
   // Code that handles another exception type
   // ...
   cerr << e.what();
}

// The following syntax shows a throw expression
MyData GetNetworkResource()
{
   // ...
   if (IOSuccess == false)
      throw networkIOException("Unable to connect");
   // ...
   if (readError)
      throw myDataFormatException("Format error");
   // ...
}
```

## <a name="remarks"></a>Comentarios

El código después de la **intente** cláusula es la sección protegida de código. El **throw** expresión *produce*, es decir, se genera, una excepción. El bloque de código tras el **catch** cláusula es el controlador de excepciones. Este es el controlador que *detecta* la excepción que se produce si los tipos en el **throw** y **catch** expresiones son compatibles. Para obtener una lista de reglas que rigen la coincidencia de tipos en **catch** bloques, vea [se evalúan los bloques Catch cómo](../cpp/how-catch-blocks-are-evaluated-cpp.md). Si el **catch** instrucción especifica puntos suspensivos (...) en lugar de un tipo, el **catch** bloque controla todos los tipos de excepción. Cuando se compila con la [/EHa](../build/reference/eh-exception-handling-model.md) opción, estos pueden incluir excepciones estructuradas de C y las excepciones asincrónicas generadas por el sistema o generados por la aplicación, como las infracciones de división por cero y de punto flotante de protección, de memoria . Dado que **catch** bloques se procesan en orden de programa para encontrar un tipo coincidente, un controlador de botón de puntos suspensivos debe ser el último controlador asociado **intente** bloque. Use `catch(...)` con precaución; no permita que un programa continúe a menos que el bloque catch sepa controlar la excepción específica que se detecta. Normalmente, un bloque `catch(...)` se emplea para registrar errores y realizar limpiezas especiales antes de que se detenga la ejecución de un programa.

Un **throw** expresión que no tiene operandos vuelve a inicia la excepción se controla actualmente. Se recomienda usar este formato al volver a iniciar la excepción, ya que esto conserva la información de tipo polimórfico de la excepción original. Solo debe usarse como una expresión en un **catch** controlador o en una función que se llama desde un **catch** controlador. El objeto de excepción que se vuelve a iniciar es el objeto de excepción original, no una copia.

```cpp
try {
   throw CSomeOtherException();
}
catch(...) {
   // Catch all exceptions - dangerous!!!
   // Respond (perhaps only partially) to the exception, then
   // re-throw to pass the exception to some other handler
   // ...
   throw;
}
```

## <a name="see-also"></a>Vea también

[Control de excepciones de C++](../cpp/cpp-exception-handling.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Excepciones de C++ no controladas](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)