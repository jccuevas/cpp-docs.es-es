---
title: Objetos temporales
ms.date: 11/04/2016
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
ms.openlocfilehash: b298872a688c3b8e383a04ea4d82753859cbb2e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160754"
---
# <a name="temporary-objects"></a>Objetos temporales

En algunos casos, es necesario que el compilador cree objetos temporales. Estos objetos temporales se pueden crear por las razones siguientes:

- Para inicializar una referencia **const** con un inicializador de un tipo diferente del tipo subyacente de la referencia que se está inicializando.

- Para almacenar el valor devuelto de una función que devuelve un tipo definido por el usuario. Estos objetos temporales solo se crean si el programa no copia el valor devuelto en un objeto. Por ejemplo:

    ```cpp
    UDT Func1();    //  Declare a function that returns a user-defined
                    //   type.

    ...

    Func1();        //  Call Func1, but discard return value.
                    //  A temporary object is created to store the return
                    //   value.
    ```

   Como el valor devuelto no se copia en otro objeto, se crea un objeto temporal. Un caso más común de creación de objetos temporales es durante la evaluación de una expresión en la que deben llamarse a funciones de operador sobrecargadas. Estas funciones de operador sobrecargadas devuelven un tipo definido por el usuario que normalmente no se copia a otro objeto.

   Considere la expresión `ComplexResult = Complex1 + Complex2 + Complex3`. La expresión `Complex1 + Complex2` se evalúa y el resultado se almacena en un objeto temporal. A continuación, se evalúa la expresión *temporal* `+ Complex3` y el resultado se copia en `ComplexResult` (suponiendo que el operador de asignación no esté sobrecargado).

- Para almacenar el resultado de una conversión en un tipo definido por el usuario. Cuando un objeto de un tipo determinado se convierte explícitamente en un tipo definido por el usuario, este nuevo objeto se crea como un objeto temporal.

Los objetos temporales tienen una duración que viene definida por su punto de creación y por el punto en el que se destruyen. Cualquier expresión que cree más de un objeto temporal los acabará destruyendo en el orden inverso en que se crearon. Los puntos en los que se produce la destrucción se muestran en la tabla siguiente.

### <a name="destruction-points-for-temporary-objects"></a>Puntos de destrucción de objetos temporales

|Motivo por el que se creó el objeto temporal|Punto de destrucción|
|------------------------------|-----------------------|
|Resultado de evaluación de la expresión|Todos los objetos temporales creados como resultado de la evaluación de expresiones se destruyen al final de la instrucción de expresión (es decir, en el punto y coma) o al final de las expresiones de control para las instrucciones **for**, **If**, **While**, **do**y **Switch** .|
|Inicializar referencias **const**|Si un inicializador no es un valor L del mismo tipo que la referencia que se va a inicializar, se crea un objeto temporal del tipo de objeto subyacente y se inicializa con la expresión de inicialización. Este objeto temporal se destruye inmediatamente después de que se destruya el objeto de referencia al que está enlazado.|
