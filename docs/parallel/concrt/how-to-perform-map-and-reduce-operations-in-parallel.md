---
title: "C&#243;mo: Realizar operaciones de asignaci&#243;n y reducci&#243;n en paralelo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "parallel_transform (función), ejemplo"
  - "asignación y reducir en paralelo, ejemplo"
  - "parallel_reduce (función), ejemplo"
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Realizar operaciones de asignaci&#243;n y reducci&#243;n en paralelo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este ejemplo muestra cómo utilizar el [Concurrency:: parallel_transform](../Topic/parallel_transform%20Function.md) y [concurrency::parallel_reduce](../Topic/parallel_reduce%20Function.md) algoritmos y la [concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) clase para contar las apariciones de palabras en los archivos.  
  
 Un *mapa* operación aplica una función a cada valor en una secuencia. Un *reducir* operación combina los elementos de una secuencia en un valor. Puede usar la biblioteca de plantillas estándar (STL) [std::transform](../Topic/transform.md)[std:: Accumulate](../Topic/accumulate.md) clases para realizar la asignación y reducir las operaciones. Sin embargo, si desea mejorar el rendimiento ante los diversos problemas que pueden surgir, use los algoritmos `parallel_transform` y `parallel_reduce` para realizar las operaciones map y reduce en paralelo, respectivamente. En algunos casos, puede usar `concurrent_unordered_map` para realizar map y reduce en una sola operación.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se cuentan las apariciones de las palabras en los archivos. Usa [std:: vector](vector%20Class.md) para representar el contenido de dos archivos. La operación map calcula las apariciones de cada palabra en cada vector. La operación reduce suma los recuentos de palabras de los dos vectores.  
  
 [!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/CPP/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-map-reduce.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe de paralelo mapa/EHsc-reduce.cpp**  
  
## <a name="robust-programming"></a>Programación sólida  
 En este ejemplo, puede usar la clase `concurrent_unordered_map` que se define en concurrent_unordered_map.h para realizar map y reduce en una sola operación.  
  
 [!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/CPP/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]  
  
 Por lo general, solo se ejecutan en paralelo los bucles internos o externos. Ejecute en paralelo el bucle interno si dispone de relativamente pocos archivos y cada uno de ellos contiene muchas palabras. Sin embargo, si dispone de un número razonable de archivos y cada uno de ellos contiene pocas palabras, ejecute en paralelo el bucle externo.  
  
## <a name="see-also"></a>Vea también  
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_transform (función)](../Topic/parallel_transform%20Function.md)   
 [parallel_reduce (función)](../Topic/parallel_reduce%20Function.md)   
 [concurrent_unordered_map (clase)](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
