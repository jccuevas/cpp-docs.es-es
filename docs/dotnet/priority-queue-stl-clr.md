---
title: "priority_queue (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/queue> (encabezado) [STL/CLR]"
  - "<queue> (encabezado) [STL/CLR]"
  - "priority_queue (clase) [STL/CLR]"
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# priority_queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia ordenada variar\- longitud de elementos con acceso restringido.  Utiliza el adaptador `priority_queue` de contenedor para administrar un contenedor subyacente como cola de prioridad.  
  
 En la descripción siguiente, `GValue` es igual que `Value` a menos que este último es un tipo de referencia, en este caso es `Value^`.  De igual forma, `GContainer` es igual que `Container` a menos que este último es un tipo de referencia, en este caso es `Container^`.  
  
## Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### Parámetros  
 Valor  
 Tipo de un elemento de la secuencia controlada.  
  
 Contenedor  
 Tipo del contenedor subyacente.  
  
## Miembros  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|[priority\_queue::const\_reference](../dotnet/priority-queue-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[priority\_queue::container\_type](../dotnet/priority-queue-container-type-stl-clr.md)|Tipo del contenedor subyacente.|  
|[priority\_queue::difference\_type](../dotnet/priority-queue-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[priority\_queue::generic\_container](../dotnet/priority-queue-generic-container-stl-clr.md)|El tipo de interfaz genérica para el adaptador del contenedor.|  
|[priority\_queue::generic\_value](../dotnet/priority-queue-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el adaptador del contenedor.|  
|[priority\_queue::reference](../dotnet/priority-queue-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[priority\_queue::size\_type](../dotnet/priority-queue-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[priority\_queue::value\_compare](../dotnet/priority-queue-value-compare-stl-clr.md)|El delegado de ordenación para dos elementos.|  
|[priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[priority\_queue::assign](../dotnet/priority-queue-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[priority\_queue::empty](../dotnet/priority-queue-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[priority\_queue::get\_container](../dotnet/priority-queue-get-container-stl-clr.md)|Tiene acceso al contenedor subyacente.|  
|[priority\_queue::pop](../dotnet/priority-queue-pop-stl-clr.md)|Quita el elemento de la hghest\-prioridad.|  
|[priority\_queue::priority\_queue](../dotnet/priority-queue-priority-queue-stl-clr.md)|Construye un objeto contenedor.|  
|[priority\_queue::push](../dotnet/priority-queue-push-stl-clr.md)|Agrega un nuevo elemento.|  
|[priority\_queue::size](../dotnet/priority-queue-size-stl-clr.md)|Cuenta el número de elementos.|  
|[priority\_queue::top](../dotnet/priority-queue-top-stl-clr.md)|Tiene acceso al elemento de prioridad más alta.|  
|[priority\_queue::to\_array](../dotnet/priority-queue-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
|[priority\_queue::value\_comp](../dotnet/priority-queue-value-comp-stl-clr.md)|Copia el delegado de ordenación de dos elementos.|  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[priority\_queue::top\_item](../dotnet/priority-queue-top-item-stl-clr.md)|Tiene acceso al elemento de prioridad más alta.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[priority\_queue::operator\=](../dotnet/priority-queue-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|IPriorityQueueValue\<, contenedor\>|Mantenga el adaptador genérico del contenedor.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla a través de un contenedor subyacente, de `Container`escrito, que almacena los elementos de `Value` y crece a petición.  Mantiene la secuencia ordenada como pila, con el elemento más prioritario \(el elemento superior\) fácilmente accesible y movible.  El objeto limita el acceso a insertar nuevos elementos y a extraen solo el elemento prioridad, implementando una cola de prioridad.  
  
 El objeto pide la secuencia que controla llamando a un objeto almacenado de delegado de [priority\_queue::value\_compare](../dotnet/priority-queue-value-compare-stl-clr.md)escrito.  Puede especificar el objeto almacenado de delegado cuando se construye el priority\_queue; si no especifica ningún objeto delegado, el valor predeterminado es la comparación `operator<(value_type, value_type)`.  Tiene acceso a este objeto almacenado llamando a la función [priority\_queue::value\_comp](../dotnet/priority-queue-value-comp-stl-clr.md)`()`miembro.  
  
 Este tipo de objeto delegado debe imponer orden débil estricto sobre valores de [priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)escrito.  Es decir, para cualquier dos claves `X` y `Y`:  
  
 `value_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.  
  
 Si `value_comp()(X, Y)` es true, el `value_comp()(Y, X)` debe ser false.  
  
 Si `value_comp()(X, Y)` es true, el `X` se secuenciado antes de `Y`.  
  
 Si `!value_comp()(X, Y) && !value_comp()(Y, X)` es true, el `X` y `Y` se dice que tienen orden equivalente.  
  
 Para cualquier elemento `X` que preceda `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. \(Para el objeto predeterminado de delegado, las teclas nunca disminuyen en valor.\)  
  
 El elemento prioridad es uno de los elementos que no se ordena antes de ningún otro elemento.  
  
 Puesto que el contenedor subyacente mantiene los elementos pedidos como montón:  
  
 El contenedor debe admitir estos últimos.  
  
 Los elementos a la ordenación de equivalente se pueden extraen en un orden diferente que se insertarán. \(El orden de no es estable.\)  
  
 Así, los candidatos al contenedor subyacente incluyen [deque](../dotnet/deque-stl-clr.md) y [vector](../dotnet/vector-stl-clr.md).  
  
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [pila](../dotnet/stack-stl-clr.md)   
 [vector](../dotnet/vector-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)