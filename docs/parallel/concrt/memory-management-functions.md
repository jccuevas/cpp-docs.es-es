---
title: Funciones de administración de memoria | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bfbef45593a95cb8b317e7585119a6afbffd7a4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423616"
---
# <a name="memory-management-functions"></a>Funciones de administración de memoria

Este documento describe las funciones de administración de memoria que el Runtime de simultaneidad proporciona para ayudarle a asignar y liberar memoria de manera simultánea.

> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas le ayuda a ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si es nuevo en el Runtime de simultaneidad.

El Runtime de simultaneidad proporciona dos funciones de administración de memoria que se optimizan para asignar y liberar bloques de memoria de manera simultánea. El [Concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) función asigna un bloque de memoria con el tamaño especificado. El [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) función libera la memoria asignada por `Alloc`.

> [!NOTE]
>  El `Alloc` y `Free` funciones dependen entre sí. Use la `Free` función solo para liberar memoria que se asigna utilizando el `Alloc` función. Además, cuando usa el `Alloc` función para asignar memoria, use solo la `Free` función liberar esa memoria.

Use la `Alloc` y `Free` funciones cuando se asignan y liberan un conjunto fijo de tamaños de asignación desde diferentes subprocesos o tareas. El Runtime de simultaneidad almacena en caché de memoria que asigna del montón en tiempo de ejecución. El Runtime de simultaneidad contiene una memoria caché independiente para cada subproceso en ejecución; por lo tanto, el runtime administra la memoria sin usar bloqueos ni barreras de memoria. Una aplicación beneficia más desde la `Alloc` y `Free` funciones cuando se tiene acceso a la memoria caché con más frecuencia. Por ejemplo, un subproceso que llama con frecuencia a ambos `Alloc` y `Free` ventajas más que un subproceso que llama principalmente `Alloc` o `Free`.

> [!NOTE]
>  Cuando utilice estas funciones de administración de memoria y las aplicación utiliza muchos de memoria, la aplicación pueden especificar una condición de poca memoria antes de lo que espera. Dado que los bloques de memoria que se almacenan en caché mediante un subproceso no están disponibles para ningún otro subproceso, si un subproceso contiene una gran cantidad de memoria, dicha memoria no está disponible.

## <a name="example"></a>Ejemplo

Para obtener un ejemplo que usa el `Alloc` y `Free` funciones para mejorar el rendimiento de memoria, vea [Cómo: Usar Alloc y Free para mejorar el rendimiento de memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

## <a name="see-also"></a>Vea también

[Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Procedimiento para usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

