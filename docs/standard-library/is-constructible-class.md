---
title: "is_constructible (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_constructible"
  - "std.is_constructible"
  - "std::is_constructible"
  - "type_traits/std::is_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_constructible"
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# is_constructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si un tipo es construir mediante cuando se utilizan tipos de argumento especificados.  
  
## Sintaxis  
  
```  
template <class T, class... Args>  
    struct is_constructible;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
 `Args`  
 Los tipos de argumento para que coincida con un constructor de `T`.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es puede construir mediante los tipos de argumento `Args`, de lo contrario, contiene false. Tipo `T` puede construirse si la definición de variable `T t(std::declval<Args>()...);` es correcto. Ambos `T` y todos los tipos de `Args` debe ser de tipos completos, `void`, o matrices de límite desconocido.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)