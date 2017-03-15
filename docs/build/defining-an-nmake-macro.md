---
title: "Definir una macro NMAKE | Microsoft Docs"
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
  - "definir macros de NMAKE"
  - "macros, NMAKE"
  - "NMAKE (macros), definir"
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Definir una macro NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
macroname=string  
```  
  
## Comentarios  
 El argumento *macroname* es una combinación de letras, dígitos y caracteres de subrayado \(\_\) que puede tener hasta 1.024 caracteres y distingue entre mayúsculas y minúsculas.  Puede contener una macro a la que se ha llamado.  Si consta en su totalidad de una macro a la que se ha llamado, ésta no puede ser nula o no estar definida.  
  
 El argumento `string` puede ser cualquier secuencia con varios caracteres o ninguno.  Una cadena nula no contiene caracteres; sólo puede contener espacios o tabulaciones.  El argumento `string` puede contener una llamada de macro.  
  
## ¿Sobre qué desea obtener más información?  
 [Caracteres especiales en las macros](../build/special-characters-in-macros.md)  
  
 [Macros Null y no definidas](../build/null-and-undefined-macros.md)  
  
 [Dónde definir macros](../build/where-to-define-macros.md)  
  
 [La precedencia en las definiciones de macro](../build/precedence-in-macro-definitions.md)  
  
## Vea también  
 [Las macros y NMAKE](../build/macros-and-nmake.md)