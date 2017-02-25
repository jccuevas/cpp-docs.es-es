---
title: "is_trivially_default_constructible (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_trivially_default_constructible"
  - "std.is_trivially_default_constructible"
  - "std::is_trivially_default_constructible"
  - "type_traits/std::is_trivially_default_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_trivially_default_constructible"
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# is_trivially_default_constructible (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un constructor predeterminado trivial.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct  is_trivially_default_constructible;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo es true si el tipo `Ty` es una clase que tiene un constructor trivial; en caso contrario, es false.  
  
 Un constructor predeterminado para una clase `Ty` es trivial si:  
  
-   es un constructor predeterminado declarado implícitamente  
  
-   la clase `Ty` no tiene ninguna función virtual  
  
-   la clase `Ty` no tiene ninguna base virtual  
  
-   todas las bases directas de la clase `Ty` tienen constructores triviales  
  
-   las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores triviales  
  
-   las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores triviales  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)