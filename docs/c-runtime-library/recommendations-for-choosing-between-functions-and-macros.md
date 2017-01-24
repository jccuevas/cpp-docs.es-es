---
title: "Recomendaciones para elegir entre funciones y macros | Microsoft Docs"
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
  - "c.functions"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "funciones [CRT], frente a macros"
  - "macros, frente a funciones"
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Recomendaciones para elegir entre funciones y macros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se compilan la mayoría de las rutinas de biblioteca en tiempo de ejecución de Microsoft o funciones ensambladas, pero algunas rutinas se implementan como macros.  Cuando un archivo de encabezado declara una función y una versión de macro de una rutina, la definición de macro tiene prioridad, porque siempre aparece después de la declaración de función.  Cuando se invoca una rutina que se implementa como una función y macro, puede hacer que el compilador para utilizar la versión de la función de dos maneras:  
  
-   Agregue el nombre tiene entre paréntesis.  
  
    ```  
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   “Anular” la definición de macro con la directiva de `#undef` :  
  
    ```  
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
 Si necesita elegir entre una función y una implementación de macro de una rutina de biblioteca, considere las compensaciones siguientes:  
  
-   La ventaja principal de**Speed versus size** The de utilizar macros es un runtime más rápido.  Durante el preprocesamiento, una macro es \(reemplazado por la definición\) insertado expandido cada vez que se utiliza.  Una definición de función sólo aparece una vez independientemente de cuántas veces se denomina.  Las macros pueden aumentar el tamaño de código pero no tienen la sobrecarga asociada a llamadas de función.  
  
-   La función de**Function evaluation** A evalúa una dirección; una macro no.  Así no puede utilizar un nombre de macro en contextos que requieren un puntero.  Por ejemplo, puede declarar un puntero a una función, pero no un puntero a una macro.  
  
-   **Type\-checking** Cuando se declara una función, el compilador puede comprobar los tipos de argumentos.  Porque no se puede declarar una macro, el compilador no puede comprobar tipos de argumentos de macro; aunque puede comprobar el número de argumentos que se pasan a una macro.  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)