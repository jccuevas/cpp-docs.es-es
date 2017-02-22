---
title: "is_trivially_copy_constructible (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_trivially_copy_constructible"
  - "std.is_trivially_copy_constructible"
  - "std::is_trivially_copy_constructible"
  - "type_traits/std::is_trivially_copy_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_copy_constructible"
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# is_trivially_copy_constructible (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un constructor de copia trivial.  
  
## Sintaxis  
  
```  
template<class T>  
    struct is_trivially_copy_constructible;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` es una clase que tiene un constructor de copias trivial; en caso contrario, es false.  
  
 Un constructor de copias para una clase `T` es trivial si se declara implícitamente, la clase `T` no tiene funciones virtuales o bases virtuales, todas las bases de directas de clase `T` tienen constructores de copia trivial, las clases de todos los miembros de datos no estáticos de tipo de clase tienen constructores de copia trivial y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de copia trivial.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)