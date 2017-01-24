---
title: "concurrent_priority_queue (Clase) | Microsoft Docs"
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
  - "concurrent_priority_queue/concurrency::concurrent_priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "concurrent_priority_queue (clase)"
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# concurrent_priority_queue (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `concurrent_priority_queue` es un contenedor que permite que varios subprocesos inserten y extraigan elementos de forma simultánea.  Los elementos se extraen en orden de prioridad donde la prioridad viene determinada por un functor proporcionado como un argumento de plantilla.  
  
## Sintaxis  
  
```  
template <  
   typename _Ty,  
   typename _Compare=std::less<_Ty>,  
   typename _Ax = std::allocator<_Ty>  
>  
, typename _Ax = std::allocator<_Ty> > class concurrent_priority_queue;  
```  
  
#### Parámetros  
 `_Ty`  
 El tipo de datos de los elementos que se van a almacenar en la cola de prioridad.  
  
 `_Compare`  
 El tipo de objeto de la función que puede comparar dos valores de elemento como criterio de ordenación para determinar el orden relativo en la cola de prioridad.  Este argumento es opcional y el predicado binario `less<``_Ty``>` es el valor predeterminado.  
  
 `_Ax`  
 El tipo que representa el objeto almacenado de asignador que encapsula los detalles sobre la asignación y la desasignación de memoria para la cola de prioridad simultánea.  Este argumento es opcional y el valor predeterminado es `allocator<``_Ty``>`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`allocator_type`|Un tipo que representa la clase del asignador de la cola de prioridad simultánea.|  
|`const_reference`|Un tipo que representa una referencia const a un elemento del tipo almacenados en una cola de prioridad simultánea.|  
|`reference`|Un tipo que representa una referencia a un elemento del tipo almacenados en una cola de prioridad simultánea.|  
|`size_type`|Un tipo que cuenta el número de elementos en una cola de prioridad simultánea.|  
|`value_type`|Un tipo que representa el tipo de datos almacenados en una cola de prioridad simultánea.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_priority\_queue::concurrent\_priority\_queue \(Constructor\)](../Topic/concurrent_priority_queue::concurrent_priority_queue%20Constructor.md)|Sobrecargado.  Crea una cola de prioridad simultánea.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_priority\_queue::clear \(Método\)](../Topic/concurrent_priority_queue::clear%20Method.md)|Borra todos los elementos de prioridad simultánea.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_priority\_queue::empty \(Método\)](../Topic/concurrent_priority_queue::empty%20Method.md)|Denominarse pruebas si la cola de prioridad simultánea está vacía en el momento de este método.  Este método es seguro para simultaneidad.|  
|[concurrent\_priority\_queue::get\_allocator \(Método\)](../Topic/concurrent_priority_queue::get_allocator%20Method.md)|Devuelve una copia del asignador utilizado para crear la cola de prioridad simultánea.  Este método es seguro para simultaneidad.|  
|[concurrent\_priority\_queue::push \(Método\)](../Topic/concurrent_priority_queue::push%20Method.md)|Sobrecargado.  Agrega un elemento a la cola de prioridad simultánea.  Este método es seguro para simultaneidad.|  
|[concurrent\_priority\_queue::size \(Método\)](../Topic/concurrent_priority_queue::size%20Method.md)|Devuelve el número de elementos en la cola de prioridad simultánea.  Este método es seguro para simultaneidad.|  
|[concurrent\_priority\_queue::swap \(Método\)](../Topic/concurrent_priority_queue::swap%20Method.md)|Cambia el contenido de dos colas de prioridad simultáneas.  Este método no es seguro para la simultaneidad.|  
|[concurrent\_priority\_queue::try\_pop \(Método\)](../Topic/concurrent_priority_queue::try_pop%20Method.md)|Quita y devuelve el elemento más prioritario de la cola si la cola no está vacío.  Este método es seguro para simultaneidad.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[concurrent\_priority\_queue::operator\= \(Operador\)](../Topic/concurrent_priority_queue::operator=%20Operator.md)|Sobrecargado.  Asigna el contenido de otro objeto `concurrent_priority_queue` a este.  Este método no es seguro para la simultaneidad.|  
  
## Comentarios  
 Para obtener información detallada sobre la clase `concurrent_priority_queue`, vea [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## Jerarquía de herencia  
 `concurrent_priority_queue`  
  
## Requisitos  
 **Encabezado:** concurrent\_priority\_queue.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Contenedores y objetos paralelos](../../../parallel/concrt/parallel-containers-and-objects.md)