---
title: "C&#243;mo: Escribir un bucle parallel_for | Microsoft Docs"
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
  - "escribir un bucle parallel_for [Runtime de simultaneidad]"
  - "parallel_for (función), ejemplo"
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Escribir un bucle parallel_for
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este ejemplo se muestra cómo utilizar [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) para calcular el producto de dos matrices.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra la función `matrix_multiply`, que calcula el producto de dos matrices cuadradas.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_1.cpp)]  
  
## Ejemplo  
 En el siguiente ejemplo se muestra la función `parallel_matrix_multiply`, que utiliza el algoritmo `parallel_for` para realizar el bucle exterior en paralelo.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_2.cpp)]  
  
 En este ejemplo solo se paraleliza el bucle exterior porque hace bastante trabajo para beneficiarse de la sobrecarga para el procesamiento paralelo.  Si paraleliza el bucle interno, no se tendrá un aumento de rendimiento porque la cantidad de trabajo pequeña que el bucle interno realiza no supera la sobrecarga para el procesamiento paralelo.  Por consiguiente, paralelizar el bucle exterior solo es la mejor manera de maximizar las ventajas de simultaneidad en la mayoría de los sistemas.  
  
## Ejemplo  
 El siguiente ejemplo completo compara el rendimiento de la función `matrix_multiply` frente a la función `parallel_matrix_multiply`.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/CPP/how-to-write-a-parallel-for-loop_3.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
  **serie: 3853**  
**parallel: 1311**   
## Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o en un archivo denominado `parallel-matrix-multiply.cpp` y ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc parallel\-matrix\-multiply.cpp**  
  
## Vea también  
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for \(Función\)](../Topic/parallel_for%20Function.md)