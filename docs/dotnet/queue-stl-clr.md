---
title: cola (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::queue
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d5b91a2556a93f3cd74a24ea57306d70f2cbdb41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="queue-stlclr"></a>queue (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso primero en salir. Usar el adaptador de contenedor `queue` para administrar un contenedor subyacente como una cola.  
  
 En la descripción siguiente, `GValue` es el mismo que `Value` a menos que el segundo es un tipo de referencia, en cuyo caso es `Value^`. De forma similar, `GContainer` es el mismo que `Container` a menos que el segundo es un tipo de referencia, en cuyo caso es `Container^`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
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
|[queue::const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[queue::container_type (STL/CLR)](../dotnet/queue-container-type-stl-clr.md)|Tipo del contenedor subyacente.|  
|[queue::difference_type (STL/CLR)](../dotnet/queue-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el adaptador de contenedor.|  
|[queue::generic_value (STL/CLR)](../dotnet/queue-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el adaptador de contenedor.|  
|[queue::reference (STL/CLR)](../dotnet/queue-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[queue::size_type (STL/CLR)](../dotnet/queue-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[queue::back (STL/CLR)](../dotnet/queue-back-stl-clr.md)|Obtiene acceso al último elemento.|  
|[queue::empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)|Obtiene acceso al primer elemento.|  
|[queue::get_container (STL/CLR)](../dotnet/queue-get-container-stl-clr.md)|Se tiene acceso del contenedor subyacente.|  
|[queue::pop (STL/CLR)](../dotnet/queue-pop-stl-clr.md)|Quita el primer elemento.|  
|[queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)|Agrega un nuevo elemento de la última.|  
|[queue::queue (STL/CLR)](../dotnet/queue-queue-stl-clr.md)|Construye un objeto contenedor.|  
|[queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md)|Cuenta el número de elementos.|  
|[queue::to_array (STL/CLR)](../dotnet/queue-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
  
|Property|Descripción|  
|--------------|-----------------|  
|[queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)|Obtiene acceso al último elemento.|  
|[queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)|Obtiene acceso al primer elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator!= (queue) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)|Determina si un `queue` no es igual a otro objeto `queue` objeto.|  
|[operator< (queue) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)|Determina si un `queue` objeto es menor que otro `queue` objeto.|  
|[operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|Determina si un `queue` objeto es menor o igual que otro `queue` objeto.|  
|[operator== (queue) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)|Determina si un `queue` es igual a otro objeto `queue` objeto.|  
|[operator> (queue) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)|Determina si un `queue` es mayor que otro objeto `queue` objeto.|  
|[operator>= (queue) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|Determina si un `queue` objeto es mayor o igual que otro `queue` objeto.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|ICola\<valor, contenedor >|Mantener el adaptador de contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla a través de un contenedor subyacente, de tipo `Container`, que almacena `Value` elementos y crece a petición. El objeto restringe el acceso a tan solo presionar el primer elemento y retirar el último elemento, implementar un salir primero en la cola (también conocida como una cola FIFO o simplemente una cola).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/cola >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)