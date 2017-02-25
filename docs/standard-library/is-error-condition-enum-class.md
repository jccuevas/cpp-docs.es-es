---
title: "is_error_condition_enum (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::is_error_condition_enum"
  - "std.is_error_condition_enum"
  - "is_error_condition_enum"
  - "system_error/std::is_error_condition_enum"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_error_condition_enum (clase)"
ms.assetid: 752bb87a-c61c-4304-9254-5aaf228b59c0
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# is_error_condition_enum (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa un predicado de tipo que comprueba la enumeración de [error\_condition](../standard-library/error-condition-class.md) .  
  
## Sintaxis  
  
```  
template<_Enum>  
    class is_error_condition_enum;  
```  
  
## Comentarios  
 Una instancia de este [predicado de tipo](../standard-library/type-traits.md) es true si el tipo `_Enum` es un valor de enumeración adecuada para almacenarla en un objeto de `error_condition`escrito.  
  
 Se permite agregar especializaciones a este tipo para tipos definidos por el usuario.  
  
## Requisitos  
 **Encabezado:** \<system\_error\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [\<system\_error\>](../standard-library/system-error.md)