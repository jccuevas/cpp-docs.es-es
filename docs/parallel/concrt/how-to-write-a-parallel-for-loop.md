---
title: Filtrar Escribir un bucle parallel_for
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: d6ac30a5de0ff45adad1064aeab708e6a84f5e9f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283597"
---
# <a name="how-to-write-a-parallelfor-loop"></a>Filtrar Escribir un bucle parallel_for

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

Para compilar el código, cópielo y, a continuación, péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-matrix-multiply.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc paralelo-matrix-multiply.cpp**

## <a name="see-also"></a>Vea también

[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for (función)](reference/concurrency-namespace-functions.md#parallel_for)
