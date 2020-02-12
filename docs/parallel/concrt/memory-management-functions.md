---
title: Funciones de administración de memoria
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: aa1951211283ddf7e4823a920d5cdf19bd6d977d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141836"
---
# <a name="memory-management-functions"></a>Funciones de administración de memoria

En este documento se describen las funciones de administración de memoria que proporciona el Runtime de simultaneidad para ayudarle a asignar y liberar memoria de manera simultánea.

> [!TIP]
> Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el Programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, se recomienda empezar con la biblioteca de [patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no está familiarizado con la Runtime de simultaneidad.

El Runtime de simultaneidad proporciona dos funciones de administración de memoria que se optimizan para asignar y liberar bloques de memoria de manera simultánea. La función [Concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) asigna un bloque de memoria con el tamaño especificado. La función [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) libera la memoria asignada por `Alloc`.

> [!NOTE]
> Las funciones `Alloc` y `Free` se basan entre sí. Utilice la función `Free` solo para liberar la memoria asignada mediante la función `Alloc`. Además, cuando utilice la función `Alloc` para asignar memoria, use solo la función `Free` para liberar esa memoria.

Use las funciones `Alloc` y `Free` al asignar y liberar un conjunto fijo de tamaños de asignación de diferentes subprocesos o tareas. El Runtime de simultaneidad almacena en memoria caché la memoria que asigna del montón en tiempo de ejecución de C. El Runtime de simultaneidad contiene una memoria caché de memoria independiente para cada subproceso en ejecución; por lo tanto, el Runtime administra la memoria sin el uso de bloqueos ni barreras de memoria. Una aplicación se beneficia más de las funciones `Alloc` y `Free` cuando se tiene acceso a la memoria caché con más frecuencia. Por ejemplo, un subproceso que llama con frecuencia a `Alloc` y `Free` ventajas más que un subproceso que principalmente llama a `Alloc` o `Free`.

> [!NOTE]
> Cuando se usan estas funciones de administración de memoria y la aplicación utiliza una gran cantidad de memoria, la aplicación puede escribir una condición de memoria insuficiente antes de lo esperado. Dado que los bloques de memoria almacenados en memoria caché por un subproceso no están disponibles para ningún otro subproceso, si un subproceso contiene una gran cantidad de memoria, esa memoria no estará disponible.

## <a name="example"></a>Ejemplo

Para obtener un ejemplo que usa las funciones `Alloc` y `Free` para mejorar el rendimiento de la memoria, consulte [Cómo: usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

## <a name="see-also"></a>Consulte también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Procedimiento para usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
