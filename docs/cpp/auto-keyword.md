---
title: "auto (Palabra clave) | Microsoft Docs"
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
  - "auto"
  - "auto_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "auto (palabra clave)"
  - "clase de almacenamiento automática, auto (palabra clave)"
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto (Palabra clave)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `auto` es un especificador de declaración.  Sin embargo, C\+\+ estándar define un significado original y otro revisado para esta palabra clave.  En las versiones anteriores a [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)], la palabra clave `auto` declara una variable en la clase de almacenamiento *automático*; es decir, una variable que tiene una duración local.  A partir de [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)], la palabra clave `auto` declara un variable cuyo tipo se deduce de la expresión de inicialización de su declaración.  La opción del compilador [\/Zc: auto &#91;\-&#93;](../build/reference/zc-auto-deduce-variable-type.md) controla el significado de la palabra clave `auto`.  
  
## Sintaxis  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## Comentarios  
 La definición de la palabra clave `auto` cambia en el lenguaje de programación C\+\+, pero no en el lenguaje de programación C.  
  
 En los temas siguientes se describe la palabra clave `auto` y la opción del compilador correspondiente:  
  
-   En [auto](../cpp/auto-cpp.md) se describe la nueva definición de la palabra clave `auto`.  
  
-   En [auto \(Palabra clave\) \(Especificador de clase de almacenamiento\)](http://msdn.microsoft.com/es-es/c7d0cecf-393d-4058-a6e6-b39e31d9edb0) se describe la definición original de la palabra clave `auto`.  
  
-   En [\/Zc:auto \(Deducir tipo de variable\)](../build/reference/zc-auto-deduce-variable-type.md) se describe la opción del compilador que indica al compilador qué definición de palabra clave `auto` debe utilizar.  
  
## Vea también  
 [\(NOTINBUILD\)Storage\-Class Specifiers](http://msdn.microsoft.com/es-es/10b3d22d-cb40-450b-994b-08cf9a211b6c)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)