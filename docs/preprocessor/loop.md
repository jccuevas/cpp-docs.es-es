---
title: "loop | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "loop_CPP"
  - "vc-pragma.loop"
dev_langs: 
  - "C++"
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# loop
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Controla cómo el paralelizador automático debe considerar el código del bucle y\/o excluye un bucle de la consideración del vectorizador automático.  
  
## Sintaxis  
  
```  
  
#pragma loop( hint_parallel(n) )  
```  
  
```  
  
#pragma loop( no_vector )  
```  
  
```  
  
#pragma loop( ivdep )  
```  
  
#### Parámetros  
 `hint_parallel(` `n` `)`  
 Sugiere al compilador que este bucle se ejecute en paralelo en `n` subprocesos, donde `n` es un literal entero positivo o cero.  Si `n` es cero, se usa el número máximo de subprocesos en tiempo de ejecución.  Esta es una sugerencia que se hace al compilador, no una orden y, por tanto, no existen garantías de que el bucle se ejecute en paralelo.  Si el bucle tiene dependencias de datos o problemas estructurales \(por ejemplo, el bucle se almacena en un valor escalar que se usa más allá del cuerpo del bucle\), el bucle no se ejecuta en paralelo.  
  
 El compilador omite esta opción a menos que se especifique el modificador del compilador [\/Qpar](../build/reference/qpar-auto-parallelizer.md).  
  
 `no_vector`  
 De forma predeterminada, el vectorizador automático está activado e intentará vectorizar todos los bucles que evalúe de modo que se beneficien de él.  Especifique esta directiva pragma para deshabilitar el vectorizador automático para el bucle que aparece detrás.  
  
 `ivdep`  
 Sugiere al compilador que omita las dependencias de vector de este bucle.  Se utiliza junto con `hint_parallel`.  
  
## Comentarios  
 Para utilizar la directiva pragma `loop`, colóquela inmediatamente antes de una definición de bucle, no dentro de ella.  La directiva pragma surte efecto para el ámbito del bucle que aparece detrás.  Puede aplicar varias directivas pragma a un bucle, en cualquier orden, pero debe establecer cada una de ellas en una instrucción pragma diferente.  
  
## Vea también  
 [Paralelización y vectorización automáticas](../parallel/auto-parallelization-and-auto-vectorization.md)   
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)