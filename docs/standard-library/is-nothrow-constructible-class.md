---
title: "is_nothrow_constructible (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_nothrow_constructible"
  - "std.is_nothrow_constructible"
  - "std::is_nothrow_constructible"
  - "type_traits/std::is_nothrow_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_constructible"
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# is_nothrow_constructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Prueba si un tipo puede construirse y se conoce no se produce cuando se utilizan los tipos de argumento especificados.  
  
## Sintaxis  
  
```  
template <class T, class... Args>  
    struct is_nothrow_constructible;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
 `Args`  
 Los tipos de argumento para que coincida con un constructor de `T`.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es puede construir mediante los tipos de argumento en `Args`, y el compilador conoce el constructor no se iniciará; de lo contrario, contiene false. Tipo `T` puede construirse si la definición de variable `T t(std::declval<Args>()...);` es correcto. Ambos `T` y todos los tipos de `Args` debe ser de tipos completos, `void`, o matrices de límite desconocido.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)