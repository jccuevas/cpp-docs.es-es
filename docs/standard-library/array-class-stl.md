---
title: "array (Clase, STL) | Microsoft Docs"
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
  - "array/std::tr1::array"
  - "std.tr1.array"
  - "array"
  - "std::tr1::array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "array (clase) [TR1]"
ms.assetid: fdfd43a5-b2b5-4b9e-991f-93bf10fb4293
caps.latest.revision: 22
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# array (Clase, STL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe un objeto que controla una secuencia de longitud `N` de elementos de tipo `Ty`.  La secuencia se almacena como matriz de `Ty`, que se encuentra en el objeto `array<Ty, N>`.  
  
## Sintaxis  
  
```  
template<class Ty, std::size_t N>  
    class array;  
```  
  
#### Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|`Ty`|El tipo de un elemento.|  
|`N`|Número de elementos.|  
  
## Miembros  
  
|||  
|-|-|  
|Definición de tipo|Descripción|  
|[array::const\_iterator](../Topic/array::const_iterator.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[array::const\_pointer](../Topic/array::const_pointer.md)|El tipo de un puntero constante a un elemento.|  
|[array::const\_reference](../Topic/array::const_reference.md)|El tipo de una referencia constante a un elemento.|  
|[array::const\_reverse\_iterator](../Topic/array::const_reverse_iterator.md)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[array::difference\_type](../Topic/array::difference_type.md)|El tipo de una distancia con signo entre dos elementos.|  
|[array::iterator](../Topic/array::iterator.md)|El tipo de un iterador para la secuencia controlada.|  
|[array::pointer](../Topic/array::pointer.md)|El tipo de un puntero a un elemento.|  
|[array::reference](../Topic/array::reference.md)|El tipo de una referencia a un elemento.|  
|[array::reverse\_iterator](../Topic/array::reverse_iterator.md)|El tipo de un iterador invertido para la secuencia controlada.|  
|[array::size\_type](../Topic/array::size_type.md)|El tipo de una distancia sin signo entre dos elementos.|  
|[array::value\_type](../Topic/array::value_type.md)|El tipo de un elemento.|  
  
|||  
|-|-|  
|Función miembro|Descripción|  
|[array::array](../Topic/array::array.md)|Construye un objeto de matriz.|  
|[array::assign](../Topic/array::assign.md)|Reemplaza todos los elementos.|  
|[array::at](../Topic/array::at.md)|Obtiene acceso a un elemento en una posición especificada.|  
|[array::back](../Topic/array::back.md)|Obtiene acceso al último elemento.|  
|[array::begin](../Topic/array::begin.md)|Designa el principio de la secuencia controlada.|  
|[array::cbegin](../Topic/array::cbegin.md)|Devuelve un iterador const de acceso aleatorio al primer elemento de la matriz.|  
|[array::cend](../Topic/array::cend.md)|Devuelve un iterador const de acceso aleatorio que apunta justo después del final de la matriz.|  
|[array::crbegin](../Topic/array::crbegin.md)|Devuelve un iterador constante al primer elemento de una matriz inversa.|  
|[array::crend](../Topic/array::crend.md)|Devuelve un iterador constante al final de una matriz invertida.|  
|[array::data](../Topic/array::data.md)|Obtiene la dirección del primer elemento.|  
|[array::empty](../Topic/array::empty.md)|Comprueba si hay algún elemento presente.|  
|[array::end](../Topic/array::end.md)|Designa el final de la secuencia controlada.|  
|[array::fill](../Topic/array::fill.md)|Reemplaza todos los elementos por un valor especificado.|  
|[array::front](../Topic/array::front.md)|Obtiene acceso al primer elemento.|  
|[array::max\_size](../Topic/array::max_size.md)|Cuenta el número de elementos.|  
|[array::rbegin](../Topic/array::rbegin.md)|Designa el principio de la secuencia controlada inversa.|  
|[array::rend](../Topic/array::rend.md)|Designa el final de la secuencia controlada inversa.|  
|[array::size](../Topic/array::size.md)|Cuenta el número de elementos.|  
|[array::swap](../Topic/array::swap.md)|Intercambia el contenido de dos contenedores.|  
  
|||  
|-|-|  
|Operador|Descripción|  
|[array::operator\=](../Topic/array::operator=.md)|Reemplaza la secuencia controlada.|  
|[array::operator](../Topic/array::operator.md)|Obtiene acceso a un elemento en una posición especificada.|  
  
## Comentarios  
 El tipo tiene un constructor predeterminado `array()` y un operador de asignación predeterminado `operator=`, y cumple los requisitos de un `aggregate`.  Por lo tanto, los objetos de tipo `array<Ty, N>` se pueden inicializar con un inicializador agregado.  Por ejemplo,  
  
```  
array<int, 4> ai = { 1, 2, 3 };  
```  
  
 crea el objeto `ai` que contiene cuatro valores enteros, inicializa los tres primeros elementos a los valores 1, 2 y 3, respectivamente, e inicializa el cuarto a 0.  
  
## Requisitos  
 **Encabezado:** \<array\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<array\>](../standard-library/array.md)