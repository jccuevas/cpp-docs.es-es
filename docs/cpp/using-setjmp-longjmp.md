---
title: "Usar setjmp/longjmp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "longjmp"
  - "setjmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones de C++, setjmp/longjmp (funciones)"
  - "longjmp (función) en programas de C++"
  - "setjmp (función)"
  - "setjmp (función), programas en C++"
  - "SETJMP.H"
  - "SETJMPEX.H"
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Usar setjmp/longjmp
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se utilizan conjuntamente [setjmp](../c-runtime-library/reference/setjmp.md) y [longjmp](../c-runtime-library/reference/longjmp.md), proporcionan una manera de ejecutar una instrucción `goto` no local.  Se utilizan normalmente para pasar el control de la ejecución al control de errores o al código de recuperación en una rutina invocada anteriormente sin utilizar convenciones estándar de llamada o devolución.  
  
> [!CAUTION]
>  Sin embargo, como `setjmp` y `longjmp` no admiten la semántica de objeto de C\+\+, y como además pueden degradar el rendimiento evitando la optimización en variables locales, se recomienda que no se utilicen en los programas de C\+\+.  Se recomienda utilizar construcciones `try`\/`catch` en su lugar.  
  
 Si decide utilizar `setjmp`\/`longjmp` en un programa de C \+\+, incluya también SETJMP.H o SETJMPEX.H para garantizar la interacción correcta entre las funciones y el control de excepciones de C\+\+.  Si utiliza [\/EH](../build/reference/eh-exception-handling-model.md) para compilar, se llama a los destructores para objetos locales durante el desenredo de la pila.  Si utiliza **\/EHs** para compilar, y una de sus funciones llama a una función que utiliza [nothrow](../cpp/nothrow-cpp.md) y la función que usa `nothrow` llama a `longjmp`, puede que no se produzca el desenredo del destructor, dependiendo del optimizador.  
  
 En código portable, cuando se ejecuta una instrucción `goto` no local que llama a `longjmp`, la destrucción correcta de objetos basados en marcos podría no ser confiable.  
  
## Vea también  
 [Mezclar excepciones de C \(Estructurado\) y C\+\+](../cpp/mixing-c-structured-and-cpp-exceptions.md)