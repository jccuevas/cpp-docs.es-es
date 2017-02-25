---
title: "error_condition (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "system_error/std::error_condition"
  - "std::error_condition"
  - "error_condition"
  - "std.error_condition"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "error_condition (clase)"
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# error_condition (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa los códigos de error definidos por el usuario.  
  
## Sintaxis  
  
```  
class error_condition;  
```  
  
## Comentarios  
 Un objeto de `error_condition` tipo almacena un valor de código de error y un puntero a un objeto que representa [category](../standard-library/error-category-class.md) de los códigos de error utilizados para los errores definidos por el usuario designados.  
  
### Constructores  
  
|||  
|-|-|  
|[error\_condition](../Topic/error_condition::error_condition.md)|Construye un objeto de tipo `error_condition`.|  
  
### Typedefs  
  
|||  
|-|-|  
|[value\_type](../Topic/error_condition::value_type.md)|Un tipo que representa el valor de código de error almacenado.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[assign](../Topic/error_condition::assign.md)|Asigna un valor y una categoría de código de error a una condición de error.|  
|[categoría](../Topic/error_condition::category.md)|Devuelve la categoría de error.|  
|[clear](../Topic/error_condition::clear.md)|Borra el valor y la categoría de código de error.|  
|[message](../Topic/error_condition::message.md)|Devuelve el nombre del código de error.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\=\=](../Topic/error_condition::operator==.md)|Comprueba la igualdad entre los objetos de `error_condition` .|  
|[operator\!\=](../Topic/error_condition::operator!=.md)|Comprueba la desigualdad entre los objetos de `error_condition` .|  
|[':?'.\<](../Topic/error_condition::operator%3C.md)|Comprueba si el objeto de `error_condition` es menor que el objeto de `error_code` pasado para la comparación.|  
|[operator\=](../Topic/error_condition::operator=.md)|Asigna un nuevo valor de enumeración en el objeto de `error_condition` .|  
|[bool de operador](../Topic/error_condition::operator%20bool.md)|Convierte una variable de `error_condition`escrito.|  
  
## Requisitos  
 **Encabezado:** \<system\_error\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [error\_category \(Clase\)](../standard-library/error-category-class.md)   
 [\<system\_error\>](../standard-library/system-error.md)