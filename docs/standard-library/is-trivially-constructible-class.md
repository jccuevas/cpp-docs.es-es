---
title: "is_trivially_constructible (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "is_trivially_constructible"
  - "std.is_trivially_constructible"
  - "std::is_trivially_constructible"
  - "type_traits/std::is_trivially_constructible"
dev_langs: 
  - "C++"
  - "c++"
helpviewer_keywords: 
  - "is_trivially_constructible"
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_trivially_constructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si es muy puede construir un tipo cuando se utilizan tipos de argumento especificados.  
  
## Sintaxis  
  
```  
template <class T, class... Args>  
    struct is_trivially_constructible;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
 `Args`  
 Los tipos de argumento para que coincida con un constructor de `T`.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es trivial puede construir mediante los tipos de argumento `Args`, de lo contrario, contiene false. Tipo `T` muy construirse si la definición de variable `T t(std::declval<Args>()...);` es correcto y se sabe que llame a ninguna operación no trivial. Ambos `T` y todos los tipos de `Args` debe ser de tipos completos, `void`, o matrices de límite desconocido.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)