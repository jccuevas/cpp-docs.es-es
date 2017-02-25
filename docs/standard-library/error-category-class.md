---
title: "error_category (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::error_category"
  - "system_error/std::error_category"
  - "error_category"
  - "std.error_category"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_category (clase)"
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# error_category (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa la base común de abstracta para los objetos que describe una categoría de códigos de error.  
  
## Sintaxis  
  
```  
class error_category;  
```  
  
## Comentarios  
 Implementan dos objetos predefinidos `error_category`: [generic\_category](../Topic/generic_category.md) y [system\_category](../Topic/system_category.md).  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[value\_type](../Topic/error_category::value_type.md)|Tipo que representa el valor del código de error almacenado.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[default\_error\_condition](../Topic/error_category::default_error_condition.md)|Almacena el valor de código de error para un objeto de la condición de error.|  
|[equivalent](../Topic/error_category::equivalent.md)|Devuelve un valor que especifica si los objetos de error son equivalentes.|  
|[message](../Topic/error_category::message.md)|Devuelve el nombre del código de error especificado.|  
|[name](../Topic/error_category::name.md)|Devuelve el nombre de la categoría.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\=\=](../Topic/error_category::operator==.md)|Comprueba la igualdad entre `error_category` objetos.|  
|[operator\!\=](../Topic/error_category::operator!=.md)|Comprueba la desigualdad entre `error_category` objetos.|  
|[operator\<](../Topic/error_category::operator%3C.md)|Comprueba si el [error\_category](../standard-library/error-category-class.md) objeto es menor que el `error_category` objeto pasado para la comparación.|  
  
## Requisitos  
 **Encabezado:** \<system\_error\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<system\_error\>](../standard-library/system-error.md)