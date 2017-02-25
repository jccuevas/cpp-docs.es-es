---
title: "embedded_idl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "embedded_idl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "embedded_idl (atributo)"
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# embedded_idl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Especifica que la biblioteca de tipos se escriba en el archivo .tlh, conservando el código generado por el atributo.  
  
## Sintaxis  
  
```  
embedded_idl[("param")]  
```  
  
#### Parámetros  
 `param`  
 Puede ser uno de dos valores:  
  
-   emitidl: la información de tipo importada de typelib estará presente en el archivo IDL generado para el proyecto con atributos.  Este es el valor predeterminado y estará en vigor si no se especifica un parámetro para `embedded_idl`.  
  
-   no\_emitidl: la información de tipo importada de typelib no estará presente en el archivo IDL generado para el proyecto con atributos.  
  
## Ejemplo  
  
```  
// import_embedded_idl.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib2")];  
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")  
```  
  
## Comentarios  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)