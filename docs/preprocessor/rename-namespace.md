---
title: "rename_namespace | Microsoft Docs"
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
  - "rename_namespace"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "rename_namespace (atributo)"
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rename_namespace
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Cambia el espacio de nombres que incluye el contenido de la biblioteca de tipos.  
  
## Sintaxis  
  
```  
rename_namespace("NewName")  
```  
  
#### Parámetros  
 `NewName`  
 Nuevo nombre del espacio de nombres.  
  
## Comentarios  
 Toma un único argumento, *NewName*, que especifica el nuevo nombre del espacio de nombres.  
  
 Para quitar el espacio de nombres, utilice el atributo [no\_namespace](../preprocessor/no-namespace.md) en su lugar.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)