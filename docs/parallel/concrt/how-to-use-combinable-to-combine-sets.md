---
title: 'Cómo: usar la clase combinable para combinar conjuntos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 69f48ed099fe033ba1847a3414ed8e5c5ce88f71
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433678"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Cómo: Usar la clase combinable para combinar conjuntos

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

**cl.exe/EHsc parallel-combine-primes.cpp**

## <a name="see-also"></a>Vea también

[Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable (clase)](../../parallel/concrt/reference/combinable-class.md)<br/>
[combinable:: combine_each (método)](reference/combinable-class.md#combine_each)

