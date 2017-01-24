---
title: "exclude (#import) | Microsoft Docs"
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
  - "exclude"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "exclude (atributo)"
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# exclude (#import)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Excluye elementos de los archivos de encabezado de la biblioteca de tipos que se generan.  
  
## Sintaxis  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
#### Parámetros  
 `Name1`  
 Primer elemento que se excluirá.  
  
 `Name2`  
 Segundo elemento que se excluirá \(si es necesario\).  
  
## Comentarios  
 Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos.  Este atributo puede tomar cualquier número de argumentos, cada uno de los cuales es un elemento de nivel superior de la biblioteca de tipos que se va a excluir.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)