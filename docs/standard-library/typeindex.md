---
title: "&lt;typeindex&gt; | Microsoft Docs"
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
  - "<typeindex>"
dev_langs: 
  - "C++"
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
caps.latest.revision: 14
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;typeindex&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incluya el typeindex estándar \<de encabezado\> para definir una clase y hacer que admite la indización de objetos de la clase [type\_information](../cpp/type-info-class.md).  
  
## Sintaxis  
  
```cpp  
#include <typeindex>  
```  
  
## Comentarios  
 [hash \(Estructura\)](../standard-library/hash-structure.md) define `hash function` apropiadas para asignar valores de [type\_index](../standard-library/type-index-class.md) tipo a una distribución de valores de índice.  
  
 La clase de `type_index` contiene un puntero a un objeto de `type_info` de ayuda en la indización.  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)