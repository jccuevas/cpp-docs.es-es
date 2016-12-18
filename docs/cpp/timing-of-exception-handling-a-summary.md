---
title: "Intervalos de control de excepciones: resumen | Microsoft Docs"
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
  - "control de excepciones, control de tiempo"
  - "controladores, orden de excepción"
  - "secuencia"
  - "secuencia, de controladores"
  - "SETJMP.H"
  - "SETJMPEX.H"
  - "control estructurado de excepciones, control de tiempo"
  - "controladores de terminación, control de tiempo"
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Intervalos de control de excepciones: resumen
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controladores de terminación se ejecutan independientemente de cómo finalice el bloque de instrucciones `__try`.  La terminación se puede producir cuando se sale del bloque `__try`, cuando una instrucción `longjmp` transfiere el control fuera del bloque y cuando se desenreda la pila debido al control de excepciones.  
  
> [!NOTE]
>  Visual C\+\+ admite dos versiones de las instrucciones `setjmp` y `longjmp`.  La versión rápida omite el control de terminación pero es más eficaz.  Para usar esta versión, incluya el archivo SETJMP.H.  La otra versión admite el control de terminación como se describe en el párrafo anterior.  Para usar esta versión, incluya el archivo SETJMPEX.H.  El aumento del rendimiento de la versión rápida depende de la configuración de hardware.  
  
 El sistema operativo ejecuta todos los controladores de terminación en el orden adecuado antes de que cualquier otro código pueda ejecutarlos, incluido el cuerpo de un controlador de excepciones.  
  
 Cuando la causa de la interrupción es una excepción, el sistema debe ejecutar primero la parte del filtro de uno o varios controladores de excepciones antes de decidir qué debe terminar.  El orden de los eventos es:  
  
1.  Se produce una excepción.  
  
2.  El sistema busca en la jerarquía de controladores de excepciones activos y ejecuta el filtro del controlador de mayor prioridad, que es el controlador de excepciones instalado más recientemente y más profundamente anidado, en términos de bloques y llamadas de función.  
  
3.  Si este filtro pasa el control \(devuelve 0\), el proceso continúa hasta que se encuentra un filtro que no pase el control.  
  
4.  Si este filtro devuelve – 1, la ejecución continúa donde se produjo la excepción y la terminación no tiene lugar.  
  
5.  Si el filtro devuelve 1, se producen los eventos siguientes:  
  
    -   El sistema desenreda la pila, borrando todos los marcos de pila entre el código que se está ejecutando actualmente \(donde se produjo la excepción\) y el marco de pila que contiene el controlador de excepciones que obtiene el control.  
  
    -   Cuando se desenreda la pila, se ejecuta cada controlador de terminación de la pila.  
  
    -   Se ejecuta el propio controlador de excepciones.  
  
    -   El control se pasa a la línea de código después del final de este controlador de excepciones.  
  
## Vea también  
 [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)   
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)