---
title: "raw_method_prefix | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "raw_method_prefix"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "raw_method_prefix (atributo)"
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# raw_method_prefix
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Especifica otro prefijo para evitar conflictos de nombres.  
  
## Sintaxis  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### Parámetros  
 `Prefix`  
 El prefijo que se va a usar.  
  
## Comentarios  
 Las propiedades y métodos de bajo nivel se exponen mediante las funciones miembro designadas con un prefijo predeterminado de **raw\_** para evitar conflictos de nombres con funciones miembro de control de errores de alto nivel.  
  
> [!NOTE]
>  Los efectos del atributo `raw_method_prefix` no se modificarán debido a la presencia del atributo [raw\_interfaces\_only](#_predir_raw_interfaces_only).  `raw_method_prefix` tiene siempre prioridad sobre `raw_interfaces_only` cuando se especifica un prefijo.  Si ambos atributos se utilizan en la misma instrucción `#import`, se usa el prefijo especificado por el atributo `raw_method_prefix`.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)