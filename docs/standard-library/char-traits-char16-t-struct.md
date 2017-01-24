---
title: "char_traits&lt;char16_t&gt; (Struct) | Microsoft Docs"
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
  - "std::char_traits<char16_t>"
  - "std.char_traits<char16_t>"
  - "char_traits<char16_t>"
  - "string/std::char_traits<char16_t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<char16_t> (clase)"
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits&lt;char16_t&gt; (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Struct que es una especialización de struct **char\_traits\<CharType\>** de plantilla a un elemento de `char16_t`escrito.  
  
## Sintaxis  
  
```  
template<> struct char_traits<char16_t>;  
```  
  
## Comentarios  
 Especialización permite que struct se aprovecha de las funciones de biblioteca que manipulan objetos de tipo `char16_t`.  
  
## Requisitos  
 **Encabezado:** \<string\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<string\>](../standard-library/string.md)   
 [char\_traits \(Struct\)](../standard-library/char-traits-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)