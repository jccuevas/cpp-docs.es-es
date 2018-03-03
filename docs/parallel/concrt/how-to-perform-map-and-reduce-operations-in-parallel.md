---
title: "Cómo: realizar la asignación y reducir las operaciones en paralelo | Documentos de Microsoft"
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
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84e38dd845f3503512f48c19e226d56d9978cc21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Cómo: Realizar operaciones de asignación y reducción en paralelo

Este ejemplo muestra cómo utilizar el [Concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) y [Concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algoritmos y [Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)clase para contar las apariciones de palabras en los archivos.  
  
 A *mapa* operación aplica una función a cada valor en una secuencia. A *reducir* operación combina los elementos de una secuencia en un valor. Puede usar la biblioteca estándar de C++ [std:: Transform](../../standard-library/algorithm-functions.md#transform) y [std:: Accumulate](../../standard-library/numeric-functions.md#accumulate) funciones para realizar la asignación y reducir las operaciones. Sin embargo, si desea mejorar el rendimiento ante los diversos problemas que pueden surgir, use los algoritmos `parallel_transform` y `parallel_reduce` para realizar las operaciones map y reduce en paralelo, respectivamente. En algunos casos, puede usar `concurrent_unordered_map` para realizar map y reduce en una sola operación.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se cuentan las apariciones de las palabras en los archivos. Usa [std:: vector](../../standard-library/vector-class.md) para representar el contenido de dos archivos. La operación map calcula las apariciones de cada palabra en cada vector. La operación reduce suma los recuentos de palabras de los dos vectores.  
  
 [!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `parallel-map-reduce.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc parallel-map-reduce.cpp**  
  
## <a name="robust-programming"></a>Programación sólida  
 En este ejemplo, puede usar la clase `concurrent_unordered_map` que se define en concurrent_unordered_map.h para realizar map y reduce en una sola operación.  
  
 [!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]  
  
 Por lo general, solo se ejecutan en paralelo los bucles internos o externos. Ejecute en paralelo el bucle interno si dispone de relativamente pocos archivos y cada uno de ellos contiene muchas palabras. Sin embargo, si dispone de un número razonable de archivos y cada uno de ellos contiene pocas palabras, ejecute en paralelo el bucle externo.  
  
## <a name="see-also"></a>Vea también  
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_transform (función)](reference/concurrency-namespace-functions.md#parallel_transform)   
 [parallel_reduce (función)](reference/concurrency-namespace-functions.md#parallel_reduce)   
 [concurrent_unordered_map (clase)](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
