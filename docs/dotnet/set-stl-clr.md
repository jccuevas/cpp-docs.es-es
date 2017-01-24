---
title: "set (STL/CLR) | Microsoft Docs"
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
  - "cliext::set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/set> (encabezado) [STL/CLR]"
  - "<set> (encabezado) [STL/CLR]"
  - "set (clase) [STL/CLR]"
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos con acceso bidireccional.  Utiliza el contenedor `set` para administrar una secuencia de elementos como \(casi\) equilibró el árbol orden de nodos, cada un elemento que almacena.  
  
 En la descripción siguiente, `GValue` es igual que `GKey`, que a su vez es igual que `Key` a menos que este último es un tipo de referencia, en este caso es `Key^`.  
  
## Sintaxis  
  
```  
template<typename Key>  
    ref class set  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### Parámetros  
 Key  
 Tipo del componente clave de un elemento en la secuencia controlada.  
  
## Miembros  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|[set::const\_iterator](../dotnet/set-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[set::const\_reference](../dotnet/set-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[set::const\_reverse\_iterator](../dotnet/set-const-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso constante para la secuencia controlada.|  
|[set::difference\_type](../dotnet/set-difference-type-stl-clr.md)|El tipo de distancia a \(firmada posiblemente\) entre dos elementos.|  
|[set::generic\_container](../dotnet/set-generic-container-stl-clr.md)|El tipo de interfaz genérica para el contenedor.|  
|[set::generic\_iterator](../dotnet/set-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[set::generic\_reverse\_iterator](../dotnet/set-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[set::generic\_value](../dotnet/set-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[set::iterator](../dotnet/set-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[set::key\_compare](../dotnet/set-key-compare-stl-clr.md)|El delegado de ordenación para dos claves.|  
|[set::key\_type](../dotnet/set-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[set::reference](../dotnet/set-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[set::reverse\_iterator](../dotnet/set-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la secuencia controlada.|  
|[set::size\_type](../dotnet/set-size-type-stl-clr.md)|El tipo de distancia \(no negativa\) de a entre dos elementos.|  
|[set::value\_compare](../dotnet/set-value-compare-stl-clr.md)|El delegado de ordenación por dos valores de elemento.|  
|[set::value\_type](../dotnet/set-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[set::begin](../dotnet/set-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[set::clear](../dotnet/set-clear-stl-clr.md)|Quita todos los elementos.|  
|[set::count](../dotnet/set-count-stl-clr.md)|Cuenta los elementos que coinciden con una clave especificada.|  
|[set::empty](../dotnet/set-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[set::end](../dotnet/set-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[set::equal\_range](../dotnet/set-equal-range-stl-clr.md)|Encuentra el intervalo que coincide con una clave especificada.|  
|[set::erase](../dotnet/set-erase-stl-clr.md)|Quita los elementos en las posiciones especificadas.|  
|[set::find](../dotnet/set-find-stl-clr.md)|Busca un elemento que coincida con una clave especificada.|  
|[set::insert](../dotnet/set-insert-stl-clr.md)|Agrega elementos.|  
|[set::key\_comp](../dotnet/set-key-comp-stl-clr.md)|Copia el delegado de ordenación para dos claves.|  
|[set::lower\_bound](../dotnet/set-lower-bound-stl-clr.md)|Encuentra el inicio del intervalo que coincide con una clave especificada.|  
|[set::make\_value](../dotnet/set-make-value-stl-clr.md)|Construye un objeto value.|  
|[set::rbegin](../dotnet/set-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[set::rend](../dotnet/set-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[set::set](../dotnet/set-set-stl-clr.md)|Construye un objeto contenedor.|  
|[set::size](../dotnet/set-size-stl-clr.md)|Cuenta el número de elementos.|  
|[set::swap](../dotnet/set-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[set::to\_array](../dotnet/set-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
|[set::upper\_bound](../dotnet/set-upper-bound-stl-clr.md)|Encuentra el final del intervalo que coincide con una clave especificada.|  
|[set::value\_comp](../dotnet/set-value-comp-stl-clr.md)|Copia el delegado de ordenación por dos valores de elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[set::operator\=](../dotnet/set-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator\!\= \(set\)](../dotnet/operator-inequality-set-stl-clr.md)|Determina si un objeto de `set` no es igual a otro objeto de `set` .|  
|[operator\< \(set\)](../dotnet/operator-less-than-set-stl-clr.md)|Determina si un objeto de `set` es menor que otro objeto de `set` .|  
|[operator\<\= \(set\)](../dotnet/operator-less-or-equal-set-stl-clr.md)|Determina si un objeto de `set` menor o igual que otro objeto de `set` .|  
|[operator\=\= \(set\)](../dotnet/operator-equality-set-stl-clr.md)|Determina si un objeto de `set` es igual a otro objeto de `set` .|  
|[operator\> \(set\)](../dotnet/operator-greater-than-set-stl-clr.md)|Determina si un objeto de `set` es mayor que otro objeto de `set` .|  
|[operator\>\= \(set\)](../dotnet/operator-greater-or-equal-set-stl-clr.md)|Determina si un objeto de `set` mayor o igual que otro objeto de `set` .|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantenga el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia mediante elementos escritos.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantenga el grupo de elementos escritos.|  
|ITreeKey\<, value\>|Mantenga el contenedor genérico.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla como nodos individuales.  Insertar elementos en \(casi\) nunca equilibró el árbol que mantiene orden modificando los vínculos entre los nodos, copiando el contenido de un nodo a otro.  Eso significa que puede insertar y quitar elementos libremente sin elementos restantes que modifican.  
  
 El objeto pide la secuencia que controla llamando a un objeto almacenado de delegado de [set::key\_compare](../dotnet/set-key-compare-stl-clr.md)escrito.  Puede especificar el objeto almacenado de delegado al crear el conjunto; si no especifica ningún objeto delegado, el valor predeterminado es la comparación `operator<(key_type, key_type)`.  Tiene acceso a este objeto almacenado llamando a la función [set::key\_comp](../dotnet/set-key-comp-stl-clr.md)`()`miembro.  
  
 Este tipo de objeto delegado debe imponer orden débil estricto sobre las teclas de [set::key\_type](../dotnet/set-key-type-stl-clr.md)escrito.  Es decir, para cualquier dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.  
  
 Si `key_comp()(X, Y)` es true, el `key_comp()(Y, X)` debe ser false.  
  
 Si `key_comp()(X, Y)` es true, el `X` se secuenciado antes de `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, el `X` y `Y` se dice que tienen orden equivalente.  
  
 Para cualquier elemento `X` que preceda `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. \(Para el objeto predeterminado de delegado, las teclas nunca disminuyen en valor.\) A diferencia de la clase de plantilla [set](../dotnet/set-stl-clr.md), un objeto de clase de plantilla `set` no requiere que las claves para todos los elementos son únicas. \(Dos o más claves pueden tener orden equivalente\).  
  
 Cada elemento actúa como un ey y valor.  La secuencia se representan de forma que permita búsqueda, la inserción, y la eliminación de un elemento arbitrario con varias operaciones proporcionales al logaritmo del número de elementos de la secuencia \(tiempo logarítmico\).  Por otra parte, inserta un elemento no invalida ningún iterador, y quitar un elemento reemplaza solo los iteradores que señalan en el elemento quitado.  
  
 Un conjunto admite iteradores bidireccionales, que significa que se puede pasar a los elementos adyacentes dado un iterador que señale un elemento de la secuencia controlada.  Un nodo principal especial corresponde al iterador devuelto por [set::end](../dotnet/set-end-stl-clr.md)`()`.  Puede reducir este iterador para lograr el último elemento de la secuencia controlada, si existe.  Puede aumentar un iterador determinado para lograr el nodo principal, y a continuación comparará el igual a `end()`.  Pero no puede desreferenciar el iterador devuelto por `end()`.  
  
 Observe que no puede hacer referencia a un elemento determinado determinado directamente su posición numérica \-\- esto requiere un iterador de acceso aleatorio.  
  
 Un iterador set almacena un identificador al nodo determinado asociado, que a su vez almacena un identificador para el contenedor asociado.  Puede usar iteradores únicamente con los objetos contenedores asociados.  Un iterador determinado sigue siendo válido siempre y cuando el nodo determinado asociado está asociado a un determinado de conjunto.  Por otra parte, un iterador válido es dereferencable \-\- puede utilizarlo para obtener acceso o modificar el valor del elemento que señala \-\- siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento denomina destructor por el valor almacenado.  Destruyendo el contenedor borra todos los elementos.  Así, un contenedor cuyo tipo de elemento es una clase de referencia se asegura que ningún elemento sobrevivan al contenedor.  La nota, sin embargo, que un contenedor de identificadores hace `not` destruye sus elementos.  
  
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)