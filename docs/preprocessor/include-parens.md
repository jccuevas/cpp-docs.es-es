---
title: "include() | Microsoft Docs"
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
  - "include()"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "include() (atributo)"
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# include()
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Deshabilita la exclusión automática.  
  
## Sintaxis  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### Parámetros  
 `Name1`  
 Primer elemento que se incluirá forzosamente.  
  
 `Name2`  
 Segundo elemento que se incluirá forzosamente \(si es necesario\).  
  
## Comentarios  
 Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos.  `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos.  Si se han excluido elementos, como se indica en [Advertencia del compilador \(nivel 3\) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), y no debería haberse producido este hecho, este atributo se puede utilizar para deshabilitar la exclusión automática.  Este atributo puede tomar cualquier número de argumentos, siendo cada uno el nombre del elemento de la biblioteca de tipos que se incluirá.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)