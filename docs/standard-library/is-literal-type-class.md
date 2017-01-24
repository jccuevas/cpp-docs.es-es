---
title: "is_literal_type (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_literal_type"
  - "std.is_literal_type"
  - "std::is_literal_type"
  - "type_traits/std::is_literal_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_literal_type"
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
caps.latest.revision: 12
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_literal_type (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Prueba si un tipo se puede utilizar como un `constexpr` variable o ser construido, utilizado por o devueltas desde `constexpr` funciones.  
  
## Sintaxis  
  
```  
template <class T>  
    struct is_literal_type;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `T` es un *tipo literal*, de lo contrario, contiene false. Un tipo de literal es `void`, un tipo escalar, un tipo de referencia, una matriz de tipo de literal o un tipo de clase literal. Un tipo de clase literal es un tipo de clase que tiene un destructor trivial, es un tipo de agregado o tiene al menos un no\-move, copy no `constexpr` constructor y todas sus clases base y los miembros de datos no estáticos son tipos literales no volátil. Aunque el tipo de un literal es siempre un tipo literal, el concepto de tipo de literal incluye todo lo que el compilador puede evaluar como un `constexpr` en tiempo de compilación.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)