---
title: 'Tutorial: Implementar futuros'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 2b9d889dac195bb60651cbb76110d54b6231a5fd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141975"
---
# <a name="walkthrough-implementing-futures"></a>Tutorial: Implementar futuros

En este tema se muestra cómo implementar futuros en la aplicación. En el tema se muestra cómo combinar la funcionalidad existente en el Runtime de simultaneidad para conseguir algo que hace más.

> [!IMPORTANT]
> En este tema se muestra el concepto de futuros para fines de demostración. Le recomendamos que use [STD:: Future](../../standard-library/future-class.md) o [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) cuando necesite una tarea asincrónica que calcule un valor para su uso posterior.

Una *tarea* es un cálculo que se puede descomponer en cálculos adicionales y más específicos. Un *futuro* es una tarea asincrónica que calcula un valor para su uso posterior.

Para implementar futuros, este tema define la clase `async_future`. La clase `async_future` usa estos componentes de la Runtime de simultaneidad: la clase [Concurrency:: task_group](reference/task-group-class.md) y la clase [Concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) . La clase `async_future` utiliza la clase `task_group` para calcular un valor de forma asincrónica y la clase `single_assignment` para almacenar el resultado del cálculo. El constructor de la clase `async_future` toma una función de trabajo que calcula el resultado, y el método `get` recupera el resultado.

### <a name="to-implement-the-async_future-class"></a>Para implementar la clase async_future

1. Declare una clase de plantilla con el nombre `async_future` que se parametrice en el tipo del cálculo resultante. Agregue secciones `public` y `private` a esta clase.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. En la sección `private` de la clase `async_future`, declare miembros de datos `task_group` y `single_assignment`.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. En la sección `public` de la clase `async_future`, implemente el constructor. El constructor es una plantilla que se parametriza en la función de trabajo que calcula el resultado. El constructor ejecuta de forma asincrónica la función de trabajo en el miembro de datos `task_group` y usa la función [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) para escribir el resultado en el miembro de datos `single_assignment`.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. En la sección `public` de la clase `async_future`, implemente el destructor. El destructor espera hasta que finaliza la tarea.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. En la sección `public` de la clase `async_future`, implemente el método `get`. Este método usa la función [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) para recuperar el resultado de la función de trabajo.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Ejemplo

### <a name="description"></a>Descripción

En el siguiente ejemplo se muestran la clase `async_future` completa y un ejemplo de su uso. La función `wmain` crea un objeto STD::[Vector](../../standard-library/vector-class.md) que contiene 10.000 valores enteros aleatorios. A continuación, utiliza objetos `async_future` para encontrar los valores mayor y menor incluidos en el objeto `vector`.

### <a name="code"></a>Código

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Comentarios

En este ejemplo se produce la siguiente salida:

```Output
smallest: 0
largest:  9999
average:  4981
```

En el ejemplo se usa el método `async_future::get` para recuperar los resultado del cálculo. El método `async_future::get` espera hasta que finaliza el cálculo si este está todavía activo.

## <a name="robust-programming"></a>Programación sólida

Para extender la clase `async_future` para controlar las excepciones producidas por la función de trabajo, modifique el método `async_future::get` para llamar al método [Concurrency:: task_group:: wait](reference/task-group-class.md#wait) . El método `task_group::wait` inicia las excepciones que genera la función de trabajo.

En el ejemplo siguiente se muestra la versión modificada de la clase `async_future`: La función `wmain` utiliza una `try`-bloque `catch` para imprimir el resultado del objeto `async_future` o para imprimir el valor de la excepción generada por la función de trabajo.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
caught exception: error
```

Para obtener más información sobre el modelo de control de excepciones en el Runtime de simultaneidad, vea [control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `futures.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl. exe/EHsc Futures. cpp**

## <a name="see-also"></a>Consulte también

[Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[task_group (clase)](reference/task-group-class.md)<br/>
[single_assignment (clase)](../../parallel/concrt/reference/single-assignment-class.md)
