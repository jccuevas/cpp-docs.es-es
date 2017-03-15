---
title: "Intr&#237;nsecos del controlador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), intrínsecos"
  - "cl.exe (compilador), rendimiento"
  - "intrínsecos del compilador"
  - "intrínsecos, compilador"
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# Intr&#237;nsecos del controlador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La mayoría de las funciones está recogida en bibliotecas, pero algunas funciones están incorporadas en el compilador \(es decir, son intrínsecas\).  Estas se conocen como funciones intrínsecas o intrínsecos.  
  
## Comentarios  
 Si una función es un intrínseco, el código de dicha función suele estar insertado, con lo que se evita la sobrecarga de una llamada de función y se emiten instrucciones de código máquina altamente eficientes para dicha función.  Un intrínseco suele ser más rápido que el ensamblado en línea equivalente, ya que el optimizador tiene un conocimiento integrado de cómo se comportan numerosos intrínsecos, por lo que pueden estar disponibles algunas optimizaciones de las que no se dispone cuando se utiliza el código ensamblado en línea.  Además, el optimizador puede expandir el intrínseco de forma diferente, alinear los búferes de forma diferente o realizar otros ajustes según el contexto y los argumentos de la llamada.  
  
 El uso de intrínsecos afecta a la portabilidad del código, ya que los intrínsecos que están disponibles en Visual C\+\+ podrían no estar disponibles si el código se compila con otros compiladores, y algunos intrínsecos que podrían estar disponibles para ciertas arquitecturas de destino no están disponibles para todas las arquitecturas.  Sin embargo, los intrínsecos son generalmente mucho más portátiles que el ensamblado en línea.  Los intrínsecos son necesarios en las arquitecturas de 64 bits donde no se admite el ensamblado en línea.  
  
 Algunos intrínsecos, como `__assume` y `__ReadWriteBarrier`, proporcionan información al compilador, lo que afecta al comportamiento del optimizador.  
  
 Algunos intrínsecos están disponibles solo como tal, mientras que otros están disponibles en implementaciones de intrínseco y de función.  Puede indicarle al compilador que utilice la implementación de intrínseco de dos maneras, en función de si desea habilitar solo funciones específicas o de si desea habilitar todos los intrínsecos.  La primera manera consiste en utilizar `#pragma intrinsic(``intrinsic-function-name-list``)`.  La directiva pragma puede utilizarse para especificar un solo intrínseco o varios intrínsecos separados por comas.  La segunda manera consiste en utilizar la opción del compilador [\/Oi \(generar funciones intrínsecas\)](../build/reference/oi-generate-intrinsic-functions.md), que habilita todos los intrínsecos de una plataforma determinada.  En **\/Oi**, utilice `#pragma function(``intrinsic-function-name-list``)` para forzar el uso de una llamada de función en lugar de un intrínseco.  Si la documentación de un intrínseco específico percibe que la rutina solo está disponible como intrínseco, se utiliza la implementación de intrínseco independientemente de si se especifica **\/Oi** o `#pragma intrinsic` .  En todos los casos, **\/Oi** o `#pragma intrinsic` permiten, sin forzarlo, que el optimizador utilice el intrínseco.  El optimizador todavía puede llamar a la función.  
  
 Algunas funciones de biblioteca estándar de C o C\+\+ están disponibles en las implementaciones de intrínseco de algunas arquitecturas.  Al llamar a una función CRT, se utiliza la implementación de intrínseco si se especifica **\/Oi** en la línea de comandos.  
  
 Un archivo de encabezado, \<intrin.h\>, está disponible para declarar los prototipos de las funciones intrínsecas comunes.  Los intrínsecos específicos del fabricante están disponibles en los archivos de encabezado \<immintrin.h\> y \<ammintrin.h\>.  Además, algunos encabezados de Windows declaran funciones que se asignan a un intrínseco del compilador.  
  
 En las secciones siguientes se enumeran todos los intrínsecos que están disponibles en varias arquitecturas.  Para obtener más información acerca de cómo funcionan los intrínsecos en un procesador de destino determinado, consulte la documentación de referencia del fabricante.  
  
-   [Intrínsecos ARM](../intrinsics/arm-intrinsics.md)  
  
-   [Lista de intrínsecos de x86](../intrinsics/x86-intrinsics-list.md)  
  
-   [x64 \(amd64\) \(Lista de intrínsecos\)](../intrinsics/x64-amd64-intrinsics-list.md)  
  
-   [Intrínsecos disponibles en las arquitecturas Todo](../intrinsics/intrinsics-available-on-all-architectures.md)  
  
-   [Lista alfabética de funciones intrínsecas](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)  
  
## Vea también  
 [ARM Assembler Reference](../assembler/arm/arm-assembler-reference.md)   
 [Microsoft Macro Assembler Reference](../assembler/masm/microsoft-macro-assembler-reference.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)