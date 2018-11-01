---
title: 'Cómo: Usar la clase Context para implementar un semáforo cooperativo'
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: 460a1de03f34cb8ef9753e761aaef37470cd6d0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467773"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Cómo: Usar la clase Context para implementar un semáforo cooperativo

En este tema se muestra cómo usar la clase Concurrency:: Context para implementar una clase de semáforo cooperativa.

La clase `Context` permite bloquear o ceder el contexto de ejecución actual. Bloquear o ceder el contexto actual es útil cuando el contexto actual no puede continuar porque un recurso no está disponible. Un *semáforo* es un ejemplo de una situación donde el contexto de ejecución actual debe esperar para que esté disponible un recurso. Un semáforo, como un objeto de sección crítica, es un objeto de sincronización que permite que el código en un contexto tenga acceso exclusivo a un recurso. Sin embargo, a diferencia de lo que sucede con un objeto de sección crítica, un semáforo permite que varios contextos tengan acceso al recurso a la vez. Si existe un bloqueo de semáforo para un número máximo de contextos, cada contexto adicional debe esperar a que el otro contexto libere el bloqueo.

### <a name="to-implement-the-semaphore-class"></a>Para implementar la clase de semáforo

1. Declare una clase que se denomine `semaphore`. Agregue secciones `public` y `private` a esta clase.

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. En el `private` sección de la `semaphore` clase, declare un [std:: atomic](../../standard-library/atomic-structure.md) variable que contiene el recuento del semáforo y un [Concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) objeto que contiene los contextos que debe esperar para adquirir el semáforo.

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. En la sección `public` de la clase `semaphore`, implemente el constructor. El constructor toma un valor `long long` que especifica el número máximo de contextos que pueden mantener el bloqueo al mismo tiempo.

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. En la sección `public` de la clase `semaphore`, implemente el método `acquire`. Este método disminuye el recuento del semáforo como una operación atómica. Si el recuento del semáforo es negativo, agregue el contexto actual al final de la cola de espera y llame a la [Concurrency](reference/context-class.md#block) para bloquear el contexto actual.

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. En la sección `public` de la clase `semaphore`, implemente el método `release`. Este método aumenta el recuento del semáforo como una operación atómica. Si el recuento del semáforo es negativo antes de la operación de incremento, hay por lo menos un contexto que está esperando por el bloqueo. En ese caso, desbloquee el contexto que está al principio de la cola de espera.

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>Ejemplo

La clase `semaphore` de este ejemplo se comporta de manera cooperativa, porque los métodos `Context::Block` y `Context::Yield` ceden la ejecución de modo que el runtime pueda realizar otras tareas.

El método `acquire` disminuye el contador, pero es posible que no termine de agregar el contexto a la cola de espera antes de que otro contexto llame al método `release`. Para tener en cuenta esto, el `release` método usa un bucle de giro que llama a la [Concurrency](reference/context-class.md#yield) método para esperar a la `acquire` método para terminar de agregar el contexto.

El método `release` puede llamar a `Context::Unblock` antes de que el método `acquire` llame a `Context::Block`. No es necesario evitar esta condición de carrera porque el runtime permite llamar a estos métodos en cualquier orden. Si el método `release` llama a `Context::Unblock` antes de que el método `acquire` llame a `Context::Block` para el mismo contexto, ese contexto permanece desbloqueado. El runtime sólo requiere que cada llamada a `Context::Block` se corresponda con la respectiva llamada a `Context::Unblock`.

En el ejemplo siguiente se muestra la clase `semaphore` completa: La función `wmain` muestra el uso básico de esta clase. El `wmain` función usa el [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo para crear varias tareas que requieren acceso al semáforo. Dado que puede haber tres subprocesos que mantengan el bloqueo en un momento dado, algunas tareas deben esperar a que otra tarea finalice y libere el bloqueo.

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

Este ejemplo genera la siguiente salida de ejemplo.

```Output
In loop iteration 5...
In loop iteration 0...
In loop iteration 6...
In loop iteration 1...
In loop iteration 2...
In loop iteration 7...
In loop iteration 3...
In loop iteration 8...
In loop iteration 9...
In loop iteration 4...
```

Para obtener más información sobre la `concurrent_queue` de clases, vea [contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md). Para obtener más información sobre la `parallel_for` algoritmo, vea [algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `cooperative-semaphore.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc cooperative-semaphore.cpp**

## <a name="robust-programming"></a>Programación sólida

Puede usar el *Resource Acquisition Is Initialization* patrón (RAII) para limitar el acceso a un `semaphore` objeto a un ámbito determinado. Bajo el modelo RAII, se asigna una estructura de datos en la pila. Esa estructura de datos se inicializa o adquiere un recurso cuando se crea, y destruye o libera ese recurso cuando se destruye la estructura de datos. El modelo RAII garantiza que se llama al destructor antes de que el ámbito de inclusión salga. Por consiguiente, se administra el recurso correctamente cuando se produce una excepción o cuando una función contiene varias instrucciones `return`.

En el siguiente ejemplo se define una clase denominada `scoped_lock`, que se define en la sección `public` de la clase `semaphore`. El `scoped_lock` es similar a la [concurrency::critical_section::scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) y [concurrency::reader_writer_lock::scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) clases. El constructor de la clase `semaphore::scoped_lock` adquiere el acceso al objeto `semaphore` en cuestión y el destructor libera el acceso a ese objeto.

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
En el ejemplo siguiente se modifica el cuerpo de la función de trabajo que se pasa al algoritmo `parallel_for` para que use RAII con el fin de garantizar que el semáforo se libere antes de que regrese la función. Esta técnica garantiza que la función de trabajo es segura ante excepciones.

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>Vea también

[Contextos](../../parallel/concrt/contexts.md)<br/>
[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)

