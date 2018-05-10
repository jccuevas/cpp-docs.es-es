---
title: 'Cómo: Usar Alloc y Free para mejorar el rendimiento de la memoria | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0be6fa309975663126331a7e38be0f2bea7dcf17
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Cómo: Usar Alloc y Free para mejorar el rendimiento de la memoria

Este documento muestra cómo utilizar el [Concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) y [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) funciones para mejorar el rendimiento de memoria. Se compara el tiempo necesario para invertir los elementos de una matriz en paralelo para tres tipos diferentes, cada uno de los cuales especifica los operadores `new` y `delete`.  

  
 Las funciones `Alloc` y `Free` son muy útiles cuando varios subprocesos llaman frecuentemente a `Alloc` y `Free`. El runtime contiene una memoria caché independiente para cada subproceso; por consiguiente, el runtime administra la memoria sin el uso de bloqueos ni barreras de memoria.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestran tres tipos que especifican los operadores `new` y `delete`. El `new_delete` clase utiliza global `new` y `delete` operadores, el `malloc_free` clase utiliza el tiempo de ejecución de C [malloc](../../c-runtime-library/reference/malloc.md) y [libre](../../c-runtime-library/reference/free.md) funciones y el `Alloc_Free` clase usa el Runtime de simultaneidad `Alloc` y `Free` funciones.  
  
 [!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran las funciones `swap` y `reverse_array`. La función `swap` intercambia el contenido de la matriz en los índices especificados. Asigna la memoria del montón para la variable temporal. La función `reverse_array` crea una matriz grande y calcula el tiempo necesario para invertir esa matriz varias veces en paralelo.  
  
 [!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra la función `wmain`, que calcula el tiempo necesario para que la función `reverse_array` actúe en los tipos `new_delete`, `malloc_free`, y `Alloc_Free`, cada uno de los cuales usa un esquema de asignación de memoria diferente.  
  
 [!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]  
  
## <a name="example"></a>Ejemplo  
 A continuación se muestra el ejemplo completo.  
  
 [!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]  
  
 En este ejemplo se genera la siguiente salida de ejemplo para un equipo que tiene cuatro procesadores.  
  
```Output  
Took 2031 ms with new/delete.  
Took 1672 ms with malloc/free.  
Took 656 ms with Alloc/Free.  
```  
  
 En este ejemplo, el tipo que usa las funciones `Alloc` y `Free` proporciona el mejor rendimiento de la memoria porque las funciones `Alloc` y `Free` se optimizan para asignar y liberar con frecuencia los bloques de memoria de varios subprocesos.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `allocators.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc allocators.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Funciones de administración de memoria](../../parallel/concrt/memory-management-functions.md)   
 [Alloc (función)](reference/concurrency-namespace-functions.md#alloc)   
 [Free (función)](reference/concurrency-namespace-functions.md#free)

