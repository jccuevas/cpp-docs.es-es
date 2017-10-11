---
title: try, throw y catch instrucciones (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- catch_cpp
- try_cpp
- throw_cpp
dev_langs:
- C++
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
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 89db418a92239460379d1ea41d2d49a8073095c2
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="try-throw-and-catch-statements-c"></a>Instrucciones try, throw y catch (C++)
Para implementar el control de excepciones de C++, se usan expresiones `try`, `throw` y `catch`.  
  
 En primer lugar, se debe usar un bloque `try` para incluir una o más instrucciones que pueden iniciar una excepción.  
  
 Una expresión `throw` indica que se ha producido una condición excepcional, a menudo un error, en un bloque `try`. Se puede usar un objeto de cualquier tipo como operando de una expresión `throw`. Normalmente, este objeto se emplea para comunicar información sobre el error. En la mayoría de los casos, recomendamos que use la [std:: Exception](../standard-library/exception-class.md) clase o una de las clases derivadas que se definen en la biblioteca estándar. Si no es adecuado usar una de ellas, se recomienda derivar su propia clase de excepción de `std::exception`.  
  
 Para controlar las excepciones que se pueden producir, implemente uno o varios bloques `catch` inmediatamente después de un bloque `try`. Cada bloque `catch` especifica el tipo de excepción que puede controlar.  
  
 En este ejemplo se muestra un bloque `try` y sus controladores. Suponga que `GetNetworkResource()` adquiere datos a través de una conexión de red y que los dos tipos de excepción son clases definidas por el usuario que derivan de `std::exception`. Observe que las excepciones se detectan en la referencia `const` de la instrucción `catch`. Se recomienda producir excepciones por valor y detectarlas mediante la referencia const.  
  
## <a name="example"></a>Ejemplo  
  
```  
  
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
 El código después de la cláusula `try` es la sección de código protegida. El `throw` expresión *produce*: es decir, se genera: una excepción. El bloque de código que hay detrás de la cláusula `catch` es el controlador de excepciones. Este es el controlador que *detecta* la excepción que se produce si los tipos en el `throw` y `catch` expresiones son compatibles. Para obtener una lista de reglas que rigen la coincidencia de tipos en `catch` bloques, vea [se evalúan los bloques Catch cómo](../cpp/how-catch-blocks-are-evaluated-cpp.md). Si la instrucción `catch` especifica puntos suspensivos (...) en lugar de un tipo, el bloque `catch` controla todos los tipos de excepciones. Cuando se compila con la [/EHa](../build/reference/eh-exception-handling-model.md) opción, estos pueden incluir excepciones estructuradas de C y las excepciones asincrónicas generadas por el sistema o generados por la aplicación como infracciones de división por cero y de punto flotante de protección, de memoria . Puesto que los bloques `catch` se procesan por orden de programa para encontrar un tipo coincidente, un controlador de puntos suspensivos debe ser el último controlador del bloque `try` asociado. Use `catch(...)` con precaución; no permita que un programa continúe a menos que el bloque catch sepa controlar la excepción específica que se detecta. Normalmente, un bloque `catch(...)` se emplea para registrar errores y realizar limpiezas especiales antes de que se detenga la ejecución de un programa.  
  
 Una expresión `throw` sin operandos vuelve a iniciar la excepción que se controla actualmente. Se recomienda usar este formato al volver a iniciar la excepción, ya que esto conserva la información de tipo polimórfico de la excepción original. Una expresión así únicamente se debe usar en un controlador `catch` o en una función a la que se llama desde un controlador `catch`. El objeto de excepción que se vuelve a iniciar es el objeto de excepción original, no una copia.  
  
```  
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
 [Control de excepciones de C++](../cpp/cpp-exception-handling.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Excepciones de C++ no controladas](../cpp/unhandled-cpp-exceptions.md)   
 [__uncaught_exception](../c-runtime-library/reference/uncaught-exception.md)
