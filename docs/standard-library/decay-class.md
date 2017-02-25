---
title: "decay (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "decay"
  - "std.tr1.decay"
  - "std::tr1::decay"
  - "std.decay"
  - "std::decay"
  - "type_traits/std::decay"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "decay (clase) [TR1]"
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# decay (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera el tipo tal y como se pasan por valor. Crea el tipo sin referencia, no const no volátil, o convierte un puntero al tipo de una función o un tipo de matriz.  
  
## Sintaxis  
  
```  
template<class T>  
    struct decay;  
  
template<class T> using decay_t = typename decay<T>::type;  
```  
  
#### Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## Comentarios  
 Utilice la plantilla decay para generar el tipo resultante como si el tipo se pasa por valor como argumento. La definición de tipo de miembro de clase de plantilla `type` contiene un tipo modificado que se define en las siguientes fases:  
  
-   El tipo `U` se define como `remove_reference<T>::type`.  
  
-   Si `is_array<U>::value` es true, el tipo modificado `type` es `remove_extent<U>::type *`.  
  
-   De lo contrario, si `is_function<U>::value` es true, el tipo modificado `type` es `add_pointer<U>::type`.  
  
-   De lo contrario, el tipo modificado `type` es `remove_cv<U>::type`.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)