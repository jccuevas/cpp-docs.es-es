---
title: "conditional (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::tr1::conditional"
  - "std.tr1.conditional"
  - "conditional"
  - "std.conditional"
  - "std::conditional"
  - "type_traits/std::conditional"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conditional (clase) [TR1]"
  - "conditional"
ms.assetid: ece9f539-fb28-4e26-a79f-3264bc984493
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# conditional (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Selecciona uno de dos tipos en función de la condición especificada.  
  
## Sintaxis  
  
```  
template <bool B, class T1, class T2>  
    struct conditional;  
  
template <bool _Test, class _T1, class _T2>  
    using conditional_t = typename conditional<_Test, _T1, _T2>::type;  
```  
  
#### Parámetros  
 `B`  
 Valor que determina el tipo seleccionado.  
  
 `T1`  
 Resultado del tipo cuando B es true.  
  
 `T2`  
 Resultado del tipo cuando B es false.  
  
## Comentarios  
 La definición de tipo de miembro de plantilla `conditional<B, T1, T2>::type` se evalúa como `T1` cuando `B` se evalúa como `true`, y se evalúa como `T2` cuando `B` se evalúa como `false`.  
  
## Requisitos  
 **Encabezado:** \<type\_traits\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<type\_traits\>](../standard-library/type-traits.md)