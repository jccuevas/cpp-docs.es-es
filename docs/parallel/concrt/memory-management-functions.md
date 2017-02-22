---
title: "Funciones de administraci&#243;n de memoria | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones de administración de memoria [Runtime de simultaneidad]"
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Funciones de administraci&#243;n de memoria
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se describen las funciones de administración de memoria que el runtime de simultaneidad proporciona para ayudarle a asignar y liberar memoria de manera simultánea.  
  
> [!TIP]
>  El runtime de simultaneidad proporciona un programador predeterminado y, por tanto, no es necesario crear uno en la aplicación.  Dado que el programador de tareas ayuda a ajustar el rendimiento de las aplicaciones, se recomienda que comience con [Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) o [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) si no ha usado antes el runtime de simultaneidad.  
  
 El Runtime de simultaneidad proporciona dos funciones de administración de memoria que se optimizan para asignar y liberar los bloques de memoria de manera simultánea.  La función de [concurrency::Alloc](../Topic/Alloc%20Function.md) asigna un bloque de memoria con el tamaño especificado.  La función de [concurrency::Free](../Topic/Free%20Function.md) libera la memoria que se asignó mediante `Alloc`.  
  
> [!NOTE]
>  Las funciones `Free` y `Alloc` confían la una en la otra.  Use la función `Free` solo para liberar memoria que se asigna utilizando la función `Alloc`.  Asimismo, cuando se usa la función `Alloc` para asignar memoria, use solo la función `Free` para liberar dicha memoria.  
  
 Utilice las funciones `Free` y `Alloc` cuando asigna y libera un conjunto fijo de tamaños de asignación de subprocesos o tareas diferentes.  El Runtime de simultaneidad almacena en caché la memoria que asigna del montón del Runtime de C.  El Runtime de simultaneidad contiene una memoria caché independiente para cada subproceso; por consiguiente, el runtime administra la memoria sin el uso de bloqueos ni barreras de memoria.  Una aplicación se beneficia más de las funciones `Free` y `Alloc` cuando se tiene acceso a la memoria caché con más frecuencia.  Por ejemplo, un subproceso que llama con frecuencia a `Alloc` y `Free` es más beneficioso que un subproceso que llama principalmente a `Alloc` o `Free`.  
  
> [!NOTE]
>  Cuando se usan estas funciones de administración de memoria y la aplicación usa mucha memoria, la aplicación puede producir un problema de memoria insuficiente antes de lo que se espera.  Dado que los bloques de memoria que un subproceso almacena en memoria caché no están disponibles para otro subproceso, si un subproceso contiene mucha memoria, esa memoria no está disponible.  
  
## Ejemplo  
 Para obtener un ejemplo que utiliza funciones `Free` y `Alloc` para mejorar el rendimiento de la memoria, vea [Cómo: Usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
## Vea también  
 [Programador de tareas](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Cómo: Usar Alloc y Free para mejorar el rendimiento de la memoria](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)