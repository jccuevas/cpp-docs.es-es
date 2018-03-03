---
title: deque (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::deque
dev_langs:
- C++
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9bd847b2641e6670a91d2edf1eb926aca423ad2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="deque-stlclr"></a>deque (STL/CLR)
La clase de plantilla describe un objeto que controla una secuencia de longitud variable de elementos que tiene acceso aleatorio. Utilice el contenedor de `deque` para administrar una secuencia de elementos que es similar a un bloque contiguo de almacenamiento, pero que puede aumentar o reducir en cualquiera de los extremos sin necesidad de copiar los elementos restantes. Lo que puede implementar eficazmente un `double-ended queue`. (Por lo tanto, el nombre.)  
  
 En la descripción siguiente, `GValue` es el mismo que `Value` a menos que el segundo es un tipo de referencia, en cuyo caso es `Value^`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value>  
    ref class deque  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IDeque<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parámetros  
 GValue  
 El tipo genérico de un elemento de la secuencia controlada.  
  
 Valor  
 Tipo de un elemento de la secuencia controlada.  
  
## <a name="members"></a>Miembros  
  
|Definición de tipo|Descripción|  
|---------------------|-----------------|  
|[deque::const_iterator (STL/CLR)](../dotnet/deque-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[deque::const_reference (STL/CLR)](../dotnet/deque-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[deque::const_reverse_iterator (STL/CLR)](../dotnet/deque-const-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido constante para la secuencia controlada.|  
|[deque::difference_type (STL/CLR)](../dotnet/deque-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)|El tipo de la interfaz genérica para el contenedor.|  
|[deque::generic_iterator (STL/CLR)](../dotnet/deque-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[deque::generic_reverse_iterator (STL/CLR)](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[deque::generic_value (STL/CLR)](../dotnet/deque-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[deque::iterator (STL/CLR)](../dotnet/deque-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[deque::reference (STL/CLR)](../dotnet/deque-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[deque::reverse_iterator (STL/CLR)](../dotnet/deque-reverse-iterator-stl-clr.md)|El tipo de un iterador invertido para la secuencia controlada.|  
|[deque::size_type (STL/CLR)](../dotnet/deque-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[deque::value_type (STL/CLR)](../dotnet/deque-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función miembro|Descripción|  
|---------------------|-----------------|  
|[deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[deque::at (STL/CLR)](../dotnet/deque-at-stl-clr.md)|Obtiene acceso a un elemento en una posición especificada.|  
|[deque::back (STL/CLR)](../dotnet/deque-back-stl-clr.md)|Obtiene acceso al último elemento.|  
|[deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[deque::clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)|Quita todos los elementos.|  
|[deque::deque (STL/CLR)](../dotnet/deque-deque-stl-clr.md)|Construye un objeto contenedor.|  
|[deque::empty (STL/CLR)](../dotnet/deque-empty-stl-clr.md)|Comprueba si no hay ningún elemento presente.|  
|[deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)|Quita los elementos de las posiciones especificadas.|  
|[deque::front (STL/CLR)](../dotnet/deque-front-stl-clr.md)|Obtiene acceso al primer elemento.|  
|[deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)|Agrega un elemento en una posición especificada.|  
|[deque::pop_back (STL/CLR)](../dotnet/deque-pop-back-stl-clr.md)|Quita el último elemento.|  
|[deque::pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)|Quita el primer elemento.|  
|[deque::push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)|Agrega un nuevo elemento de la última.|  
|[deque::push_front (STL/CLR)](../dotnet/deque-push-front-stl-clr.md)|Agrega un nuevo primer elemento.|  
|[deque::rbegin (STL/CLR)](../dotnet/deque-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[deque::rend (STL/CLR)](../dotnet/deque-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[deque::resize (STL/CLR)](../dotnet/deque-resize-stl-clr.md)|Cambia el número de elementos.|  
|[deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md)|Cuenta el número de elementos.|  
|[deque::swap (STL/CLR)](../dotnet/deque-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[deque::to_array (STL/CLR)](../dotnet/deque-to-array-stl-clr.md)|Copia la secuencia controlada en una nueva matriz.|  
  
|Property|Descripción|  
|--------------|-----------------|  
|[deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)|Obtiene acceso al último elemento.|  
|[deque::front_item (STL/CLR)](../dotnet/deque-front-item-stl-clr.md)|Obtiene acceso al primer elemento.|  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[deque::operator!= (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)|Determina si dos `deque` objetos no son iguales.|  
|[deque::operator(STL/CLR)](../dotnet/deque-operator-stl-clr.md)|Obtiene acceso a un elemento en una posición especificada.|  
|[operator< (deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)|Determina si un `deque` objeto es menor que otro `deque` objeto.|  
|[operator<= (deque) (STL/CLR)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|Determina si un `deque` objeto es menor o igual que otro `deque` objeto.|  
|[operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator== (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)|Determina si un `deque` es igual a otro objeto `deque` objeto.|  
|[operator> (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)|Determina si un `deque` es mayor que otro objeto `deque` objeto.|  
|[operator>= (deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|Determina si un `deque` objeto es mayor o igual que otro `deque` objeto.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interfaz|Descripción|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicar un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantener el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia a través de los elementos con tipo.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantener el grupo de elementos con tipo.|  
|<xref:System.Collections.Generic.IList%601>|Mantener un grupo ordenado de elementos con tipo.|  
|IDeque < valor\>|Mantener contenedor genérico.|  
  
## <a name="remarks"></a>Comentarios  
 El objeto asigna y libera almacenamiento para la secuencia que controla a través de una matriz de identificadores que designan los bloques de almacenado `Value` elementos. La matriz aumenta de tamaño a petición. El crecimiento tiene lugar de tal manera que el costo de anteponiendo o anexar un nuevo elemento es tiempo constante y no quedan elementos se ven afectados. También puede quitar un elemento en cualquier extremo en tiempo constante y sin alterar los elementos restantes. Por lo tanto, un deque es un buen candidato para el contenedor subyacente para la clase de plantilla [cola (STL/CLR)](../dotnet/queue-stl-clr.md) o clase de plantilla [(STL/CLR) de la pila](../dotnet/stack-stl-clr.md).  
  
 A `deque` objeto admite iteradores de acceso aleatorio, lo que significa que puede hacer referencia a un elemento directamente según su posición numérica, contando desde cero para el primer elemento (frontal), para [deque (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() - 1` para el último elemento (atrás). También significa que un deque es un buen candidato para el contenedor subyacente para la clase de plantilla [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Un iterador de deque almacena un identificador a su objeto deque asociado, junto con la diferencia del elemento que este designa. Sólo puede usar iteradores con sus objetos de contenedor asociado. Es la diferencia de un elemento de deque `not` necesariamente igual a su posición. El primer elemento que se insertan con desviación del cero, el siguiente elemento anexado tiene compensación de 1, pero el siguiente elemento antepuesto tiene compensación de -1.  
  
 Insertar o borrar elementos en cualquier extremo hace `not` modificar el valor de un elemento almacenado en cualquier diferencia válido. Insertar o borrar un elemento interior, sin embargo, `can` cambiar el valor del elemento almacenado en un sesgo determinado, por lo que también puede cambiar el valor designado por un iterador. (El contenedor puede tener que copiar los elementos de seguridad o hacia abajo para crear un "agujero" antes de una instrucción insert o para rellenar un "agujero" después de un borrado). Sin embargo, un iterador deque sigue siendo válido siempre y cuando su diferencia designa un elemento válido. Además, un iterador válido permanece dereferencable: se puede utilizar para tener acceso o modificar el valor del elemento designa--siempre y cuando su diferencia no es igual a la diferencia para el iterador devuelto por `end()`.  
  
 Borrar o quitar un elemento llama al destructor para definir el valor almacenado. Destruir el contenedor, borrará todos los elementos. Por lo tanto, un contenedor cuyo tipo de elemento es una clase ref garantiza que ningún elemento su duración mayor que el contenedor. Sin embargo, tenga en cuenta que un contenedor de identificadores no `not` destruir sus elementos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/deque >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [cola (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Referencia de la biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)