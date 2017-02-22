---
title: "Clase is_nothrow_default_constructible | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_nothrow_default_constructible"
  - "std.is_nothrow_default_constructible"
  - "std::is_nothrow_default_constructible"
  - "type_traits/std::is_nothrow_default_constructible"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_nothrow_default_constructible"
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# Clase is_nothrow_default_constructible
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si el tipo tiene un constructor predeterminado que no produce excepciones.  
  
## Sintaxis  
  
```  
template<class Ty>  
    struct is_nothrow_default_constructible;  
```  
  
#### Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` tiene un constructor predeterminado nothrow; en caso contrario, contiene false.  Una instancia del predicado de tipo es equivalente a `is_nothrow_constructible<Ty>`.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)