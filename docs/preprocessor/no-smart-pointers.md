---
title: "no_smart_pointers | Microsoft Docs"
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
  - "no_search_pointers"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "no_smart_pointers (atributo)"
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# no_smart_pointers
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Suprime la creación de punteros inteligentes para todas las interfaces en la biblioteca de tipos.  
  
## Sintaxis  
  
```  
no_smart_pointers  
```  
  
## Comentarios  
 De forma predeterminada, cuando se utiliza `#import`, se obtiene una declaración de puntero inteligente para todas las interfaces de la biblioteca de tipos.  Estos punteros inteligentes son de tipo [\_com\_ptr\_t \(Clase\)](../cpp/com-ptr-t-class.md).  
  
 **Específicos de C\+\+: END**  
  
## Vea también  
 [\#import \(Atributos\)](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import \(Directiva\)](../preprocessor/hash-import-directive-cpp.md)