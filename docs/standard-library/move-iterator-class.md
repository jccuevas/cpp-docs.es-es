---
title: "move_iterator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.move_iterator"
  - "move_iterator"
  - "iterator/std::move_iterator"
  - "std::move_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "move_iterator (clase)"
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# move_iterator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La plantilla de clase `move_iterator` es un contenedor para un iterador.  La plantilla move\_iterator ofrece el mismo comportamiento que el iterador que contiene \(almacena\), con la excepción de que cambia el operador de desreferencia por una referencia rvalue y convierte una copia en un movimiento.  Para obtener más información acerca de los valores rvalues, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## Sintaxis  
  
```  
template<class Iterator>  
    class move_iterator {  
public:  
    typedef Iterator iterator_type;  
    typedef typename      
        iterator_traits<Iterator>::iterator_category  
            iterator_category;  
    typedef typename iterator_traits<Iterator>::value_type  
        value_type;  
    typedef typename iterator_traits<Iterator>::difference_type  
        difference_type;  
    typedef Iterator  
        pointer;  
    typedef value_type&&  
        reference;  
  
    move_iterator();  
    explicit move_iterator (Iterator right);  
    template<class Type>  
        move_iterator (const move_iterator<Type>& right);  
    template <class Type>   
        move_iterator& operator=(const move_iterator<Type>& right);  
  
    iterator_type base () const;  
    reference operator* () const;  
    pointer operator-> () const;  
  
    move_iterator& operator++ ();  
    move_iterator operator++ (int);  
    move_iterator& operator-- ();  
    move_iterator operator-- (int);  
  
    move_iterator& operator+= (difference_type off);  
    move_iterator operator+ (difference_type off) const;  
    move_iterator& operator-= (difference_type off);  
    move_iterator operator- (difference_type off) const;  
    reference operator[] (difference_type off) const;  
    };  
```  
  
## Comentarios  
 La clase de plantilla describe un objeto que se comporta como un iterador salvo cuando se desreferencia.  Almacena un iterador de acceso aleatorio de tipo `Iterator`, al que se tiene acceso mediante la función miembro `base``()`.  Todas las operaciones de `move_iterator` se realizan directamente en el iterador almacenado, con la excepción de que el resultado de `operator*` se convierte implícitamente en `value_type&&` para crear una referencia rvalue.  
  
 Un `move_iterator` puede llevar a cabo operaciones no definidas por el iterador contenedor.  Estas operaciones no se deben usar.  
  
### Constructores  
  
|||  
|-|-|  
|[move\_iterator](../Topic/move_iterator::move_iterator.md)|Constructor para los objetos de tipo `move_iterator`.|  
  
### Typedefs  
  
|||  
|-|-|  
|[move\_iterator::iterator\_type](../Topic/move_iterator::iterator_type.md)|Sinónimo del parámetro de plantilla `RandomIterator`.|  
|[move\_iterator::iterator\_category](../Topic/move_iterator::iterator_category.md)|Un sinónimo de una expresión más larga de `typename` del mismo nombre, `iterator_category` identifica las capacidades generales del iterador.|  
|[move\_iterator::value\_type](../Topic/move_iterator::value_type.md)|Un sinónimo de una expresión más larga de `typename` del mismo nombre, `value_type` describe de qué tipo son los elementos del iterador.|  
|[move\_iterator::difference\_type](../Topic/move_iterator::difference_type.md)|Un sinónimo de una expresión más larga de `typename` del mismo nombre, `difference_type` describe el tipo entero necesario para expresar valores diferentes entre elementos.|  
|[move\_iterator::pointer](../Topic/move_iterator::pointer.md)|Sinónimo del parámetro de plantilla `RandomIterator`.|  
|[move\_iterator::reference](../Topic/move_iterator::reference.md)|Sinónimo de la referencia `rvalue` `value_type&&`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[move\_iterator::base](../Topic/move_iterator::base.md)|La función miembro devuelve el iterador almacenado contenido en este `move_iterator`.|  
  
### Operadores  
  
|||  
|-|-|  
|[move\_iterator::operator\*](../Topic/move_iterator::operator*.md)|Devuelve `(reference)*``base``().`|  
|[move\_iterator::operator\+\+](../Topic/move_iterator::operator++.md)|Incrementa el iterador almacenado.  El comportamiento exacto depende de si se trata de una operación de incremento previo o posterior.|  
|[move\_iterator::operator\-\-](../Topic/move_iterator::operator--.md)|Disminuye el iterador almacenado.  El comportamiento exacto depende de si se trata de una operación de disminución previa o posterior.|  
|[move\_iterator::operator\-\>](../Topic/move_iterator::operator-%3E.md)|Devuelve `&**this`.|  
|[move\_iterator::operator\-](../Topic/move_iterator::operator-.md)|Devuelve `move_iterator(*this) -=` restando primero el valor situado a la derecha de la posición actual.|  
|[move\_iterator::operator](../Topic/move_iterator::operator.md)|Devuelve `(reference)*(*this + off)`.  Permite especificar una posición de desplazamiento a partir de la base actual para obtener el valor que se encuentra en esa ubicación.|  
|[move\_iterator::operator\+](../Topic/move_iterator::operator+.md)|Devuelve el valor `move_iterator(*this) +=` .  Permite agregar una posición de desplazamiento a la base para obtener el valor que se encuentra en esa ubicación.|  
|[move\_iterator::operator\+\=](../Topic/move_iterator::operator+=.md)|Agrega el valor situado a la derecha del iterador almacenado y devuelve `*this`.|  
|[move\_iterator::operator\-\=](../Topic/move_iterator::operator-=.md)|Resta el valor situado a la derecha del iterador almacenado y devuelve `*this`.|  
  
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Lvalues y rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)   
 [Constructores de movimiento y operadores de asignación de movimiento \(C\+\+\)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)