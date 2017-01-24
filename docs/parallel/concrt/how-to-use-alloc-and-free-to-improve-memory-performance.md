---
title: "C&#243;mo: Usar Alloc y Free para mejorar el rendimiento de la memoria | Microsoft Docs"
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
  - "Alloc y Free, usar [Runtime de simultaneidad]"
  - "Usar Alloc y Free [Runtime de simultaneidad]"
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Usar Alloc y Free para mejorar el rendimiento de la memoria
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se muestra cómo usar las funciones [concurrency::Alloc](../Topic/Alloc%20Function.md) y [concurrency::Free](../Topic/Free%20Function.md) para mejorar el rendimiento de la memoria.  Se compara el tiempo necesario para invertir los elementos de una matriz en paralelo para tres tipos diferentes, cada uno de los cuales especifica los operadores `new` y `delete`.  
  
 Las funciones `Free` y `Alloc` son muy útiles cuando varios subprocesos llaman frecuentemente a `Alloc` y `Free`.  El runtime contiene una memoria caché independiente para cada subproceso; por consiguiente, el runtime administra la memoria sin el uso de bloqueos ni barreras de memoria.  
  
## Ejemplo  
 En el siguiente ejemplo se muestran tres tipos que especifican los operadores `new` y `delete`.  La clase `new_delete` usa los operadores globales `new` y `delete`, la clase `malloc_free` usa las funciones [malloc](../../c-runtime-library/reference/malloc.md) y [free](../../c-runtime-library/reference/free.md) del Runtime de C y la clase `Alloc_Free` usa las funciones `Free` y `Alloc` del Runtime de simultaneidad.  
  
 [!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/CPP/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]  
  
## Ejemplo  
 En el ejemplo siguiente se muestran las funciones `swap` y `reverse_array`.  La función `swap` intercambia el contenido de la matriz en los índices especificados.  Asigna la memoria del montón para la variable temporal.  La función `reverse_array` crea una matriz grande y calcula el tiempo necesario para invertir esa matriz varias veces en paralelo.  
  
 [!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/CPP/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]  
  
## Ejemplo  
 En el siguiente ejemplo se muestra la función `wmain`, que calcula el tiempo necesario para que la función `reverse_array` actúe en los tipos `new_delete`, `malloc_free`, y `Alloc_Free`, cada uno de los cuales usa un esquema de asignación de memoria diferente.  
  
 [!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/CPP/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]  
  
## Ejemplo  
 A continuación se muestra el ejemplo completo.  
  
 [!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/CPP/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]  
  
 En este ejemplo se genera la siguiente salida de ejemplo para un equipo que tiene cuatro procesadores.  
  
  **Took 2031 ms with new\/delete.**  
**Took 1672 ms with malloc\/free.**  
**Took 656 ms with Alloc\/Free.** En este ejemplo, el tipo que usa las funciones `Alloc` y `Free` proporciona el mejor rendimiento de la memoria porque las funciones `Alloc` y `Free` se optimizan para asignar y liberar con frecuencia los bloques de memoria de varios subprocesos.  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `allocators.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc allocators.cpp**  
  
## Vea también  
 [Funciones de administración de memoria](../../parallel/concrt/memory-management-functions.md)   
 [Alloc \(Función\)](../Topic/Alloc%20Function.md)   
 [Free \(Función\)](../Topic/Free%20Function.md)