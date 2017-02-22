---
title: "reverse_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "reverse_iterator"
  - "std::reverse_iterator"
  - "std.reverse_iterator"
  - "xutility/std::reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_iterator (clase)"
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# reverse_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla es un adaptador de iterador que describe un objeto iterador inverso que se comporta como un iterador de acceso aleatorio o bidireccional, pero en orden inverso.  Habilita el recorrido hacia atrás de un intervalo.  
  
## Sintaxis  
  
```  
template <class RandomIterator>  
class reverse_iterator  
```  
  
#### Parámetros  
 RandomIterator  
 El tipo que representa el iterador que se adaptará para trabajar en orden inverso.  
  
## Comentarios  
 Los contenedores existentes en la Biblioteca de plantillas estándar también definen los tipos `reverse_iterator` y `const_reverse_iterator` y tienen funciones miembro `rbegin` y `rend` que devuelven iteradores inversos.  Estos iteradores tienen semántica de sobrescritura.  El adaptador `reverse_iterator` complementa esta funcionalidad porque proporciona semántica de inserción y también se puede utilizar con flujos.  
  
 Los `reverse_iterator`s que requiere un iterador bidireccional no deben llamar a ninguna de las funciones miembro `operator+=`, `operator+`, `operator-=`, `operator-` u `operator[]`, que solo se pueden utilizar con iteradores de acceso aleatorio.  
  
 Si el intervalo de un iterador es \[`_First`, \_Last\), donde el corchete izquierdo indica la inclusión en \_*First* y el paréntesis derecho indica la inclusión de elementos hasta \_*Left* pero la exclusión del propio \_*Left*.  Los mismos elementos están incluidos en la secuencia inversa \[**rev** – `_First`, **rev** – \_*Left*\) de manera que si \_*Left* es el elemento siguiente al elemento final de una secuencia, entonces el primer elemento **rev** – \_*First* de la secuencia inversa apunta a \*\(\_*Left* – 1 \).  La identidad que relaciona todos los iteradores inversos con sus iteradores subyacentes es:  
  
 &\*\(**reverse\_iterator** \( *i* \) \) \=\= &\*\( *i* – 1 \).  
  
 En la práctica esto significa que, en la secuencia inversa, reverse\_iterator hará referencia al elemento situado una posición más allá \(a la derecha\) del elemento al que el iterador se había referido en la secuencia original.  Así pues, si un iterador señaló el elemento 6 en la secuencia \(2, 4, 6, 8\), entonces `reverse_iterator` señalará el elemento 4 en la secuencia inversa \(8, 6, 4, 2\).  
  
### Constructores  
  
|||  
|-|-|  
|[reverse\_iterator](../Topic/reverse_iterator::reverse_iterator.md)|Construye un `reverse_iterator` predeterminado o un `reverse_iterator` a partir de un iterador subyacente.|  
  
### Typedefs  
  
|||  
|-|-|  
|[difference\_type](../Topic/reverse_iterator::difference_type.md)|Tipo que proporciona la diferencia entre dos `reverse_iterator`s que hacen referencia a elementos del mismo contenedor.|  
|[iterator\_type](../Topic/reverse_iterator::iterator_type.md)|Tipo que proporciona el iterador subyacente para `reverse_iterator`.|  
|[pointer](../Topic/reverse_iterator::pointer.md)|Tipo que proporciona un puntero a un elemento direccionado por `reverse_iterator`.|  
|[reference](../Topic/reverse_iterator::reference.md)|Tipo que proporciona una referencia a un elemento direccionado por `reverse_iterator`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[base](../Topic/reverse_iterator::base.md)|Recupera el iterador subyacente de su `reverse_iterator`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\*](../Topic/reverse_iterator::operator*.md)|Devuelve el elemento que direcciona un `reverse_iterator`.|  
|[operator\+](../Topic/reverse_iterator::operator+.md)|Agrega un desplazamiento a un iterador y devuelve el nuevo `reverse_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|  
|[operator\+\+](../Topic/reverse_iterator::operator++.md)|Incrementa el `reverse_iterator` al elemento siguiente.|  
|[operator\+\=](../Topic/reverse_iterator::operator+=.md)|Agrega un desplazamiento especificado desde un `reverse_iterator`.|  
|[operator\-](../Topic/reverse_iterator::operator-.md)|Resta un desplazamiento a `reverse_iterator` y devuelve un `reverse_iterator` que señala el elemento en la posición desplazada.|  
|[operator\-\-](../Topic/reverse_iterator::operator--.md)|Disminuye el `reverse_iterator` al elemento anterior.|  
|[operator\-\=](../Topic/reverse_iterator::operator-=.md)|Resta un desplazamiento especificado a un `reverse_iterator`.|  
|[operator\-\>](../Topic/reverse_iterator::operator-%3E.md)|Devuelve un puntero al elemento direccionado por `reverse_iterator`.|  
|[operator&#91;&#93;](../Topic/reverse_iterator::operator.md)|Devuelve una referencia a un desplazamiento de elemento con respecto al elemento direccionado por `reverse_iterator` un número especificado de posiciones.|  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)