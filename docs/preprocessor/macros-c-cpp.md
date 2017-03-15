---
title: "Macros (C/C++) | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "preprocesador"
  - "preprocesador, macros"
  - "Visual C++, macros de preprocesador"
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Macros (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El preprocesamiento expande las macros en todas las líneas que no son directivas de preprocesador \(líneas que no tienen **\#** como primer carácter de espacio no en blanco\) y en partes de algunas directivas que no se omiten como parte de una compilación condicional. Las directivas de "compilación condicional" permiten suprimir la compilación de partes de un archivo de código fuente mediante la prueba de un identificador o una expresión de constante para determinar qué bloques de texto se pasan al compilador y qué bloques de texto se quitan del archivo de código fuente durante el preprocesamiento.  
  
 La directiva `#define` se utiliza normalmente para asociar identificadores significativos con constantes, palabras clave e instrucciones o expresiones usadas con frecuencia.  Los identificadores que representan constantes se denominan a veces "constantes simbólicas" o "constantes del manifiesto". Los identificadores que representan instrucciones o expresiones se denominan "macros". En esta documentación de preprocesador, solo se utiliza el término "macro".  
  
 Cuando el nombre de la macro se reconoce en el texto original del programa o en los argumentos de otros comandos de preprocesador determinados, se trata como una llamada a esa macro.  El nombre de la macro se reemplaza por una copia del cuerpo de la macro.  Si la macro acepta argumentos, los argumentos reales que siguen al nombre de la macro se sustituyen por los parámetros formales en el cuerpo de la macro.  El proceso de reemplazar la llamada a una macro por la copia procesada del cuerpo se denomina "expansión" de la llamada a la macro.  
  
 En la práctica, hay dos tipos de macros. Las macros "similares a objeto" no toman argumentos, mientras que las macros "similares a función" pueden definirse para aceptar argumentos de modo que parezcan y actúen como llamadas de función.  Dado que las macros no representan llamadas de función reales, a veces se puede acelerar la ejecución de los programas reemplazando las llamadas de función por macros. \(En C\+\+, las funciones insertadas suelen ser un método preferido\). Sin embargo, las macros pueden crear problemas si no se definen y utilizan con cuidado.  Puede que tenga que utilizar paréntesis en definiciones de macro con argumentos para conservar la prioridad correcta en una expresión.  Además, puede que las macros no controlen correctamente las expresiones con efectos secundarios.  Vea el ejemplo de `getrandom` en [La directiva \#define](../preprocessor/hash-define-directive-c-cpp.md) para obtener más información.  
  
 Una vez que haya definido una macro, no podrá volver a definirla en un valor diferente sin antes quitar la definición original.  Sin embargo, puede volver a definir la macro con exactamente la misma definición.  De este modo, la misma definición puede aparecer más de una vez en un programa.  
  
 La directiva \#**undef** quita la definición de una macro.  Una vez que haya quitado la definición, podrá volver a definir la macro en un valor diferente.  [La directiva \#define](../preprocessor/hash-define-directive-c-cpp.md) y [la directiva \#undef](../preprocessor/hash-undef-directive-c-cpp.md) analizan las directivas `#define` y `#undef`, respectivamente.  
  
 Para obtener más información, vea  
  
-   [Macros y C\+\+](../preprocessor/macros-and-cpp.md)  
  
-   [Macros variádicas](../preprocessor/variadic-macros.md)  
  
-   [Macros predefinidas](../preprocessor/predefined-macros.md)  
  
## Vea también  
 [Referencia del preprocesador de C\/C\+\+](../preprocessor/c-cpp-preprocessor-reference.md)