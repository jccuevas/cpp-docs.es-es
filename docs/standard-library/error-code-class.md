---
title: "error_code (Clase) | Microsoft Docs"
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
  - "error_code"
  - "std.error_code"
  - "std::error_code"
  - "system_error/std::error_code"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_code (clase)"
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
caps.latest.revision: 17
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# error_code (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa los errores del sistema de bajo nivel que son implementación\- concretos.  
  
## Sintaxis  
  
```  
class error_code;  
```  
  
## Comentarios  
 Un objeto del tipo de clase de `error_code` almacena un valor de código de error y un puntero a un objeto que representa [category](../standard-library/error-category-class.md) de los códigos de error que describen errores del sistema de bajo nivel designados.  
  
### Constructores  
  
|||  
|-|-|  
|[error\_code](../Topic/error_code::error_code.md)|Construye un objeto de tipo `error_code`.|  
  
### Typedefs  
  
|||  
|-|-|  
|[value\_type](../Topic/error_code::value_type.md)|Un tipo que representa el valor de código de error almacenado.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[assign](../Topic/error_code::assign.md)|Asigna un valor y una categoría de código de error un código de error.|  
|[categoría](../Topic/error_code::category.md)|Devuelve la categoría de error.|  
|[clear](../Topic/error_code::clear.md)|Borra el valor y la categoría de código de error.|  
|[default\_error\_condition](../Topic/error_code::default_error_condition.md)|Devuelve la condición de error predeterminada.|  
|[message](../Topic/error_code::message.md)|Devuelve el nombre del código de error.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\=\=](../Topic/error_code::operator==.md)|Comprueba la igualdad entre los objetos de `error_code` .|  
|[operator\!\=](../Topic/error_code::operator!=.md)|Comprueba la desigualdad entre los objetos de `error_code` .|  
|[':?'.\<](../Topic/error_code::operator%3C.md)|Comprueba si el objeto de `error_code` es menor que el objeto de `error_code` pasado para la comparación.|  
|[operator\=](../Topic/error_code::operator=.md)|Asigna un nuevo valor de enumeración en el objeto de `error_code` .|  
|[bool de operador](../Topic/error_code::operator%20bool.md)|Convierte una variable de `error_code`escrito.|  
  
## Requisitos  
 **Encabezado:** \<system\_error\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [error\_category \(Clase\)](../standard-library/error-category-class.md)   
 [\<system\_error\>](../standard-library/system-error.md)