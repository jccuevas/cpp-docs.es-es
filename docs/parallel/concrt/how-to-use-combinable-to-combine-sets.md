---
title: 'Cómo: Usar la clase combinable para combinar conjuntos'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: 7ccbb3e8bad5c4d3b6f4177afbfdba3e200681a5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142129"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Cómo: Usar la clase combinable para combinar conjuntos

En este tema se muestra cómo usar la clase [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) para calcular el conjunto de números primos.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se calcula el conjunto de números primos dos veces. Cada cálculo almacena el resultado en un objeto [STD:: BitSet](../../standard-library/bitset-class.md) . El ejemplo calcula en primer lugar el conjunto en serie y, a continuación, lo calcula en paralelo. También se imprime en la consola el tiempo necesario para realizar ambos cálculos.

En este ejemplo se usa el algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) y un objeto `combinable` para generar conjuntos locales de subprocesos. A continuación, usa el método [Concurrency:: combinable:: combine_each](reference/combinable-class.md#combine_each) para combinar los conjuntos locales del subproceso en el conjunto final.

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `parallel-combine-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Parallel-combine-primes. cpp**

## <a name="see-also"></a>Consulte también

[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable (clase)](../../parallel/concrt/reference/combinable-class.md)<br/>
[combinable:: combine_each (método)](reference/combinable-class.md#combine_each)
