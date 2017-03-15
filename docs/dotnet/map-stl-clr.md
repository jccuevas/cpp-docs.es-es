---
title: "map (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/map> (encabezado) [STL/CLR]"
  - "<map> (encabezado) [STL/CLR]"
  - "map (clase) [STL/CLR]"
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos con acceso bidireccional.  Utiliza el contenedor `map` para administrar una secuencia de elementos como \(casi\) equilibró el árbol orden de nodos, cada un elemento que almacena.  Un elemento se compone de una clave, para ordenar la secuencia, y un valor asignado, que va adelante para el recorrido.  
  
 En la descripción siguiente, `GValue` es igual que:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 donde:  
  
 `GKey` es igual que `Key` a menos que este último es un tipo de referencia, en este caso es `Key^`  
  
 `GMapped` es igual que `Mapped` a menos que este último es un tipo de referencia, en este caso es `Mapped^`  
  
## Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
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
|[map::const\_iterator](../dotnet/map-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[map::const\_reference](../dotnet/map-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[map::const\_reverse\_iterator](../dotnet/map-const-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso constante para la secuencia controlada.|  
|[map::difference\_type](../dotnet/map-difference-type-stl-clr.md)|El tipo de distancia a \(firmada posiblemente\) entre dos elementos.|  
|[map::generic\_container](../dotnet/map-generic-container-stl-clr.md)|El tipo de interfaz genérica para el contenedor.|  
|[map::generic\_iterator](../dotnet/map-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[map::generic\_reverse\_iterator](../dotnet/map-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[map::generic\_value](../dotnet/map-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[map::iterator](../dotnet/map-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[map::key\_compare](../dotnet/map-key-compare-stl-clr.md)|El delegado de ordenación para dos claves.|  
|[map::key\_type](../dotnet/map-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[map::mapped\_type](../dotnet/map-mapped-type-stl-clr.md)|El tipo del valor asignado asociado a cada clave.|  
|[map::reference](../dotnet/map-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[map::reverse\_iterator](../dotnet/map-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la secuencia controlada.|  
|[map::size\_type](../dotnet/map-size-type-stl-clr.md)|El tipo de distancia \(no negativa\) de a entre dos elementos.|  
|[map::value\_compare](../dotnet/map-value-compare-stl-clr.md)|El delegado de ordenación por dos valores de elemento.|  
|[map::value\_type](../dotnet/map-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[map::begin](../dotnet/map-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[map::clear](../dotnet/map-clear-stl-clr.md)|Quita todos los elementos.|  
|[map::count](../dotnet/map-count-stl-clr.md)|Cuenta los elementos que coinciden con una clave especificada.|  
|[map::empty](../dotnet/map-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[map::end](../dotnet/map-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[map::equal\_range](../dotnet/map-equal-range-stl-clr.md)|Encuentra el intervalo que coincide con una clave especificada.|  
|[map::erase](../dotnet/map-erase-stl-clr.md)|Quita los elementos en las posiciones especificadas.|  
|[map::find](../dotnet/map-find-stl-clr.md)|Busca un elemento que coincida con una clave especificada.|  
|[map::insert](../dotnet/map-insert-stl-clr.md)|Agrega elementos.|  
|[map::key\_comp](../dotnet/map-key-comp-stl-clr.md)|Copia el delegado de ordenación para dos claves.|  
|[map::lower\_bound](../dotnet/map-lower-bound-stl-clr.md)|Encuentra el inicio del intervalo que coincide con una clave especificada.|  
|[map::make\_value](../dotnet/map-make-value-stl-clr.md)|Construye un objeto value.|  
|[map::map](../dotnet/map-map-stl-clr.md)|Construye un objeto contenedor.|  
|[map::rbegin](../dotnet/map-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[map::rend](../dotnet/map-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[map::size](../dotnet/map-size-stl-clr.md)|Cuenta el número de elementos.|  
|[map::swap](../dotnet/map-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[map::to\_array](../dotnet/map-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
|[map::upper\_bound](../dotnet/map-upper-bound-stl-clr.md)|Encuentra el final del intervalo que coincide con una clave especificada.|  
|[map::value\_comp](../dotnet/map-value-comp-stl-clr.md)|Copia el delegado de ordenación por dos valores de elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[map::operator\=](../dotnet/map-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[map::operator](../dotnet/map-operator-stl-clr.md)|Asigna una clave a su valor asignado asociado.|  
|[operator\!\= \(map\)](../dotnet/operator-inequality-map-stl-clr.md)|Determina si un objeto de `map` no es igual a otro objeto de `map` .|  
|[operator\< \(map\)](../dotnet/operator-less-than-map-stl-clr.md)|Determina si un objeto de `map` es menor que otro objeto de `map` .|  
|[operator\<\= \(map\)](../dotnet/operator-less-or-equal-map-stl-clr.md)|Determina si un objeto de `map` menor o igual que otro objeto de `map` .|  
|[operator\=\= \(map\)](../dotnet/operator-equality-map-stl-clr.md)|Determina si un objeto de `map` es igual a otro objeto de `map` .|  
|[operator\> \(map\)](../dotnet/operator-greater-than-map-stl-clr.md)|Determina si un objeto de `map` es mayor que otro objeto de `map` .|  
|[operator\>\= \(map\)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|Determina si un objeto de `map` mayor o igual que otro objeto de `map` .|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantenga el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia mediante elementos escritos.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantenga el grupo de elementos escritos.|  
|<xref:System.Collections.Generic.IDictionary%602>|Mantenga el grupo {clave, valor} de pares.|  
|ITreeKey\<, value\>|Mantenga el contenedor genérico.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla como nodos individuales.  Insertar elementos en \(casi\) nunca equilibró el árbol que mantiene orden modificando los vínculos entre los nodos, copiando el contenido de un nodo a otro.  Eso significa que puede insertar y quitar elementos libremente sin elementos restantes que modifican.  
  
 El objeto pide la secuencia que controla llamando a un objeto almacenado de delegado de [map::key\_compare](../dotnet/map-key-compare-stl-clr.md)escrito.  Puede especificar el objeto almacenado de delegado cuando se construye el mapa; si no especifica ningún objeto delegado, el valor predeterminado es la comparación `operator<(key_type, key_type)`.  Tiene acceso a este objeto almacenado llamando a la función [map::key\_comp](../dotnet/map-key-comp-stl-clr.md)`()`miembro.  
  
 Este tipo de objeto delegado debe imponer orden débil estricto sobre las teclas de [map::key\_type](../dotnet/map-key-type-stl-clr.md)escrito.  Es decir, para cualquier dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.  
  
 Si `key_comp()(X, Y)` es true, el `key_comp()(Y, X)` debe ser false.  
  
 Si `key_comp()(X, Y)` es true, el `X` se secuenciado antes de `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, el `X` y `Y` se dice que tienen orden equivalente.  
  
 Para cualquier elemento `X` que preceda `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. \(Para el objeto predeterminado de delegado, las teclas nunca disminuyen en valor.\) A diferencia de la clase de plantilla [map](../dotnet/map-stl-clr.md), un objeto de clase de plantilla `map` no requiere que las claves para todos los elementos son únicas. \(Dos o más claves pueden tener orden equivalente\).  
  
 Cada elemento contiene una clave independiente y un valor asignado.  La secuencia se representan de forma que permita búsqueda, la inserción, y la eliminación de un elemento arbitrario con varias operaciones proporcionales al logaritmo del número de elementos de la secuencia \(tiempo logarítmico\).  Por otra parte, inserta un elemento no invalida ningún iterador, y quitar un elemento reemplaza solo los iteradores que señalan en el elemento quitado.  
  
 Un mapa admite iteradores bidireccionales, que significa que se puede pasar a los elementos adyacentes dado un iterador que señale un elemento de la secuencia controlada.  Un nodo principal especial corresponde al iterador devuelto por [map::end](../dotnet/map-end-stl-clr.md)`()`.  Puede reducir este iterador para lograr el último elemento de la secuencia controlada, si existe.  Puede incrementar un iterador de mapa para lograr el nodo principal, y a continuación comparará el igual a `end()`.  Pero no puede desreferenciar el iterador devuelto por `end()`.  
  
 Observe que no puede hacer referencia a un elemento de mapa determinado directamente su posición numérica \-\- esto requiere un iterador de acceso aleatorio.  
  
 Un iterador de mapa almacena un identificador al nodo asociado del mapa, que a su vez almacena un identificador para el contenedor asociado.  Puede usar iteradores únicamente con los objetos contenedores asociados.  Un iterador de mapa sigue siendo válido siempre y cuando el nodo asociado del mapa se asocia al mapa.  Por otra parte, un iterador válido es dereferencable \-\- puede utilizarlo para obtener acceso o modificar el valor del elemento que señala \-\- siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento denomina destructor por el valor almacenado.  Destruyendo el contenedor borra todos los elementos.  Así, un contenedor cuyo tipo de elemento es una clase de referencia se asegura que ningún elemento sobrevivan al contenedor.  La nota, sin embargo, que un contenedor de identificadores hace `not` destruye sus elementos.  
  
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)