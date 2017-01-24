---
title: "no_implementation | Microsoft Docs"
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
  - "no_implementation"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "no_implementation (atributo)"
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# no_implementation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Suprime la generación del encabezado .tli, que contiene las implementaciones de las funciones miembro de contenedor.  
  
## Sintaxis  
  
```  
no_implementation  
```  
  
## Comentarios  
 Si se especifica este atributo, el encabezado.tlh, con las declaraciones para exponer elementos de la biblioteca de tipos, se generará sin una instrucción `#include` para incluir el archivo de encabezado .tli.  
  
 Este atributo se usa junto con [implementation\_only](../preprocessor/implementation-only.md).  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)