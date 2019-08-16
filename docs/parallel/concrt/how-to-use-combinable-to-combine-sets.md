---
title: Procedimiento Usar la clase combinable para combinar conjuntos
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: bf8a5bee65ea0ba1718c1d4d436b6af3e0b95961
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345583"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Procedimiento Usar la clase combinable para combinar conjuntos

En este tema se muestra cómo usar el [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) clase para calcular el conjunto de números primos.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se calcula el conjunto de números primos dos veces. Cada cálculo almacena el resultado en un [std:: BitSet](../../standard-library/bitset-class.md) objeto. El ejemplo calcula en primer lugar el conjunto en serie y, a continuación, lo calcula en paralelo. También se imprime en la consola el tiempo necesario para realizar ambos cálculos.

Este ejemplo se usa el [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo y un `combinable` objeto para generar conjuntos locales de subprocesos. A continuación, usa el [combine_each](reference/combinable-class.md#combine_each) método para combinar los conjuntos locales de subprocesos en el conjunto final.

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-combine-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe /EHsc parallel-combine-primes.cpp**

## <a name="see-also"></a>Vea también

[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable (clase)](../../parallel/concrt/reference/combinable-class.md)<br/>
[combinable:: combine_each (método)](reference/combinable-class.md#combine_each)
