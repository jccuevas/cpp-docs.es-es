---
title: "multimap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/map> (encabezado) [STL/CLR]"
  - "<map> (encabezado) [STL/CLR]"
  - "multimap (clase) [STL/CLR]"
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos con acceso bidireccional.  Utiliza el contenedor `multimap` para administrar una secuencia de elementos como \(casi\) equilibró el árbol orden de nodos, cada un elemento que almacena.  Un elemento se compone de una clave, para ordenar la secuencia, y un valor asignado, que va adelante para el recorrido.  
  
 En la descripción siguiente, `GValue` es igual que:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 donde:  
  
 `GKey` es igual que `Key` a menos que este último es un tipo de referencia, en este caso es `Key^`  
  
 `GMapped` es igual que `Mapped` a menos que este último es un tipo de referencia, en este caso es `Mapped^`  
  
## Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class multimap  
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
  
 Asignado  
 El tipo de componente adicional de un elemento de la secuencia controlada.  
  
## Miembros  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|[multimap::const\_iterator](../dotnet/multimap-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[multimap::const\_reference](../dotnet/multimap-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[multimap::const\_reverse\_iterator](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso constante para la secuencia controlada.|  
|[multimap::difference\_type](../dotnet/multimap-difference-type-stl-clr.md)|El tipo de distancia a \(firmada posiblemente\) entre dos elementos.|  
|[multimap::generic\_container](../dotnet/multimap-generic-container-stl-clr.md)|El tipo de interfaz genérica para el contenedor.|  
|[multimap::generic\_iterator](../dotnet/multimap-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[multimap::generic\_reverse\_iterator](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[multimap::generic\_value](../dotnet/multimap-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[multimap::iterator](../dotnet/multimap-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[multimap::key\_compare](../dotnet/multimap-key-compare-stl-clr.md)|El delegado de ordenación para dos claves.|  
|[multimap::key\_type](../dotnet/multimap-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[multimap::mapped\_type](../dotnet/multimap-mapped-type-stl-clr.md)|El tipo del valor asignado asociado a cada clave.|  
|[multimap::reference](../dotnet/multimap-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[multimap::reverse\_iterator](../dotnet/multimap-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la secuencia controlada.|  
|[multimap::size\_type](../dotnet/multimap-size-type-stl-clr.md)|El tipo de distancia \(no negativa\) de a entre dos elementos.|  
|[multimap::value\_compare](../dotnet/multimap-value-compare-stl-clr.md)|El delegado de ordenación por dos valores de elemento.|  
|[multimap::value\_type](../dotnet/multimap-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[multimap::begin](../dotnet/multimap-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[multimap::clear](../dotnet/multimap-clear-stl-clr.md)|Quita todos los elementos.|  
|[multimap::count](../dotnet/multimap-count-stl-clr.md)|Cuenta los elementos que coinciden con una clave especificada.|  
|[multimap::empty](../dotnet/multimap-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[multimap::end](../dotnet/multimap-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[multimap::equal\_range](../dotnet/multimap-equal-range-stl-clr.md)|Encuentra el intervalo que coincide con una clave especificada.|  
|[multimap::erase](../dotnet/multimap-erase-stl-clr.md)|Quita los elementos en las posiciones especificadas.|  
|[multimap::find](../dotnet/multimap-find-stl-clr.md)|Busca un elemento que coincida con una clave especificada.|  
|[multimap::insert](../dotnet/multimap-insert-stl-clr.md)|Agrega elementos.|  
|[multimap::key\_comp](../dotnet/multimap-key-comp-stl-clr.md)|Copia el delegado de ordenación para dos claves.|  
|[multimap::lower\_bound](../dotnet/multimap-lower-bound-stl-clr.md)|Encuentra el inicio del intervalo que coincide con una clave especificada.|  
|[multimap::make\_value](../dotnet/multimap-make-value-stl-clr.md)|Construye un objeto value.|  
|[multimap::multimap](../dotnet/multimap-multimap-stl-clr.md)|Construye un objeto contenedor.|  
|[multimap::rbegin](../dotnet/multimap-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[multimap::rend](../dotnet/multimap-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[multimap::size](../dotnet/multimap-size-stl-clr.md)|Cuenta el número de elementos.|  
|[multimap::swap](../dotnet/multimap-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[multimap::to\_array](../dotnet/multimap-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
|[multimap::upper\_bound](../dotnet/multimap-upper-bound-stl-clr.md)|Encuentra el final del intervalo que coincide con una clave especificada.|  
|[multimap::value\_comp](../dotnet/multimap-value-comp-stl-clr.md)|Copia el delegado de ordenación por dos valores de elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[multimap::operator\=](../dotnet/multimap-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator\!\= \(multimap\)](../dotnet/operator-inequality-multimap-stl-clr.md)|Determina si un objeto de `multimap` no es igual a otro objeto de `multimap` .|  
|[operator\< \(multimap\)](../dotnet/operator-less-than-multimap-stl-clr.md)|Determina si un objeto de `multimap` es menor que otro objeto de `multimap` .|  
|[operator\<\= \(multimap\)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|Determina si un objeto de `multimap` menor o igual que otro objeto de `multimap` .|  
|[operator\=\= \(multimap\)](../dotnet/operator-equality-multimap-stl-lr.md)|Determina si un objeto de `multimap` es igual a otro objeto de `multimap` .|  
|[operator\> \(multimap\)](../dotnet/operator-greater-than-multimap-stl-clr.md)|Determina si un objeto de `multimap` es mayor que otro objeto de `multimap` .|  
|[operator\>\= \(multimap\)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|Determina si un objeto de `multimap` mayor o igual que otro objeto de `multimap` .|  
  
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
  
 El objeto pide la secuencia que controla llamando a un objeto almacenado de delegado de [multimap::key\_compare](../dotnet/multimap-key-compare-stl-clr.md)escrito.  Puede especificar el objeto almacenado de delegado cuando se construye el multimap; si no especifica ningún objeto delegado, el valor predeterminado es la comparación `operator<(key_type, key_type)`.  Tiene acceso a este objeto almacenado llamando a la función [multimap::key\_comp](../dotnet/multimap-key-comp-stl-clr.md)`()`miembro.  
  
 Este tipo de objeto delegado debe imponer orden débil estricto sobre las teclas de [multimap::key\_type](../dotnet/multimap-key-type-stl-clr.md)escrito.  Es decir, para cualquier dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.  
  
 Si `key_comp()(X, Y)` es true, el `key_comp()(Y, X)` debe ser false.  
  
 Si `key_comp()(X, Y)` es true, el `X` se secuenciado antes de `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, el `X` y `Y` se dice que tienen orden equivalente.  
  
 Para cualquier elemento `X` que preceda `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. \(Para el objeto predeterminado de delegado, las teclas nunca disminuyen en valor.\) A diferencia de la clase de plantilla [map](../dotnet/map-stl-clr.md), un objeto de clase de plantilla `multimap` no requiere que las claves para todos los elementos son únicas. \(Dos o más claves pueden tener orden equivalente\).  
  
 Cada elemento contiene una clave independiente y un valor asignado.  La secuencia se representan de forma que permita búsqueda, la inserción, y la eliminación de un elemento arbitrario con varias operaciones proporcionales al logaritmo del número de elementos de la secuencia \(tiempo logarítmico\).  Por otra parte, inserta un elemento no invalida ningún iterador, y quitar un elemento reemplaza solo los iteradores que señalan en el elemento quitado.  
  
 Un multimap admite iteradores bidireccionales, que significa que se puede pasar a los elementos adyacentes dado un iterador que señale un elemento de la secuencia controlada.  Un nodo principal especial corresponde al iterador devuelto por [multimap::end](../dotnet/multimap-end-stl-clr.md)`()`.  Puede reducir este iterador para lograr el último elemento de la secuencia controlada, si existe.  Puede incrementar un iterador de multimap para lograr el nodo principal, y a continuación comparará el igual a `end()`.  Pero no puede desreferenciar el iterador devuelto por `end()`.  
  
 Observe que no puede hacer referencia a un elemento de multimap determinado directamente su posición numérica \-\- esto requiere un iterador de acceso aleatorio.  
  
 Un iterador de multimap almacena un identificador al nodo asociado de multimap, que a su vez almacena un identificador para el contenedor asociado.  Puede usar iteradores únicamente con los objetos contenedores asociados.  Un iterador de multimap sigue siendo válido siempre y cuando el nodo asociado de multimap está asociado a algún multimap.  Por otra parte, un iterador válido es dereferencable \-\- puede utilizarlo para obtener acceso o modificar el valor del elemento que señala \-\- siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento denomina destructor por el valor almacenado.  Destruyendo el contenedor borra todos los elementos.  Así, un contenedor cuyo tipo de elemento es una clase de referencia se asegura que ningún elemento sobrevivan al contenedor.  La nota, sin embargo, que un contenedor de identificadores hace `not` destruye sus elementos.  
  
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)