---
title: "C&#243;mo: Usar la clase combinable para combinar conjuntos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "combinable (clase), ejemplo"
  - "combinar conjuntos con combinable [Runtime de simultaneidad]"
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# C&#243;mo: Usar la clase combinable para combinar conjuntos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se muestra cómo usar la clase [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) para calcular el conjunto de números primos.  
  
## Ejemplo  
 En el siguiente ejemplo se calcula el conjunto de números primos dos veces.  Cada cálculo almacena el resultado en un objeto [std::bitset](../../standard-library/bitset-class.md).  El ejemplo calcula en primer lugar el conjunto en serie y, a continuación, lo calcula en paralelo.  También se imprime en la consola el tiempo necesario para realizar ambos cálculos.  
  
 En este ejemplo se usa el algoritmo [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) y un objeto `combinable` para generar conjuntos locales de subprocesos.  A continuación, se usa el método [concurrency::combinable::combine\_each](../Topic/combinable::combine_each%20Method.md) para combinar los conjuntos locales de subprocesos en el conjunto final.  
  
 [!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/CPP/how-to-use-combinable-to-combine-sets_1.cpp)]  
  
 La siguiente salida de ejemplo corresponde a un equipo con cuatro procesadores.  
  
  **serial time: 312 ms**  
**parallel time: 78 ms**   
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `parallel-combine-primes.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc parallel\-combine\-primes.cpp**  
  
## Vea también  
 [Contenedores y objetos paralelos](../../parallel/concrt/parallel-containers-and-objects.md)   
 [Clase combinable](../../parallel/concrt/reference/combinable-class.md)   
 [combinable::combine\_each \(Método\)](../Topic/combinable::combine_each%20Method.md)