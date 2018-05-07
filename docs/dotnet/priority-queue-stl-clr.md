---
title: priority_queue (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue
dev_langs:
- C++
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 63e806603a795a71dc2afb95ae17779d1c6f210b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
La clase de plantilla describe un objeto que controla una longitud variable secuencia de elementos que tiene acceso limitado ordenada. Usar el adaptador de contenedor `priority_queue` para administrar un contenedor subyacente como una cola de prioridad.  
  
 En la descripción siguiente, `GValue` es el mismo que `Value` a menos que el segundo es un tipo de referencia, en cuyo caso es `Value^`. De forma similar, `GContainer` es el mismo que `Container` a menos que el segundo es un tipo de referencia, en cuyo caso es `Container^`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parámetros  
 Valor  
 Tipo de un elemento de la secuencia controlada.  
  
 contenedor  
 Tipo del contenedor subyacente.  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[priority_queue::const_reference (STL/CLR)](../dotnet/priority-queue-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[priority_queue::container_type (STL/CLR)](../dotnet/priority-queue-container-type-stl-clr.md)|Tipo del contenedor subyacente.|  
|[priority_queue::difference_type (STL/CLR)](../dotnet/priority-queue-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el adaptador de contenedor.|  
|[priority_queue::generic_value (STL/CLR)](../dotnet/priority-queue-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el adaptador de contenedor.|  
|[priority_queue::reference (STL/CLR)](../dotnet/priority-queue-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[priority_queue::size_type (STL/CLR)](../dotnet/priority-queue-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)|El delegado de ordenación para dos elementos.|  
|[priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[priority_queue::assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[priority_queue::empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[priority_queue::get_container (STL/CLR)](../dotnet/priority-queue-get-container-stl-clr.md)|Se tiene acceso del contenedor subyacente.|  
|[priority_queue::pop (STL/CLR)](../dotnet/priority-queue-pop-stl-clr.md)|Quita el elemento de prioridad de hghest.|  
|[priority_queue::priority_queue (STL/CLR)](../dotnet/priority-queue-priority-queue-stl-clr.md)|Construye un objeto contenedor.|  
|[priority_queue::push (STL/CLR)](../dotnet/priority-queue-push-stl-clr.md)|Agrega un nuevo elemento.|  
|[priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)|Cuenta el número de elementos.|  
|[priority_queue::top (STL/CLR)](../dotnet/priority-queue-top-stl-clr.md)|Accede al elemento de prioridad más alta.|  
|[priority_queue::to_array (STL/CLR)](../dotnet/priority-queue-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
|[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)|Copia al delegado de ordenación para dos elementos.|  
  
|Property|Descripción|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](../dotnet/priority-queue-top-item-stl-clr.md)|Accede al elemento de prioridad más alta.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|IPriorityQueue\<valor, contenedor >|Mantener el adaptador de contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla a través de un contenedor subyacente, de tipo `Container`, que almacena `Value` elementos y crece a petición. Mantiene la secuencia ordenada como un montón, con el elemento de prioridad más alta (el elemento superior) fácilmente accesible y extraíble. El objeto restringe el acceso a la inserción de nuevos elementos y retirar solo el elemento de prioridad más alta, la implementación de una cola de prioridad.  
  
 El objeto ordena la secuencia controla mediante una llamada a un objeto de delegado almacenado de tipo [priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Puede especificar el objeto de delegado almacenado cuando se construye la priority_queue; Si no se especifica ningún objeto de delegado, el valor predeterminado es la comparación `operator<(value_type, value_type)`. Tener acceso a este objeto almacenado llamando a la función miembro [priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.  
  
 Este tipo de objeto de delegado debe imponer una ordenación débil estricta en valores de tipo [priority_queue:: value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). Es decir, para las dos claves `X` y `Y`:  
  
 `value_comp()(X, Y)` Devuelve el valor booleano mismo resultado en cada llamada.  
  
 Si `value_comp()(X, Y)` es true, a continuación, `value_comp()(Y, X)` debe ser false.  
  
 Si `value_comp()(X, Y)` es true, a continuación, `X` se dice que se ordenan antes que `Y`.  
  
 Si `!value_comp()(X, Y) && !value_comp()(Y, X)` es true, a continuación, `X` y `Y` se dice que tienen una ordenación equivalente.  
  
 Para cualquier elemento `X` que precede a `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. (Para el objeto de delegado de forma predeterminada, las claves nunca disminuyen en valor.)  
  
 El elemento de prioridad más alto, por tanto, es uno de los elementos que no se ordenan antes que cualquier otro elemento.  
  
 Puesto que el contenedor subyacente mantiene elementos ordenados como un montón:  
  
 El contenedor debe admitir los iteradores de acceso aleatorio.  
  
 Pueden sacar elementos con una ordenación equivalente en un orden diferente de la que se insertaron. (El orden no es estable.)  
  
 Por lo tanto, son candidatos para el contenedor subyacente [deque (STL/CLR)](../dotnet/deque-stl-clr.md) y [vector (STL/CLR)](../dotnet/vector-stl-clr.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/cola >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [cola (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)