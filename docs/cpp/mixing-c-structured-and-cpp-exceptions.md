---
title: "Mezclar excepciones de C (Estructurado) y C++ | Microsoft Docs"
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
  - "control de excepciones de C++, varios lenguajes"
  - "catch (palabra clave) [C++], mixtos"
  - "excepciones, mezcla de C y C++"
  - "control estructurado de excepciones, mezcla de C y C++"
  - "try-catch (palabra clave) [C++], varios lenguajes"
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mezclar excepciones de C (Estructurado) y C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si desea escribir código más portable, no se recomienda utilizar el control de excepciones estructuradas en un programa de C\+\+.  Sin embargo, puede que a veces desee compilar con **\/EHa** y mezclar excepciones estructuradas y código fuente de C\+\+ estructurado, con lo que necesitará alguna capacidad para controlar ambos tipos de excepciones.  Dado que un controlador de excepciones estructuradas no tiene el concepto de objetos ni de excepciones con tipo, no puede controlar las excepciones producidas por código de C\+\+; sin embargo, los controladores **catch** de C\+\+ pueden controlar excepciones estructuradas.  Como tal, la sintaxis de control de excepciones de C\+\+ \(**try**, `throw`, **catch**\) no es aceptada por el compilador de C, pero la sintaxis del control de excepciones estructuradas \(`__try`, `__except`, `__finally`\) es admitida por el compilador de C\+\+.  
  
 Vea [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md) para obtener información sobre el control de excepciones estructuradas como excepciones de C\+\+.  
  
 Si mezcla excepciones estructuradas y de C\+\+, tenga en cuenta lo siguiente:  
  
1.  Las excepciones de C\+\+ y las excepciones estructuradas no se pueden mezclar dentro de la misma función.  
  
2.  Los controladores de finalización \(bloques `__finally`\) se ejecutan siempre, incluso durante el desenredo después de producirse una excepción.  
  
3.  El control de excepciones de C\+\+ puede detectar y conservar la semántica de desenredo en todos los módulos compilados con la opción del compilador [\/EH](../build/reference/eh-exception-handling-model.md) \(esta opción habilita la semántica de desenredo\).  
  
4.  Puede que haya situaciones en las que no se llame a las funciones de destructor para todos los objetos.  Por ejemplo, si una excepción estructurada se produce al intentar realizar una llamada de función a través de un puntero de función inicializado, y esa función toma como parámetros objetos que se construyeron antes de la llamada, no se llamará a los destructores de esos objetos durante el desenredo de la pila.  
  
## ¿Qué más desea saber?  
  
-   [Uso de setjmp o longjmp en programas de C\+\+](../cpp/using-setjmp-longjmp.md)  
  
-   [Diferencias entre SEH y C\+\+ EH](../cpp/exception-handling-differences.md)  
  
## Vea también  
 [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md)