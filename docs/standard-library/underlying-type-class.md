---
title: "underlying_type (clase) | Microsoft Docs"
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
  - "underlying_type"
  - "std.underlying_type"
  - "std::underlying_type"
  - "type_traits/std::underlying_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "underlying_type"
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# underlying_type (clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera el tipo entero subyacente para un tipo de enumeración.  
  
## Sintaxis  
  
```  
template <class T>  
    struct underlying_type;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## Comentarios  
 El `type` el tipo entero subyacente de nombres de miembro typedef de la clase de plantilla `T`, cuando `T` es un tipo de enumeración, de lo contrario, no hay ninguna definición de tipos de miembro `type`.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)