---
title: "Declaraciones y definiciones de C | Microsoft Docs"
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
ms.assetid: 575f0c9b-5554-4346-be64-b2129ca9227f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Declaraciones y definiciones de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una “declaración” establece una asociación entre una variable, función o tipo determinado y sus atributos.  En [Información general de declaraciones](../c-language/overview-of-declarations.md) se proporciona la sintaxis ANSI de la `declaration` no terminal.  Una declaración también especifica dónde y cuándo se puede acceder a un identificador \(la "vinculación" de un identificador\).  Vea [Duración, ámbito, visibilidad y vinculación](../c-language/lifetime-scope-visibility-and-linkage.md) para obtener información sobre la vinculación.  
  
 Una “definición” de una variable establece las mismas asociaciones que una declaración pero también hace que se asigne almacenamiento a la variable.  
  
 Por ejemplo, las funciones `main`, `find` y `count` y las variables `var` y `val` se definen en un archivo de código fuente, en este orden:  
  
```  
int main() {}  
  
int var = 0;  
double val[MAXVAL];  
char find( fileptr ) {}  
int count( double f ) {}  
```  
  
 Las variables `var` y `val` se pueden utilizar en las funciones `find` y `count`; no se requieren más declaraciones.  Pero estos nombres no son visibles \(no se puede acceder a ellos\) en `main`.  
  
## Vea también  
 [Archivos de código fuente y programas de origen](../c-language/source-files-and-source-programs.md)