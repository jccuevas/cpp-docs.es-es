---
title: "char_traits&lt;wchar_t&gt; (Struct) | Microsoft Docs"
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
  - "std.char_traits<wchar_t>"
  - "char_traits<wchar_t>"
  - "string/std::char_traits<wchar_t>"
  - "std::char_traits<wchar_t>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits<wchar_t> (clase)"
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
caps.latest.revision: 21
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits&lt;wchar_t&gt; (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una clase que es una especialización de struct **char\_traits\<CharType\>** de plantilla a un elemento de `wchar_t`escrito.  
  
## Sintaxis  
  
```  
template<> struct char_traits<wchar_t>;  
```  
  
## Comentarios  
 Especialización permite que struct se aprovecha de las funciones de biblioteca que manipulan objetos de este tipo `wchar_t`.  
  
## Requisitos  
 **Encabezado:** \<string\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [char\_traits \(Struct\)](../standard-library/char-traits-struct.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)