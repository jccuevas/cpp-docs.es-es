---
title: "inline_recursion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "inline_recursion_CPP"
  - "vc-pragma.inline_recursion"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inline_recursion (pragma)"
  - "pragma (directivas), inline_recursion"
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# inline_recursion
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Controla la expansión en línea de llamadas de función directas o mutuamente recursivas.  
  
## Sintaxis  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## Comentarios  
 Use esta pragma para controlar funciones marcadas como [inline](../misc/inline-inline-forceinline.md) e [\_\_inline](../misc/inline-inline-forceinline.md) o funciones que el compilador expanda automáticamente bajo la opción \/Ob2.  El uso de esta pragma requiere que la configuración de la opción del compilador [\/Ob](../build/reference/ob-inline-function-expansion.md) sea 1 o 2.  El estado predeterminado de `inline_recursion` es desactivado.  Esta pragma tiene efecto en la primera llamada de función después de que se considere la directiva pragma y no afecta a la definición de la función.  
  
 La directiva pragma `inline_recursion` controla cómo se expanden las funciones recursivas.  Si `inline_recursion` está desactivada y una función insertada se llama a sí misma \(directa o indirectamente\), la función solo se expande una vez.  Si `inline_recursion` está activada, la función se expande varias veces hasta alcanzar el valor establecido con la directiva pragma [inline\_depth](../preprocessor/inline-depth.md), el valor predeterminado para funciones recursivas definido por la directiva pragma `inline_depth` o un límite de capacidad.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline\_depth](../preprocessor/inline-depth.md)   
 [\/Ob \(Expansión de funciones inline\)](../build/reference/ob-inline-function-expansion.md)