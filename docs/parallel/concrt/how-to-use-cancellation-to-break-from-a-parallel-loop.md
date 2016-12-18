---
title: "C&#243;mo: Usar la cancelaci&#243;n para interrumpir un bucle Parallel | Microsoft Docs"
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
  - "algoritmo de búsqueda paralelo, escribir [Runtime de simultaneidad]"
  - "escribir un algoritmo de búsqueda paralelo [Runtime de simultaneidad]"
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
caps.latest.revision: 19
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Usar la cancelaci&#243;n para interrumpir un bucle Parallel
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este ejemplo muestra cómo se usa la cancelación para implementar un algoritmo de búsqueda paralelo básico.  
  
## Ejemplo  
 En el siguiente ejemplo se usa la cancelación para buscar un elemento en una matriz.  La función de `parallel_find_any` utiliza el algoritmo de [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) y la función de [concurrency::run\_with\_cancellation\_token](../Topic/run_with_cancellation_token%20Function.md) para buscar la posición que contiene el valor especificado.  Cuando el bucle paralelo encuentra el valor, llama al método de [concurrency::cancellation\_token\_source::cancel](../Topic/cancellation_token_source::cancel%20Method.md) para cancelar el trabajo posterior.  
  
 [!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/CPP/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]  
  
 El algoritmo de [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) actúa en paralelo.  Por consiguiente, no realiza las operaciones en un orden predeterminado.  Si la matriz contiene varias instancias del valor, el resultado puede ser cualquiera de sus posiciones.  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio, o péguelo en un archivo denominado `parallel-array-search.cpp` y después se ejecute el siguiente comando en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc parallel\-array\-search.cpp**  
  
## Vea también  
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [parallel\_for \(Función\)](../Topic/parallel_for%20Function.md)   
 [cancellation\_token\_source \(Clase\)](../../parallel/concrt/reference/cancellation-token-source-class.md)