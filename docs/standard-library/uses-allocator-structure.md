---
title: "uses_allocator (Estructura) | Microsoft Docs"
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
  - "future/std::uses_allocator"
dev_langs: 
  - "C++"
ms.assetid: c418f002-62e9-4806-b70c-41c663cae583
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# uses_allocator (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especializaciones que siempre son true.  
  
## Sintaxis  
  
```  
template<class Ty, class Alloc>  
struct uses_allocator<promise<Ty>, Alloc> : true_type;  
template<class Ty, class Alloc>  
struct uses_allocator<packaged_task<Ty>, Alloc> : true_type;  
```  
  
## Requisitos  
 **Encabezado:** future  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)