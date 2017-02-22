---
title: "vector (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/vector> (encabezado) [STL/CLR]"
  - "<vector> (encabezado) [STL/CLR]"
  - "vector (clase) [STL/CLR]"
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# vector (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos que tiene acceso aleatorio.  Utiliza el contenedor `vector` para administrar una secuencia de elementos como bloque contiguo de almacenamiento.  El bloque se implementa como una matriz que aumenta a petición.  
  
 En la descripción siguiente, `GValue` es igual que `Value` a menos que este último es un tipo de referencia, en este caso es `Value^`.  
  
## Sintaxis  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
#### Parámetros  
 Valor  
 Tipo de un elemento de la secuencia controlada.  
  
## Miembros  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|[vector::const\_iterator](../dotnet/vector-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[vector::const\_reference](../dotnet/vector-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[vector::const\_reverse\_iterator](../dotnet/vector-const-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso constante para la secuencia controlada.|  
|[vector::difference\_type](../dotnet/vector-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[vector::generic\_container](../dotnet/vector-generic-container-stl-clr.md)|El tipo de interfaz genérica para el contenedor.|  
|[vector::generic\_iterator](../dotnet/vector-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[vector::generic\_reverse\_iterator](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[vector::generic\_value](../dotnet/vector-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[vector::iterator](../dotnet/vector-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[vector::reference](../dotnet/vector-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[vector::reverse\_iterator](../dotnet/vector-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la secuencia controlada.|  
|[vector::size\_type](../dotnet/vector-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[vector::value\_type](../dotnet/vector-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[vector::assign](../dotnet/vector-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[vector::at](../dotnet/vector-at-stl-clr.md)|Tiene acceso a un elemento en una posición especificada.|  
|[vector::back](../dotnet/vector-back-stl-clr.md)|Tiene acceso al último elemento.|  
|[vector::begin](../dotnet/vector-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[vector::capacity](../dotnet/vector-capacity-stl-clr.md)|Notifica el tamaño de almacenamiento asignado del contenedor.|  
|[vector::clear](../dotnet/vector-clear-stl-clr.md)|Quita todos los elementos.|  
|[vector::empty](../dotnet/vector-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[vector::end](../dotnet/vector-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[vector::erase](../dotnet/vector-erase-stl-clr.md)|Quita los elementos en las posiciones especificadas.|  
|[vector::front](../dotnet/vector-front-stl-clr.md)|Tiene acceso al primer elemento.|  
|[vector::insert](../dotnet/vector-insert-stl-clr.md)|Agrega elementos en una posición especificada.|  
|[vector::pop\_back](../dotnet/vector-pop-back-stl-clr.md)|Quita el último elemento.|  
|[vector::push\_back](../dotnet/vector-push-back-stl-clr.md)|Agrega un nuevo elemento pasado.|  
|[vector::rbegin](../dotnet/vector-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[vector::rend](../dotnet/vector-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[vector::reserve](../dotnet/vector-reserve-stl-clr.md)|Proteger una capacidad mínima de crecimiento para el contenedor.|  
|[vector::resize](../dotnet/vector-resize-stl-clr.md)|Cambia el número de elementos.|  
|[vector::size](../dotnet/vector-size-stl-clr.md)|Cuenta el número de elementos.|  
|[vector::swap](../dotnet/vector-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[vector::to\_array](../dotnet/vector-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
|[vector::vector](../dotnet/vector-vector-stl-clr.md)|Construye un objeto contenedor.|  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[vector::back\_item](../dotnet/vector-back-item-stl-clr.md)|Tiene acceso al último elemento.|  
|[vector::front\_item](../dotnet/vector-front-item-stl-clr.md)|Tiene acceso al primer elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[vector::operator\=](../dotnet/vector-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[vector::operator](../dotnet/vector-operator-stl-clr.md)|Tiene acceso a un elemento en una posición especificada.|  
|[operator\!\= \(vector\)](../dotnet/operator-inequality-vector-stl-clr.md)|Determina si un objeto de `vector` no es igual a otro objeto de `vector` .|  
|[operator\< \(vector\)](../dotnet/operator-less-than-vector-stl-clr.md)|Determina si un objeto de `vector` es menor que otro objeto de `vector` .|  
|[operator\<\= \(vector\)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|Determina si un objeto de `vector` menor o igual que otro objeto de `vector` .|  
|[operator\=\= \(vector\)](../dotnet/operator-equality-vector-stl-clr.md)|Determina si un objeto de `vector` es igual a otro objeto de `vector` .|  
|[operator\> \(vector\)](../dotnet/operator-greater-than-vector-stl-clr.md)|Determina si un objeto de `vector` es mayor que otro objeto de `vector` .|  
|[operator\>\= \(vector\)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|Determina si un objeto de `vector` mayor o igual que otro objeto de `vector` .|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantenga el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia mediante elementos escritos.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantenga el grupo de elementos escritos.|  
|<xref:System.Collections.Generic.IList%601>|Maintain pidió al grupo de elementos escritos.|  
|IVectorValue\<\>|Mantenga el contenedor genérico.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla con una matriz almacenado de los elementos de `Value` , que crece a petición.  El crecimiento aparece de manera que el costo de anexar un nuevo elemento se amortice tiempo constante.  Es decir el costo de agregar elementos al final no aumenta, por término medio, como la longitud de la secuencia controlada obtiene mayor.  Así, un vector es un buen candidato al contenedor subyacente para la clase de plantilla [pila](../dotnet/stack-stl-clr.md).  
  
 `vector` admite iteradores de acceso aleatorio, lo que significa que puede hacer referencia a un elemento determinado directamente su posición numérica, contando a desde cero para el primer elemento \(frontal\), a [vector::size](../dotnet/vector-size-stl-clr.md)`() - 1` para el elemento \(posterior\) pasado.  También significa que un vector es un buen candidato al contenedor subyacente para la clase de plantilla [priority\_queue](../dotnet/priority-queue-stl-clr.md).  
  
 Un iterador de vector almacena un identificador al objeto asociado vectoriales, junto con la tendencia del elemento que señala.  Puede usar iteradores únicamente con los objetos contenedores asociados.  La tendencia de un elemento de vector coincide con su posición.  
  
 Insertar o eliminar elementos puede cambiar el valor del elemento almacenado en una posición determinada, por lo que el valor indicado por un iterador también puede cambiar. \(El contenedor se puede tener que copiar elementos arriba o abajo para crear un hueco antes de una inserción o para rellenar una vulnerabilidad después de un barrido.\) Sin embargo, un iterador de vector sigue siendo válido siempre y cuando la tendencia está en el intervalo `[0,` [vector::size](../dotnet/vector-size-stl-clr.md)`()]`.  Por otra parte, un iterador válido permanece dereferencable \-\- puede utilizarlo para obtener acceso o modificar el valor del elemento que señala \-\- siempre y cuando la tendencia no es igual a `size()`.  
  
 Borrar o quitar un elemento denomina destructor por el valor almacenado.  Destruyendo el contenedor borra todos los elementos.  Así, un contenedor cuyo tipo de elemento es una clase de referencia se asegura que ningún elemento sobrevivan al contenedor.  La nota, sin embargo, que un contenedor de identificadores hace `not` destruye sus elementos.  
  
## Requisitos  
 cliext \<\/vector de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [pila](../dotnet/stack-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)