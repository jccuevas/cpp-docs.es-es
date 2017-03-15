---
title: "inject_statement | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "inject_statement"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inject_statement (atributo)"
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# inject_statement
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Inserta el argumento como texto original en el encabezado de la biblioteca de tipos.  
  
## Sintaxis  
  
```  
inject_statement("source_text")  
```  
  
#### Parámetros  
 `source_text`  
 Texto original que se inserta en el archivo de encabezado de la biblioteca de tipos.  
  
## Comentarios  
 El texto se coloca al principio de la declaración de espacio de nombres que incluye el contenido de la biblioteca de tipos en el archivo de encabezado.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)