---
title: "3.2 Lock Functions | Microsoft Docs"
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
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2 Lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las funciones descritas en esta sección manipulan bloqueos utilizado para la sincronización.  
  
 Para las funciones siguientes, la variable de bloqueo debe ser de tipo **omp\_lock\_t**.  Esta variable debe realizarse únicamente con estas funciones.  Todas las funciones de bloqueo requieren un argumento con un puntero al tipo de **omp\_lock\_t** .  
  
-   La función de `omp_init_lock` inicializa un bloqueo simple.  
  
-   la función de `omp_destroy_lock` quita un bloqueo simple.  
  
-   La función de `omp_set_lock` espera hasta que un bloqueo simple esté disponible.  
  
-   Las versiones de la función de `omp_unset_lock` un bloqueo simple.  
  
-   las pruebas de función de `omp_test_lock` un bloqueo simple.  
  
 Para las funciones siguientes, la variable de bloqueo debe ser de tipo **omp\_nest\_lock\_t**.  Esta variable debe realizarse únicamente con estas funciones.  Todas las funciones de bloqueo encajables requieren un argumento con un puntero al tipo de **omp\_nest\_lock\_t** .  
  
-   La función de `omp_init_nest_lock` inicializa un bloqueo encajable.  
  
-   la función de `omp_destroy_nest_lock` quita un bloqueo encajable.  
  
-   La función de `omp_set_nest_lock` espera hasta que un bloqueo encajable esté disponible.  
  
-   Las versiones de la función de `omp_unset_nest_lock` un bloqueo encajable.  
  
-   las pruebas de función de `omp_test_nest_lock` un bloqueo encajable.  
  
 Las funciones de bloqueo de OpenMP tienen acceso a la variable de bloqueo de modo que lean y actualizar siempre el valor más actual de la variable de bloqueo.  Por consiguiente, no es necesario que un programa de OpenMP incluya las directivas explícitas de **vaciado** para asegurarse de que el valor de variable de bloqueo es coherente entre subprocesos diferentes.  \(Puede haber una necesidad de las directivas de **vaciado** de crear los valores de otras variables coherentes.\)