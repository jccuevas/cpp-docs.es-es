---
title: "allocator (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::allocator"
  - "allocator"
  - "memory/std::allocator"
  - "std.allocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator (clase)"
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# allocator (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que administra la asignación de almacenamiento y la liberación de las matrices de objetos del tipo **Type**. Un objeto de clase **allocator** es el objeto de asignador predeterminado especificado en los constructores de varias clases de plantilla de contenedor en la biblioteca Standard C\+\+ Library.  
  
## Sintaxis  
  
```  
  
template <class   
Type  
>  
class allocator  
  
```  
  
#### Parámetros  
 *Tipo*  
 Tipo de objeto al que se va a asignar o desasignar almacenamiento.  
  
## Comentarios  
 Todos los contenedores de la biblioteca de plantillas estándar tienen un parámetro de plantilla establecido de forma predeterminada en **allocator**. Crear un contenedor con un asignador personalizado confiere control sobre la asignación y la liberación de los elementos de ese contenedor.  
  
 Así, por ejemplo, un objeto de asignador puede asignar almacenamiento en un montón privado o en la memoria compartida, o puede optimizar los tamaños de objetos pequeños o grandes. También puede especificar, a través de las definiciones de tipo que proporciona, que el acceso a los elementos tiene que realizarse a través de objetos de descriptor de acceso especiales que administran la memoria compartida, o realizar una recolección automática de elementos no utilizados. Por lo tanto, una clase que asigna almacenamiento con un objeto de asignador debe usar estos tipos para declarar los objetos de puntero y referencia, tal y como hacen los contenedores de la biblioteca Standard C\+\+ Library.  
  
 **\(C\_\+\+98\/03 solo\)**Si deriva de la clase allocator, tendrá que proporcionar un struct [rebind](../Topic/allocator::rebind.md) cuyo typedef `_Other` haga referencia a la clase recién derivada.  
  
 Por lo tanto, un asignador define los siguientes tipos:  
  
-   [pointer](../Topic/allocator::pointer.md) se comporta como un puntero a **Type**.  
  
-   [const\_pointer](../Topic/allocator::const_pointer.md) se comporta como un puntero constante a **Type**.  
  
-   [reference](../Topic/allocator::reference.md) se comporta como una referencia a **Type**.  
  
-   [const\_reference](../Topic/allocator::const_reference.md) se comporta como una referencia constante a **Type**.  
  
 Estos **Type** especifican la forma que han de tomar los punteros y las referencias para los elementos asignados. \([allocator::pointer](../Topic/allocator::pointer.md) no es necesariamente el mismo que **Type**\* para todos los objetos de asignador, aun cuando tenga esta definición obvia para la clase **allocator**\).  
  
 **C\+\+11 y versiones posteriores:**  para permitir las operaciones de movimiento en el asignador, use la interfaz de asignador mínima e implemente el constructor de copias, los operadores \=\= y\! \= y allocate y deallocate. Para obtener más información y ver un ejemplo, vea [Asignadores](../standard-library/allocators.md).  
  
## Miembros  
  
### Constructores  
  
|||  
|-|-|  
|[asignador](../Topic/allocator::allocator.md)|Constructores usados para crear objetos `allocator`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[const\_pointer](../Topic/allocator::const_pointer.md)|Tipo que proporciona un puntero constante al tipo de objeto administrado por el asignador.|  
|[const\_reference](../Topic/allocator::const_reference.md)|Tipo que proporciona una referencia constante al tipo de objeto administrado por el asignador.|  
|[difference\_type](../Topic/allocator::difference_type.md)|Tipo entero con signo que puede representar la diferencia entre valores de punteros que señalan al tipo de objeto administrado por el asignador.|  
|[puntero](../Topic/allocator::pointer.md)|Tipo que proporciona un puntero al tipo de objeto administrado por el asignador.|  
|[reference](../Topic/allocator::reference.md)|Tipo que proporciona una referencia al tipo de objeto administrado por el asignador.|  
|[size\_type](../Topic/allocator::size_type.md)|Tipo entero sin signo que puede representar la longitud de cualquier secuencia que un objeto de clase de plantilla `allocator` puede asignar.|  
|[value\_type](../Topic/allocator::value_type.md)|Tipo administrado por el asignador.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[dirección](../Topic/allocator::address.md)|Encuentra la dirección de un objeto cuyo valor se especifica.|  
|[allocate](../Topic/allocator::allocate.md)|Asigna un bloque de memoria lo suficientemente grande como para almacenar al menos un número especificado de elementos.|  
|[construct](../Topic/allocator::construct.md)|Crea un tipo concreto de objeto en una dirección especificada que se inicializa con un valor especificado.|  
|[deallocate](../Topic/allocator::deallocate.md)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
|[destruir](../Topic/allocator::destroy.md)|Llama a un destructor de objetos sin desasignar la memoria donde el objeto se almacena.|  
|[max\_size](../Topic/allocator::max_size.md)|Devuelve el número de elementos de tipo `Type` que podrían ser asignados por un objeto de clase `allocator` antes de que la memoria libre se agote.|  
|[rebind](../Topic/allocator::rebind.md)|Estructura que permite que un asignador de objetos de un tipo asigne almacenamiento para objetos de otro tipo.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\=](../Topic/allocator::operator=.md)|Asigna un objeto `allocator` a otro objeto `allocator`.|  
  
## Requisitos  
 **Encabezado:** \<memory\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)