---
title: "is_error_code_enum (Clase) | Microsoft Docs"
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
  - "system_error/std::is_error_code_enum"
  - "std.is_error_code_enum"
  - "is_error_code_enum"
  - "std::is_error_code_enum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_error_code_enum (clase)"
ms.assetid: cee5be2d-7c20-4cec-a352-1ab8b7d32601
caps.latest.revision: 15
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_error_code_enum (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un predicado de tipo que comprueba la enumeración de [error\_code](../standard-library/error-code-class.md) .  
  
## Sintaxis  
  
```  
template<_Enum>  
    class is_error_code_enum;  
```  
  
## Comentarios  
 Una instancia de este [predicado de tipo](../standard-library/type-traits.md) es true si el tipo `_Enum` es un valor de enumeración adecuada para almacenarla en un objeto de `error_code`escrito.  
  
 Se permite agregar especializaciones a este tipo para tipos definidos por el usuario.  
  
## Requisitos  
 **Encabezado:** \<system\_error\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [\<system\_error\>](../standard-library/system-error.md)