---
title: "Informaci&#243;n general sobre las instrucciones de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "instrucciones, C++"
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general sobre las instrucciones de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las instrucciones de C\+\+ se ejecutan secuencialmente, excepto cuando una instrucción de expresión, una instrucción de selección, una instrucción de iteración o una instrucción de salto modifica específicamente esa secuencia.  
  
 Las instrucciones pueden ser de los tipos siguientes:  
  
```  
  
        labeled-statement  
expression-statement  
compound-statement  
selection-statement  
iteration-statement  
jump-statement  
declaration-statement  
try-throw-catch  
```  
  
 En la mayoría de los casos, la sintaxis de la instrucción de C\+\+ es idéntica a la de ANSI C.  La principal diferencia entre los dos es que en C las declaraciones solo se permiten al principio de un bloque; C\+\+ agrega el elemento *declaration\-statement*, que elimina eficazmente esta restricción.  Esto permite introducir variables en un punto del programa donde se puede calcular un valor de inicialización precalculado.  
  
 Declarar variables dentro de bloques también permite controlar con precisión el ámbito y la duración de esas variables.  
  
 Los temas sobre instrucciones describen las siguientes palabras clave de C\+\+:  
  
|||||  
|-|-|-|-|  
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[\_\_if\_exists](../cpp/if-exists-statement.md)|[\_\_try](../cpp/structured-exception-handling-c-cpp.md)|  
|[case](../cpp/switch-statement-cpp.md)|[\_\_except](../cpp/structured-exception-handling-c-cpp.md)|[\_\_if\_not\_exists](../cpp/if-not-exists-statement.md)|[try](../cpp/try-throw-and-catch-statements-cpp.md)|  
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[\_\_leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|  
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||  
|[default](../cpp/switch-statement-cpp.md)|[\_\_finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||  
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||  
  
## Vea también  
 [Instrucciones](../cpp/statements-cpp.md)