---
title: "no_auto_exclude | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_auto_exclude"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_auto_exclude (atributo)"
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# no_auto_exclude
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Deshabilita la exclusión automática.  
  
## Sintaxis  
  
```  
no_auto_exclude  
```  
  
## Comentarios  
 Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos.  `#import` intenta evitar varios errores de definición mediante la exclusión automática de dichos elementos.  En este caso, se emite [Advertencia del compilador \(nivel 3\) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) para que se excluya cada elemento.  Se puede deshabilitar esta exclusión automática con este atributo.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)