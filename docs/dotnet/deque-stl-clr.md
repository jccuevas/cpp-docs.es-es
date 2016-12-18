---
title: "deque (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/deque> (encabezado) [STL/CLR]"
  - "<deque> (encabezado) [STL/CLR]"
  - "deque (clase) [STL/CLR]"
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos que tiene acceso aleatorio.  Utiliza el contenedor `deque` para administrar una secuencia de elementos que parezca un bloque contiguo de almacenamiento, pero que puede crecer o reduzca en cualquier extremo sin necesidad de copiar cualquier elemento restante.  Así puede implementar eficazmente `double-ended queue`. \(Hence el nombre.\)  
  
 En la descripción siguiente, `GValue` es igual que `Value` a menos que este último es un tipo de referencia, en este caso es `Value^`.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 Coeficiente  
 El tipo genérico de un elemento de la secuencia controlada.  
  
 Valor  
 Tipo de un elemento de la secuencia controlada.  
  
## Miembros  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|[deque::const\_iterator](../dotnet/deque-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[deque::const\_reference](../dotnet/deque-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[deque::const\_reverse\_iterator](../dotnet/deque-const-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso constante para la secuencia controlada.|  
|[deque::difference\_type](../dotnet/deque-difference-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[deque::generic\_container](../dotnet/deque-generic-container-stl-clr.md)|El tipo de interfaz genérica para el contenedor.|  
|[deque::generic\_iterator](../dotnet/deque-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[deque::generic\_reverse\_iterator](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[deque::generic\_value](../dotnet/deque-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[deque::iterator](../dotnet/deque-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[deque::reference](../dotnet/deque-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[deque::reverse\_iterator](../dotnet/deque-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la secuencia controlada.|  
|[deque::size\_type](../dotnet/deque-size-type-stl-clr.md)|El tipo de una distancia con signo entre dos elementos.|  
|[deque::value\_type](../dotnet/deque-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[deque::assign](../dotnet/deque-assign-stl-clr.md)|Reemplaza todos los elementos.|  
|[deque::at](../dotnet/deque-at-stl-clr.md)|Tiene acceso a un elemento en una posición especificada.|  
|[deque::back](../dotnet/deque-back-stl-clr.md)|Tiene acceso al último elemento.|  
|[deque::begin](../dotnet/deque-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[deque::clear](../dotnet/deque-clear-stl-clr.md)|Quita todos los elementos.|  
|[deque::deque](../dotnet/deque-deque-stl-clr.md)|Construye un objeto contenedor.|  
|[deque::empty](../dotnet/deque-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[deque::end](../dotnet/deque-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[deque::erase](../dotnet/deque-erase-stl-clr.md)|Quita los elementos en las posiciones especificadas.|  
|[deque::front](../dotnet/deque-front-stl-clr.md)|Tiene acceso al primer elemento.|  
|[deque::insert](../dotnet/deque-insert-stl-clr.md)|Agrega elementos en una posición especificada.|  
|[deque::pop\_back](../dotnet/deque-pop-back-stl-clr.md)|Quita el último elemento.|  
|[deque::pop\_front](../dotnet/deque-pop-front-stl-clr.md)|Quita el primer elemento.|  
|[deque::push\_back](../dotnet/deque-push-back-stl-clr.md)|Agrega un nuevo elemento pasado.|  
|[deque::push\_front](../dotnet/deque-push-front-stl-clr.md)|Agrega un nuevo primero.|  
|[deque::rbegin](../dotnet/deque-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[deque::rend](../dotnet/deque-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[deque::resize](../dotnet/deque-resize-stl-clr.md)|Cambia el número de elementos.|  
|[deque::size](../dotnet/deque-size-stl-clr.md)|Cuenta el número de elementos.|  
|[deque::swap](../dotnet/deque-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[deque::to\_array](../dotnet/deque-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
  
|Propiedad|Descripción|  
|---------------|-----------------|  
|[deque::back\_item](../dotnet/deque-back-item-stl-clr.md)|Tiene acceso al último elemento.|  
|[deque::front\_item](../dotnet/deque-front-item-stl-clr.md)|Tiene acceso al primer elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[deque::operator\!\=](../dotnet/deque-operator-inequality-stl-clr.md)|Determina si dos objetos `deque` no son iguales.|  
|[deque::operator](../dotnet/deque-operator-stl-clr.md)|Tiene acceso a un elemento en una posición especificada.|  
|[operator\< \(deque\)](../dotnet/operator-less-than-deque-stl-clr.md)|Determina si un objeto de `deque` es menor que otro objeto de `deque` .|  
|[operator\<\= \(deque\)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|Determina si un objeto de `deque` menor o igual que otro objeto de `deque` .|  
|[operator\= \(deque\)](../dotnet/operator-assign-deque-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator\=\= \(deque\)](../dotnet/operator-equality-deque-stl-clr.md)|Determina si un objeto de `deque` es igual a otro objeto de `deque` .|  
|[operator\> \(deque\)](../dotnet/operator-greater-than-deque-stl-clr.md)|Determina si un objeto de `deque` es mayor que otro objeto de `deque` .|  
|[operator\>\= \(deque\)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|Determina si un objeto de `deque` mayor o igual que otro objeto de `deque` .|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantenga el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia mediante elementos escritos.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantenga el grupo de elementos escritos.|  
|<xref:System.Collections.Generic.IList%601>|Maintain pidió al grupo de elementos escritos.|  
|IDequeValue\<\>|Mantenga el contenedor genérico.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla con una matriz almacenado de identificadores que los bloques denominados de elementos de `Value` .  La matriz crece a petición.  El crecimiento aparece de manera que el costo de anteponiendo o de anexar un nuevo elemento sea tiempo constante, y no se perturba ningún elemento restantes.  También puede quitar un elemento en cualquier extremo en tiempo constante, y sin elementos restantes que modifican.  Así, un deque es un buen candidato al contenedor subyacente para la clase de plantilla [queue](../dotnet/queue-stl-clr.md) o clase de plantilla [pila](../dotnet/stack-stl-clr.md).  
  
 Un objeto de `deque` admite iteradores de acceso aleatorio, lo que significa que puede hacer referencia a un elemento determinado directamente su posición numérica, contando a desde cero para el primer elemento \(frontal\), a [deque::size](../dotnet/deque-size-stl-clr.md)`() - 1` para el elemento \(posterior\) pasado.  También significa que un deque es un buen candidato al contenedor subyacente para la clase de plantilla [priority\_queue](../dotnet/priority-queue-stl-clr.md).  
  
 Un iterador de deque almacena un identificador al objeto asociado de deque, así como la tendencia del elemento que señala.  Puede usar iteradores únicamente con los objetos contenedores asociados.  La tendencia de un elemento de deque es `not` necesariamente igual a su posición.  El primer elemento insertado tiene cero diagonal, el elemento anexado siguiente tiene 1 diagonal, pero el elemento work item siguiente tiene \-1 diagonal.  
  
 Insertar o eliminar elementos en cualquier extremo hace `not` modifica el valor de un elemento almacenado en cualquier tendencia válido.  Insertar o borrar un elemento interior, sin embargo, el cambio de `can` el valor del elemento almacenado en un tendencia determinado, por lo que el valor indicado por un iterador también puede cambiar. \(El contenedor se puede tener que copiar elementos arriba o abajo para crear un hueco antes de una inserción o para rellenar una vulnerabilidad después de un barrido.\) Sin embargo, un iterador de deque sigue siendo válido siempre y cuando la tendencia designa un elemento válido.  Por otra parte, un iterador válido permanece dereferencable \-\- puede utilizarlo para obtener acceso o modificar el valor del elemento que señala \-\- siempre y cuando la tendencia no es igual al tendencia para el iterador devuelto por `end()`.  
  
 Borrar o quitar un elemento denomina destructor por el valor almacenado.  Destruyendo el contenedor borra todos los elementos.  Así, un contenedor cuyo tipo de elemento es una clase de referencia se asegura que ningún elemento sobrevivan al contenedor.  La nota, sin embargo, que un contenedor de identificadores hace `not` destruye sus elementos.  
  
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [queue](../dotnet/queue-stl-clr.md)   
 [pila](../dotnet/stack-stl-clr.md)   
 [vector](../dotnet/vector-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)