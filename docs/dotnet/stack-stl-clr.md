---
title: "stack (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/stack> (encabezado) [STL/CLR]"
  - "<stack> (encabezado) [STL/CLR]"
  - "clase de pila [STL/CLR]"
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# stack (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos que tenga acceso de último en entrar, primero en salir\).  Utiliza el adaptador `stack` de contenedor para administrar un contenedor subyacente como pila de inserción \- a continuación.  
  
 En la descripción siguiente, `GValue` es igual que `Value` a menos que este último es un tipo de referencia, en este caso es `Value^`.  De igual forma, `GContainer` es igual que `Container` a menos que este último es un tipo de referencia, en este caso es `Container^`.  
  
## Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
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
|[stack::const\_reference](../dotnet/stack-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[stack::container\_type](../dotnet/stack-container-type-stl-clr.md)|Tipo del contenedor subyacente.|  
|[stack::difference\_type](../dotnet/stack-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[stack::generic\_container](../dotnet/stack-generic-container-stl-clr.md)|El tipo de interfaz genérica para el adaptador del contenedor.|  
|[stack::generic\_value](../dotnet/stack-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el adaptador del contenedor.|  
|[stack::reference](../dotnet/stack-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[stack::size\_type](../dotnet/stack-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[stack::value\_type](../dotnet/stack-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[stack::assign](../dotnet/stack-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[stack::empty](../dotnet/stack-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[stack::get\_container](../dotnet/stack-get-container-stl-clr.md)|Tiene acceso al contenedor subyacente.|  
|[stack::pop](../dotnet/stack-pop-stl-clr.md)|Quita el último elemento.|  
|[stack::push](../dotnet/stack-push-stl-clr.md)|Agrega un nuevo elemento pasado.|  
|[stack::size](../dotnet/stack-size-stl-clr.md)|Cuenta el número de elementos.|  
|[stack::stack](../dotnet/stack-stack-stl-clr.md)|Construye un objeto contenedor.|  
|[stack::top](../dotnet/stack-top-stl-clr.md)|Tiene acceso al último elemento.|  
|[stack::to\_array](../dotnet/stack-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[stack::top\_item](../dotnet/stack-top-item-stl-clr.md)|Tiene acceso al último elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[stack::operator\=](../dotnet/stack-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator\!\= \(stack\)](../dotnet/operator-inequality-stack-stl-clr.md)|Determina si un objeto de `stack` no es igual a otro objeto de `stack` .|  
|[operator\< \(stack\)](../dotnet/operator-less-than-stack-stl-clr.md)|Determina si un objeto de `stack` es menor que otro objeto de `stack` .|  
|[operator\<\= \(stack\)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|Determina si un objeto de `stack` menor o igual que otro objeto de `stack` .|  
|[operator\=\= \(stack\)](../dotnet/operator-equality-stack-stl-clr.md)|Determina si un objeto de `stack` es igual a otro objeto de `stack` .|  
|[operator\> \(stack\)](../dotnet/operator-greater-than-stack-stl-clr.md)|Determina si un objeto de `stack` es mayor que otro objeto de `stack` .|  
|[operator\>\= \(stack\)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|Determina si un objeto de `stack` mayor o igual que otro objeto de `stack` .|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|IStackValue\<, contenedor\>|Mantenga el adaptador genérico del contenedor.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla a través de un contenedor subyacente, de `Container`escrito, que almacena los elementos de `Value` y crece a petición.  El objeto limita el acceso a insertar y a extraen solo el último elemento, implementando una cola de último en entrar, primero en salir \(también conocida como una cola LIFO, o montón\).  
  
## Requisitos  
 cliext \<\/pila de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [vector](../dotnet/vector-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)