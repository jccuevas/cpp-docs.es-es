---
title: "queue (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::queue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/queue> (encabezado) [STL/CLR]"
  - "<queue> (encabezado) [STL/CLR]"
  - "queue (clase) [STL/CLR]"
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# queue (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos con primer \- out acceso primero en entrar, primero en salir.  Utiliza el adaptador `queue` de contenedor para administrar un contenedor subyacente como cola.  
  
 En la descripción siguiente, `GValue` es igual que `Value` a menos que este último es un tipo de referencia, en este caso es `Value^`.  De igual forma, `GContainer` es igual que `Container` a menos que este último es un tipo de referencia, en este caso es `Container^`.  
  
## Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
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
|[queue::const\_reference](../dotnet/queue-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[queue::container\_type](../dotnet/queue-container-type-stl-clr.md)|Tipo del contenedor subyacente.|  
|[queue::difference\_type](../dotnet/queue-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[queue::generic\_container](../dotnet/queue-generic-container-stl-clr.md)|El tipo de interfaz genérica para el adaptador del contenedor.|  
|[queue::generic\_value](../dotnet/queue-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el adaptador del contenedor.|  
|[queue::reference](../dotnet/queue-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[queue::size\_type](../dotnet/queue-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[queue::value\_type](../dotnet/queue-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[queue::assign](../dotnet/queue-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[queue::back](../dotnet/queue-back-stl-clr.md)|Tiene acceso al último elemento.|  
|[queue::empty](../dotnet/queue-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[queue::front](../dotnet/queue-front-stl-clr.md)|Tiene acceso al primer elemento.|  
|[queue::get\_container](../dotnet/queue-get-container-stl-clr.md)|Tiene acceso al contenedor subyacente.|  
|[queue::pop](../dotnet/queue-pop-stl-clr.md)|Quita el primer elemento.|  
|[queue::push](../dotnet/queue-push-stl-clr.md)|Agrega un nuevo elemento pasado.|  
|[queue::queue](../dotnet/queue-queue-stl-clr.md)|Construye un objeto contenedor.|  
|[queue::size](../dotnet/queue-size-stl-clr.md)|Cuenta el número de elementos.|  
|[queue::to\_array](../dotnet/queue-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[queue::back\_item](../dotnet/queue-back-item-stl-clr.md)|Tiene acceso al último elemento.|  
|[queue::front\_item](../dotnet/queue-front-item-stl-clr.md)|Tiene acceso al primer elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[queue::operator\=](../dotnet/queue-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator\!\= \(queue\)](../dotnet/operator-inequality-queue-stl-clr.md)|Determina si un objeto de `queue` no es igual a otro objeto de `queue` .|  
|[operator\< \(queue\)](../dotnet/operator-less-than-queue-stl-clr.md)|Determina si un objeto de `queue` es menor que otro objeto de `queue` .|  
|[operator\<\= \(queue\)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|Determina si un objeto de `queue` menor o igual que otro objeto de `queue` .|  
|[operator\=\= \(queue\)](../dotnet/operator-equality-queue-stl-clr.md)|Determina si un objeto de `queue` es igual a otro objeto de `queue` .|  
|[operator\> \(queue\)](../dotnet/operator-greater-than-queue-stl-clr.md)|Determina si un objeto de `queue` es mayor que otro objeto de `queue` .|  
|[operator\>\= \(queue\)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|Determina si un objeto de `queue` mayor o igual que otro objeto de `queue` .|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|IQueueValue\<, contenedor\>|Mantenga el adaptador genérico del contenedor.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla a través de un contenedor subyacente, de `Container`escrito, que almacena los elementos de `Value` y crece a petición.  El objeto limita el acceso solo a insertar el primer y a extraen el último elemento, implementando una primera \- out cola primero en entrar, primero en salir \(también conocida como una cola FIFO \(primero en entrar, primero en salir, o simplemente cola\).  
  
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [pila](../dotnet/stack-stl-clr.md)   
 [vector](../dotnet/vector-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)