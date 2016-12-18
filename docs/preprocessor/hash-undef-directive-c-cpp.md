---
title: "#undef (Directiva) (C/C++) | Microsoft Docs"
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
  - "#undef"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#undef (directiva)"
  - "preprocesador, directivas"
  - "undef (directiva) (#undef)"
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #undef (Directiva) (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Quita \(anula la definición de\) un nombre creado previamente con `#define`.  
  
## Sintaxis  
  
```  
  
#undef   
identifier  
  
```  
  
## Comentarios  
 La directiva `#undef` quita la definición actual de *identifier*.  Por consiguiente, el preprocesador omite las apariciones posteriores de *identifier*.  Para quitar una definición de macro utilizando `#undef`, solo hay que proporcionar el *identifier* de macro; no hay que proporcionar una lista de parámetros.  
  
 También puede aplicar la directiva `#undef` a un identificador que no tenga ninguna definición anterior.  De este modo se garantiza que el identificador no esté definido.  El reemplazo de macros no se realiza dentro de instrucciones `#undef`.  
  
 La directiva `#undef` se empareja normalmente con una directiva `#define` para crear una región en un programa de origen en el que un identificador tiene un significado especial.  Por ejemplo, una función específica del programa de origen puede utilizar constantes de manifiesto para definir valores específicos del entorno que no afecten al resto del programa.  La directiva `#undef` también funciona con la directiva `#if` para controlar la compilación condicional del programa de origen.  Vea [Directivas \#if, \#elif, \#else y \#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) para obtener más información.  
  
 En el ejemplo siguiente, la directiva `#undef` quita las definiciones de una constante simbólica y una macro.  Observe que solo se proporciona el identificador de la macro.  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Específicos de Microsoft**  
  
 Las macros pueden no definirse desde la línea de comandos mediante la opción \/U seguida de los nombres de las macros que no se definen.  El efecto de emitir este comando equivale a una secuencia de instrucciones `#undef` *macro\-name* al principio del archivo.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)