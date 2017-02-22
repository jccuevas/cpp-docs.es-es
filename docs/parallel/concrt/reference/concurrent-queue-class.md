---
title: "Clase concurrent_queue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concurrent_queue/concurrency::concurrent_queue"
  - "concurrent_queue/Concurrency::concurrent_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_queue (clase)"
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Clase concurrent_queue
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `concurrent_queue` es una clase de contenedor de secuencias que permite el acceso primero en entrar, primero en salir a sus elementos.  Habilita un conjunto limitado de operaciones seguras para simultaneidad, como `push` y `try_pop`.  
  
## Sintaxis  
  
```  
template<  
   typename _Ty,  
   class _Ax  
>  
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;  
```  
  
#### Parámetros  
 `_Ty`  
 Tipo de datos de los elementos que se van a almacenar en la cola.  
  
 `_Ax`  
 El tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria para esta cola simultánea.  Este argumento es opcional y el valor predeterminado es `allocator<``_Ty``>`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`allocator_type`|Un tipo que representa la clase de asignador de la cola simultánea.|  
|`const_iterator`|Un tipo que representa un iterador `const` no seguro para subprocesos sobre los elementos en una cola simultánea.|  
|`const_reference`|Un tipo que proporciona una referencia a un elemento `const` almacenado en una cola simultánea para leer y realizar operaciones `const`.|  
|`difference_type`|Un tipo que proporciona la distancia firmada entre dos elementos en una cola simultánea.|  
|`iterator`|Un tipo que representa un iterador no seguro para subprocesos sobre los elementos en una cola simultánea.|  
|`reference`|Un tipo que proporciona una referencia a un elemento almacenado en una cola simultánea.|  
|`size_type`|Un tipo que cuenta el número de elementos en una cola simultánea.|  
|`value_type`|Un tipo que representa el tipo de datos almacenados en una cola simultánea.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_queue::concurrent\_queue \(Constructor\)](../Topic/concurrent_queue::concurrent_queue%20Constructor.md)|Sobrecargado.  Construye una cola simultánea.|  
|[concurrent\_queue::~concurrent\_queue \(Destructor\)](../Topic/concurrent_queue::~concurrent_queue%20Destructor.md)|Destruye la cola simultánea.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_queue::clear \(Método\)](../Topic/concurrent_queue::clear%20Method.md)|Borra la cola simultánea, destruyendo los elementos que se encuentren en la cola actualmente.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_queue::empty \(Método\)](../Topic/concurrent_queue::empty%20Method.md)|Comprueba si la cola simultánea está vacía en el momento al que se llama a este método.  Este método es seguro para simultaneidad.|  
|[concurrent\_queue::get\_allocator \(Método\)](../Topic/concurrent_queue::get_allocator%20Method.md)|Devuelve una copia del asignador usada para construir la cola simultánea.  Este método es seguro para simultaneidad.|  
|[concurrent\_queue::push \(Método\)](../Topic/concurrent_queue::push%20Method.md)|Sobrecargado.  Elimina un elemento del final de la cola de la cola simultánea.  Este método es seguro para simultaneidad.|  
|[concurrent\_queue::try\_pop \(Método\)](../Topic/concurrent_queue::try_pop%20Method.md)|Elimina un elemento de la cola si está disponible.  Este método es seguro para simultaneidad.|  
|[concurrent\_queue::unsafe\_begin \(Método\)](../Topic/concurrent_queue::unsafe_begin%20Method.md)|Sobrecargado.  Devuelve un iterador de tipo `iterator` o `const_iterator` al principio de la cola simultánea.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_queue::unsafe\_end \(Método\)](../Topic/concurrent_queue::unsafe_end%20Method.md)|Sobrecargado.  Devuelve un iterador de tipo `iterator` o `const_iterator` al final de la cola simultánea.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_queue::unsafe\_size \(Método\)](../Topic/concurrent_queue::unsafe_size%20Method.md)|Devuelve el número de elementos de la cola.  Este método no es seguro para la simultaneidad.|  
  
## Comentarios  
 Para obtener más información, vea [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## Jerarquía de herencia  
 `concurrent_queue`  
  
## Requisitos  
 **Encabezado:** concurrent\_queue.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)