---
title: "Cómo: escribir un bucle parallel_for | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 60ae6b7f496f86bde91801e486315587fb693436
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-a-parallelfor-loop"></a>Cómo: Escribir un bucle parallel_for
Este ejemplo muestra cómo usar [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) para calcular el producto de dos matrices.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra la función `matrix_multiply`, que calcula el producto de dos matrices cuadradas.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra la función `parallel_matrix_multiply`, que utiliza el algoritmo `parallel_for` para realizar el bucle exterior en paralelo.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]  
  
 En este ejemplo solo se paraleliza el bucle exterior porque hace bastante trabajo para beneficiarse de la sobrecarga para el procesamiento paralelo. Si paraleliza el bucle interno, no se tendrá un aumento de rendimiento porque la cantidad de trabajo pequeña que el bucle interno realiza no supera la sobrecarga para el procesamiento paralelo. Por consiguiente, paralelizar el bucle exterior solo es la mejor manera de maximizar las ventajas de simultaneidad en la mayoría de los sistemas.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo completo compara el rendimiento de la función `matrix_multiply` frente a la función `parallel_matrix_multiply`.  
  
 [!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
```Output  
serial: 3853  
parallel: 1311  
```  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo que se denomina `parallel-matrix-multiply.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc parallel-matrix-multiply.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_for (función)](reference/concurrency-namespace-functions.md#parallel_for)


