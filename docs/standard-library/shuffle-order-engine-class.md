---
title: "shuffle_order_engine (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "shuffle_order_engine"
  - "std.tr1.shuffle_order_engine"
  - "tr1::shuffle_order_engine"
  - "tr1.shuffle_order_engine"
  - "std::tr1::shuffle_order_engine"
  - "random/std::tr1::shuffle_order_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "shuffle_order_engine (clase)"
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
caps.latest.revision: 17
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# shuffle_order_engine (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una secuencia aleatoria reordenando los valores que devuelve su motor base.  
  
## Sintaxis  
  
```  
template<class Engine, size_t K>  
class shuffle_order_engine;  
```  
  
#### Parámetros  
 `Engine`  
 El tipo de motor base.  
  
 `K`  
 **Tamaño de la tabla**. Número de elementos en el búfer \(tabla\).**Condición previa**: `0 < K`  
  
## Miembros  
  
||||  
|-|-|-|  
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|  
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|  
  
 Para obtener más información acerca de los miembros del motor, consulte [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 Esta clase de plantilla describe un *adaptador de motor* que genera valores reordenando los valores que su motor base devuelve. Cada constructor rellena la tabla interna con los valores `K` que el motor base ha devuelto y, cuando se solicita un valor, se selecciona un elemento aleatorio de la tabla.  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)