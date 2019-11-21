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

To implement exception handling in C++, you use **try**, **throw**, and **catch** expressions.

First, use a **try** block to enclose one or more statements that might throw an exception.

A **throw** expression signals that an exceptional condition—often, an error—has occurred in a **try** block. You can use an object of any type as the operand of a **throw** expression. Normalmente, este objeto se emplea para comunicar información sobre el error. In most cases, we recommend that you use the [std::exception](../standard-library/exception-class.md) class or one of the derived classes that are defined in the standard library. Si no es adecuado usar una de ellas, se recomienda derivar su propia clase de excepción de `std::exception`.

To handle exceptions that may be thrown, implement one or more **catch** blocks immediately following a **try** block. Each **catch** block specifies the type of exception it can handle.

This example shows a **try** block and its handlers. Suponga que `GetNetworkResource()` adquiere datos a través de una conexión de red y que los dos tipos de excepción son clases definidas por el usuario que derivan de `std::exception`. Notice that the exceptions are caught by **const** reference in the **catch** statement. Se recomienda producir excepciones por valor y detectarlas mediante la referencia const.

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

The code after the **try** clause is the guarded section of code. The **throw** expression *throws*—that is, raises—an exception. The code block after the **catch** clause is the exception handler. This is the handler that *catches* the exception that's thrown if the types in the **throw** and **catch** expressions are compatible. For a list of rules that govern type-matching in **catch** blocks, see [How Catch Blocks are Evaluated](../cpp/how-catch-blocks-are-evaluated-cpp.md). If the **catch** statement specifies an ellipsis (...) instead of a type, the **catch** block handles every type of exception. When you compile with the [/EHa](../build/reference/eh-exception-handling-model.md) option, these can include C structured exceptions and system-generated or application-generated asynchronous exceptions such as memory protection, divide-by-zero, and floating-point violations. Because **catch** blocks are processed in program order to find a matching type, an ellipsis handler must be the last handler for the associated **try** block. Use `catch(...)` con precaución; no permita que un programa continúe a menos que el bloque catch sepa controlar la excepción específica que se detecta. Normalmente, un bloque `catch(...)` se emplea para registrar errores y realizar limpiezas especiales antes de que se detenga la ejecución de un programa.

A **throw** expression that has no operand re-throws the exception currently being handled. Se recomienda usar este formato al volver a iniciar la excepción, ya que esto conserva la información de tipo polimórfico de la excepción original. Such an expression should only be used in a **catch** handler or in a function that's called from a **catch** handler. El objeto de excepción que se vuelve a iniciar es el objeto de excepción original, no una copia.

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

[Modern C++ best practices for exceptions and error handling](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Excepciones de C++ no controladas](../cpp/unhandled-cpp-exceptions.md)<br/>
[__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)