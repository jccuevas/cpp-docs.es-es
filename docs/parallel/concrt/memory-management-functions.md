---
title: "Funciones de administración de memoria | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 309080a807a1325bbf921657a152cff60e87cb95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-functions"></a>Funciones de administración de memoria
Este documento describe las funciones de administración de memoria que el Runtime de simultaneidad proporciona para ayudarle a asignar y liberar memoria de manera simultánea.  
  
> [!TIP]
>  Runtime de simultaneidad proporciona un programador predeterminado, por lo que no deberá crear uno en la aplicación. Dado que el programador de tareas permite ajustar el rendimiento de las aplicaciones, es recomendable que comience con la [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si está nuevo para el Runtime de simultaneidad.  
  
 El Runtime de simultaneidad proporciona dos funciones de administración de memoria que se optimizan para asignar y liberar bloques de memoria de forma simultánea. El [Concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) función asigna un bloque de memoria utilizando el tamaño especificado. El [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) función libera la memoria asignada por `Alloc`.  
  
> [!NOTE]
>  El `Alloc` y `Free` funciones confían entre sí. Use la `Free` función solo para liberar la memoria que se asigna utilizando el `Alloc` función. Además, cuando se usa el `Alloc` función para asignar memoria, use solo la `Free` función liberar esa memoria.  
  
 Use la `Alloc` y `Free` funciona cuando se asignan y liberan un conjunto fijo de tamaños de asignación de subprocesos diferentes o tareas. El Runtime de simultaneidad almacena en memoria caché de memoria que asigna del montón en tiempo de ejecución de C. El Runtime de simultaneidad contiene una memoria caché independiente para cada subproceso en ejecución; por lo tanto, el runtime administra la memoria sin el uso de bloqueos ni barreras de memoria. Una aplicación beneficia más de los `Alloc` y `Free` funciona cuando se tiene acceso a la memoria caché con más frecuencia. Por ejemplo, un subproceso que llama con frecuencia a ambos `Alloc` y `Free` ventajas más de un subproceso que llama principalmente `Alloc` o `Free`.  
  
> [!NOTE]
>  Cuando utilice estas funciones de administración de memoria y las aplicación utiliza muchos de memoria, la aplicación pueden especificar una condición de memoria insuficiente antes de lo que espera. Dado que los bloques de memoria que se almacenan en caché por un subproceso no están disponibles para ningún otro subproceso, si un subproceso tiene una gran cantidad de memoria, dicha memoria no está disponible.  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que usa el `Alloc` y `Free` funciones para mejorar el rendimiento de memoria, vea [Cómo: Usar Alloc y Free para mejorar el rendimiento de memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
## <a name="see-also"></a>Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Procedimiento para usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

