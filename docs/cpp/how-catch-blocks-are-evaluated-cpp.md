---
title: Cómo se evalúan los bloques catch (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: 027dc87923a588ea891dbf6dd835e2baba75a1cb
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245858"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Cómo se evalúan los bloques catch (C++)

C++ permite iniciar excepciones de cualquier tipo, aunque en general se recomienda iniciar tipos derivados de std::exception. Una C++ excepción puede ser detectada por un controlador **catch** que especifique el mismo tipo que la excepción iniciada, o por un controlador que pueda detectar cualquier tipo de excepción.

Si el tipo de excepción que se inicia es una clase, que también tiene una o varias clases base, se puede detectar mediante los controladores que aceptan las clases base del tipo de la excepción, así como referencias a las bases del tipo de la excepción. Observe que, cuando una referencia detecta una excepción, está enlazada al objeto de excepción real que se ha iniciado; si no, es una copia (igual que un argumento de una función).

Cuando se produce una excepción, puede ser detectada por los siguientes tipos de controladores **catch** :

- Un controlador que pueda aceptar cualquier tipo (mediante la sintaxis de puntos suspensivos).

- Un controlador que acepta el mismo tipo que el objeto de excepción; Dado que es una copia, se omiten los modificadores **const** y **volatile** .

- Un controlador que acepte una referencia al mismo tipo que el objeto de excepción.

- Un controlador que acepta una referencia a una forma **const** o **volátil** del mismo tipo que el objeto de excepción.

- Un controlador que acepta una clase base del mismo tipo que el objeto de excepción; Dado que es una copia, se omiten los modificadores **const** y **volatile** . El controlador **catch** de una clase base no debe preceder al controlador **catch** de la clase derivada.

- Un controlador que acepte una referencia a una clase base del mismo tipo que el objeto de excepción.

- Un controlador que acepta una referencia a una forma **const** o **volátil** de una clase base del mismo tipo que el objeto de excepción.

- Un controlador que acepte un puntero al que pueda convertirse un objeto de puntero iniciado mediante las reglas de conversión de puntero estándar.

El orden en que aparecen los controladores **catch** es significativo, ya que los controladores de un bloque **try** determinado se examinan en orden de aparición. Por ejemplo, es un error colocar el controlador para una clase base antes del controlador para una clase derivada. Después de encontrar un controlador **catch** coincidente, no se examinan los controladores subsiguientes. Como resultado, un controlador **catch** de puntos suspensivos debe ser el último controlador del bloque **try** . Por ejemplo:

```cpp
// ...
try
{
    // ...
}
catch( ... )
{
    // Handle exception here.
}
// Error: the next two handlers are never examined.
catch( const char * str )
{
    cout << "Caught exception: " << str << endl;
}
catch( CExcptClass E )
{
    // Handle CExcptClass exception here.
}
```

En este ejemplo, el controlador **catch** de puntos suspensivos es el único controlador que se examina.

## <a name="see-also"></a>Vea también

[Prácticas C++ recomendadas modernas para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md)