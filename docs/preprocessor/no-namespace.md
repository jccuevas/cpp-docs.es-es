---
title: "no_namespace | Microsoft Docs"
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
  - "no_namespace"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "no_namespace (atributo)"
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# no_namespace
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Especifica que el compilador no genera el espacio de nombres.  
  
## Sintaxis  
  
```  
no_namespace  
```  
  
## Comentarios  
 El contenido de la biblioteca de tipos en el archivo de encabezado `#import` se define normalmente en un espacio de nombres.  El nombre del espacio de nombres se especifica en la instrucción **library** del archivo IDL original.  Si se especifica el atributo `no_namespace`, el compilador no genera este espacio de nombres.  
  
 Si desea utilizar otro espacio de nombres, use el atributo [rename\_namespace](../preprocessor/rename-namespace.md) en su lugar.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)