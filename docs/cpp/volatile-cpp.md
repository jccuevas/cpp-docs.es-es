---
title: "volatile (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "volatile_cpp"
  - "volatile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controladores de interrupción y palabra clave volatile"
  - "objetos [C++], volatile"
  - "volatile (palabra clave) [C++]"
  - "objetos volátiles"
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
caps.latest.revision: 43
caps.handback.revision: 43
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# volatile (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Calificador de tipo que puede utilizar para declarar que el hardware puede modificar un objeto en el programa.  
  
## Sintaxis  
  
```  
  
volatile declarator ;  
```  
  
## Comentarios  
 Puede utilizar el modificador [\/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) del compilador para modificar cómo interpreta el compilador esta palabra clave.  
  
 Visual Studio interpreta la palabra clave `volatile` de manera diferente según la arquitectura de destino.  En el caso de ARM, si no se especifica ninguna opción **\/volatile** del compilador, el compilador funciona como si se hubiera especificado **\/volatile:iso**.  En las arquitecturas distintas de ARM, si no se especifica ninguna opción **\/volatile** del compilador, el compilador funciona como si se hubiera especificado **\/volatile:ms**; por tanto, para otras arquitecturas que no sean ARM, se recomienda encarecidamente especificar **\/volatile:iso**, y utilizar tipos primitivos de sincronización e intrínsecos del compilador explícitos al tratar con memoria que se comparte entre distintos subprocesos.  
  
 Se puede utilizar el calificador `volatile` para proporcionar acceso a ubicaciones de memoria utilizadas por procesos asincrónicos como controladores de interrupciones.  
  
 Cuando `volatile` se utiliza en una variable que tiene también la palabra clave [\_\_restrict](../cpp/extension-restrict.md), tiene prioridad `volatile`.  
  
 Si un miembro `struct` está marcado como `volatile`, `volatile` se propaga a toda la estructura.  Si una estructura no tiene una longitud que se pueda copiar en la arquitectura actual mediante una instrucción, se puede perder completamente `volatile` en esa estructura.  
  
 La palabra clave `volatile` puede no tener ningún efecto sobre un campo si se cumple una de las condiciones siguientes:  
  
-   La longitud del campo volátil supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.  
  
-   La longitud del `struct` contenedor exterior, o si es miembro de un `struct` posiblemente anidado, supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.  
  
 Aunque el procesador no reordena los accesos a memoria que no pueden almacenarse en la memoria caché, las variables que no pueden almacenarse en la memoria caché deben marcarse como `volatile` para garantizar que el compilador no reordene los accesos a memoria.  
  
 Los objetos declarados como `volatile` no se utilizan en ciertas optimizaciones porque sus valores pueden cambiar en cualquier momento.  El sistema lee siempre el valor actual de un objeto volátil cuando se solicita, incluso aunque una instrucción anterior pidiera un valor del mismo objeto.  Además, el valor del objeto se escribe inmediatamente en la asignación.  
  
## Conforme a ISO  
 Si está familiarizado con la palabra clave [volatile de C\#](../Topic/volatile%20\(C%23%20Reference\).md) o con el comportamiento de `volatile` en versiones anteriores de Visual C\+\+, tenga en cuenta que la palabra clave `volatile` del estándar C\+\+11 de ISO es diferente y se admite en Visual Studio cuando se especifica la opción [\/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) del compilador. \(Para ARM, se especifica de forma predeterminada\).  La palabra clave `volatile` en código del estándar C\+\+11 de ISO se usa únicamente para el acceso de hardware; no la utilice para la comunicación entre subprocesos.  Para la comunicación entre subprocesos, emplee mecanismos como [std::atomic\<T\>](../standard-library/atomic.md) de la [Biblioteca de plantillas estándar de C\+\+](../standard-library/cpp-standard-library-reference.md).  
  
## Fin de Conforme a ISO  
  
## Específicos de Microsoft  
 Cuando se utiliza la opción **\/volatile:ms** del compilador \(de forma predeterminada, cuando el destino es una arquitectura distinta de ARM\), el compilador genera código adicional para mantener el orden entre las referencias a objetos volátiles y el orden de las referencias a otros objetos globales.  En concreto:  
  
-   Una escritura en un objeto volátil \(también conocida como escritura volátil\) tiene liberación de semántica; es decir, una referencia a un objeto global o estático que se produce antes que una escritura en un objeto volátil en la secuencia de instrucciones se realice antes que esa escritura volátil en el binario compilado.  
  
-   Una lectura de un objeto volátil \(también conocida como lectura volátil\) tiene adquisición de semántica; es decir, una referencia a un objeto global o estático que se produce después que una lectura de memoria volátil en la secuencia de instrucciones se realice después de esa lectura volátil en el binario compilado.  
  
 Esto permite utilizar objetos volátiles para bloqueos y liberaciones de memoria en aplicaciones multiproceso.  
  
> [!NOTE]
>  Cuando se basa en la seguridad mejorada que se proporciona cuando se usa la opción **\/volatile:ms** del compilador, el código es no portable.  
  
## Fin de Específicos de Microsoft  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [const](../cpp/const-cpp.md)   
 [const y volatile \(Punteros\)](../cpp/const-and-volatile-pointers.md)