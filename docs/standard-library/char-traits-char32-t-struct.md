---
title: "char_traits&lt;char32_t&gt; (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "string/std::char_traits<char_32t>"
  - "char_traits<char32_t>"
  - "std.char_traits<char_32t>"
  - "std::char_traits<char_32t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<char32_t> (clase)"
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# char_traits&lt;char32_t&gt; (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Struct que es una especialización de struct **char\_traits\<CharType\>** de plantilla a un elemento de `char32_t`escrito.  
  
## Sintaxis  
  
```  
template<> struct char_traits<char32_t>;  
```  
  
## Comentarios  
 Especialización permite que struct se aprovecha de las funciones de biblioteca que manipulan objetos de este tipo `char32_t`.  
  
## Requisitos  
 **Encabezado:** \<string\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<string\>](../standard-library/string.md)   
 [char\_traits \(Struct\)](../standard-library/char-traits-struct.md)