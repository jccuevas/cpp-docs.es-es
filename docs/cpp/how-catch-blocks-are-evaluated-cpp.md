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
ms.openlocfilehash: 7504439c565d4dfb720bc2fa7e097e3230733423
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153689"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Cómo se evalúan los bloques catch (C++)

C++ permite iniciar excepciones de cualquier tipo, aunque en general se recomienda iniciar tipos derivados de std::exception. Se puede detectar una excepción de C++ mediante un **catch** controlador que especifica el mismo tipo que la excepción, o mediante un controlador que puede detectar cualquier tipo de excepción.

Si el tipo de excepción que se inicia es una clase, que también tiene una o varias clases base, se puede detectar mediante los controladores que aceptan las clases base del tipo de la excepción, así como referencias a las bases del tipo de la excepción. Observe que, cuando una referencia detecta una excepción, está enlazada al objeto de excepción real que se ha iniciado; si no, es una copia (igual que un argumento de una función).

Cuando se produce una excepción, se puede detectar mediante los siguientes tipos de **catch** controladores:

- Un controlador que pueda aceptar cualquier tipo (mediante la sintaxis de puntos suspensivos).

- Un controlador que acepte el mismo tipo que el objeto de excepción; Dado que es una copia, **const** y **volátil** se omiten los modificadores.

- Un controlador que acepte una referencia al mismo tipo que el objeto de excepción.

- Un controlador que acepte una referencia a un **const** o **volátil** formulario del mismo tipo que el objeto de excepción.

- Un controlador que acepte una clase base del mismo tipo que el objeto de excepción; Puesto que es una copia, **const** y **volátil** se omiten los modificadores. El **catch** controlador para una clase base no debe preceder el **catch** controlador para la clase derivada.

- Un controlador que acepte una referencia a una clase base del mismo tipo que el objeto de excepción.

- Un controlador que acepte una referencia a un **const** o **volátil** forma de una clase base del mismo tipo que el objeto de excepción.

- Un controlador que acepte un puntero al que pueda convertirse un objeto de puntero iniciado mediante las reglas de conversión de puntero estándar.

El orden en que **catch** controladores aparecen es importante, porque los controladores para una determinada **intente** bloque se examinan por orden de aparición. Por ejemplo, es un error colocar el controlador para una clase base antes del controlador para una clase derivada. Después de una coincidencia **catch** se encuentra el controlador, no se examinan los controladores subsiguientes. Como resultado, los puntos suspensivos **catch** controlador debe ser el último controlador su **intente** bloque. Por ejemplo:

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

En este ejemplo, los puntos suspensivos **catch** controlador es el único controlador que se examina.

## <a name="see-also"></a>Vea también

[Control de excepciones de C++](../cpp/cpp-exception-handling.md)