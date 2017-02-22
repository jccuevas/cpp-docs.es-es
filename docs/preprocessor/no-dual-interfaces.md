---
title: "no_dual_interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_dual_interfaces"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_dual_interfaces (atributo)"
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# no_dual_interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.  
  
## Sintaxis  
  
```  
no_dual_interfaces  
```  
  
## Comentarios  
 Normalmente, el contenedor llamará al método a través de la tabla de funciones virtuales para la interfaz.  Con `no_dual_interfaces`, el contenedor llama en su lugar a **IDispatch::Invoke** para invocar el método.  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)