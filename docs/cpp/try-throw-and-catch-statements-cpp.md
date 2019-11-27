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
ms.openlocfilehash: 31ed5f7a17b9b45dbbecf5ccb29d2b51a7635eaa
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245140"
---
# <a name="try-throw-and-catch-statements-c"></a>Instrucciones try, throw y catch (C++)

Para implementar el control de C++excepciones en, se usan expresiones **try**, **Throw**y **catch** .

En primer lugar, use un bloque **try** para incluir una o varias instrucciones que puedan producir una excepción.

Una expresión **Throw** indica que se ha producido una condición excepcional (a menudo un error) en un bloque **try** . Puede usar un objeto de cualquier tipo como operando de una expresión **Throw** . Normalmente, este objeto se emplea para comunicar información sobre el error. En la mayoría de los casos, se recomienda usar la clase [STD:: Exception](../standard-library/exception-class.md) o una de las clases derivadas definidas en la biblioteca estándar. Si no es adecuado usar una de ellas, se recomienda derivar su propia clase de excepción de `std::exception`.

Para controlar las excepciones que se pueden producir, implemente uno o más bloques **catch** inmediatamente después de un bloque **try** . Cada bloque **catch** especifica el tipo de excepción que puede controlar.

En este ejemplo se muestra un bloque **try** y sus controladores. Suponga que `GetNetworkResource()` adquiere datos a través de una conexión de red y que los dos tipos de excepción son clases definidas por el usuario que derivan de `std::exception`. Observe que las excepciones se detectan mediante la referencia **const** en la instrucción **catch** . Se recomienda producir excepciones por valor y detectarlas mediante la referencia const.

## <a name="example"></a>Ejemplo

```cpp
MyData md;
try {
   // Code that could throw an exception
   md = GetNetworkResource();
}
catch (const networkIOException& e) {
   // Code that executes when an exception of type
   // networkIOException is thrown in the try block
   // ...
   // Log error message in the exception object
   cerr << e.what();
}
catch (const myDataFormatException& e) {
   // Code that handles another exception type
   // ...
   cerr << e.what();
}

// The following syntax shows a throw expression
MyData GetNetworkResource()
{
   // ...
   if (IOSuccess == false)
      throw networkIOException("Unable to connect");
   // ...
   if (readError)
      throw myDataFormatException("Format error");
   // ...
}
```

## <a name="remarks"></a>Comentarios

El código después de la cláusula **try** es la sección protegida del código. La expresión Throw *produce*, es decir, produce una excepción. El bloque de código después de la cláusula **catch** es el controlador de excepciones. Este es el controlador que *detecta* la excepción que se produce si los tipos de las expresiones **Throw** y **catch** son compatibles. Para obtener una lista de las reglas que rigen la coincidencia de tipos en los bloques **catch** , consulte [cómo se evalúan los bloques Catch](../cpp/how-catch-blocks-are-evaluated-cpp.md). Si la instrucción **catch** especifica puntos suspensivos (...) en lugar de un tipo, el bloque **catch** controla todos los tipos de excepciones. Al compilar con la opción [/EHA](../build/reference/eh-exception-handling-model.md) , se pueden incluir excepciones estructuradas de C y excepciones asincrónicas generadas por el sistema o generadas por la aplicación, como la protección de memoria, la división por cero y las infracciones de punto flotante. Dado que los bloques **catch** se procesan en el orden del programa para encontrar un tipo coincidente, un controlador de puntos suspensivos debe ser el último controlador del bloque **try** asociado. Use `catch(...)` con precaución; no permita que un programa continúe a menos que el bloque catch sepa controlar la excepción específica que se detecta. Normalmente, un bloque `catch(...)` se emplea para registrar errores y realizar limpiezas especiales antes de que se detenga la ejecución de un programa.

Una expresión **Throw** que no tiene ningún operando vuelve a iniciar la excepción que se está controlando actualmente. Se recomienda usar este formato al volver a iniciar la excepción, ya que esto conserva la información de tipo polimórfico de la excepción original. Este tipo de expresión solo se debe usar en un controlador **catch** o en una función a la que se llama desde un controlador **catch** . El objeto de excepción que se vuelve a iniciar es el objeto de excepción original, no una copia.

```cpp
try {
   throw CSomeOtherException();
}
catch(...) {
   // Catch all exceptions - dangerous!!!
   // Respond (perhaps only partially) to the exception, then
   // re-throw to pass the exception to some other handler
   // ...
   throw;
}
```

## <a name="see-also"></a>Vea también

[Prácticas C++ recomendadas modernas para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Excepciones de C++ no controladas](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)