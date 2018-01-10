---
title: pila (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack
dev_langs: C++
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c7f6d9eac97fa1907a0901c725645f29dcdd5d9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="stack-stlclr"></a>stack (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tenga acceso a la última en salir. Usar el adaptador de contenedor `stack` para administrar un contenedor subyacente como una pila de inserción.  
  
 En la descripción siguiente, `GValue` es el mismo que `Value` a menos que el segundo es un tipo de referencia, en cuyo caso es `Value^`. De forma similar, `GContainer` es el mismo que `Container` a menos que el segundo es un tipo de referencia, en cuyo caso es `Container^`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
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
|[stack::const_reference (STL/CLR)](../dotnet/stack-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[stack::container_type (STL/CLR)](../dotnet/stack-container-type-stl-clr.md)|Tipo del contenedor subyacente.|  
|[stack::difference_type (STL/CLR)](../dotnet/stack-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[stack::generic_container (STL/CLR)](../dotnet/stack-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el adaptador de contenedor.|  
|[stack::generic_value (STL/CLR)](../dotnet/stack-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el adaptador de contenedor.|  
|[stack::reference (STL/CLR)](../dotnet/stack-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[stack::size_type (STL/CLR)](../dotnet/stack-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[stack::value_type (STL/CLR)](../dotnet/stack-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[stack::assign (STL/CLR)](../dotnet/stack-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[stack::empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[stack::get_container (STL/CLR)](../dotnet/stack-get-container-stl-clr.md)|Se tiene acceso del contenedor subyacente.|  
|[stack::pop (STL/CLR)](../dotnet/stack-pop-stl-clr.md)|Quita el último elemento.|  
|[stack::push (STL/CLR)](../dotnet/stack-push-stl-clr.md)|Agrega un nuevo elemento de la última.|  
|[stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)|Cuenta el número de elementos.|  
|[stack::stack (STL/CLR)](../dotnet/stack-stack-stl-clr.md)|Construye un objeto contenedor.|  
|[stack::top (STL/CLR)](../dotnet/stack-top-stl-clr.md)|Obtiene acceso al último elemento.|  
|[stack::to_array (STL/CLR)](../dotnet/stack-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
  
|Property|Descripción|  
|--------------|-----------------|  
|[stack::top_item (STL/CLR)](../dotnet/stack-top-item-stl-clr.md)|Obtiene acceso al último elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[stack::operator= (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator!= (stack) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)|Determina si un `stack` no es igual a otro objeto `stack` objeto.|  
|[operator< (stack) (STL/CLR)](../dotnet/operator-less-than-stack-stl-clr.md)|Determina si un `stack` objeto es menor que otro `stack` objeto.|  
|[operator<= (stack) (STL/CLR)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|Determina si un `stack` objeto es menor o igual que otro `stack` objeto.|  
|[operator== (stack) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)|Determina si un `stack` es igual a otro objeto `stack` objeto.|  
|[operator> (stack) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)|Determina si un `stack` es mayor que otro objeto `stack` objeto.|  
|[operator>= (stack) (STL/CLR)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|Determina si un `stack` objeto es mayor o igual que otro `stack` objeto.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|IStack\<valor, contenedor >|Mantener el adaptador de contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla a través de un contenedor subyacente, de tipo `Container`, que almacena `Value` elementos y crece a petición. El objeto restringe el acceso a insertar y retirar solo el último elemento, la implementación de una cola de último en entrar en salir (también conocido como una cola de LIFO o pila).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/pila >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [cola (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)