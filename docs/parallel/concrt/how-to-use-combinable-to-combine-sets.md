---
title: "Cómo: usar la clase combinable para combinar conjuntos | Documentos de Microsoft"
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
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bbd36e9536707bc639e8f80cc019b7fda18f793
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Cómo: Usar la clase combinable para combinar conjuntos
Este tema muestra cómo utilizar el [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) clase para calcular el conjunto de números primos.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se calcula el conjunto de números primos dos veces. Cada cálculo almacena el resultado en un [std:: BitSet](../../standard-library/bitset-class.md) objeto. El ejemplo calcula en primer lugar el conjunto en serie y, a continuación, lo calcula en paralelo. También se imprime en la consola el tiempo necesario para realizar ambos cálculos.  
  
 Este ejemplo se utiliza la [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo y un `combinable` objeto para generar conjuntos locales de subprocesos. A continuación, utiliza el [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) método para combinar los conjuntos locales de subproceso en el conjunto final.  

  
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
 [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable (clase)](../../parallel/concrt/reference/combinable-class.md)   
 [combinable:: combine_each (método)](reference/combinable-class.md#combine_each)


