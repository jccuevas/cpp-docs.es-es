---
title: "hash_map (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/hash_map> (encabezado) [STL/CLR]"
  - "<hash_map> (encabezado) [STL/CLR]"
  - "hash_map (clase) [STL/CLR]"
ms.assetid: c3cfc69b-04c6-42ae-a30e-0eda953fe883
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos con acceso bidireccional.  Utiliza el contenedor `hash_map` para administrar una secuencia de elementos como una tabla hash, cada entrada de tabla almacenar una lista vinculada bidireccional de nodos, y cada nodo almacenando un elemento.  Un elemento se compone de una clave, para ordenar la secuencia, y un valor asignado, que va adelante para el recorrido.  
  
 En la descripción siguiente, `GValue` es igual que:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 donde:  
  
 `GKey` es igual que `Key` a menos que este último es un tipo de referencia, en este caso es `Key^`  
  
 `GMapped` es igual que `Mapped` a menos que este último es un tipo de referencia, en este caso es `Mapped^`  
  
## Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
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
|[hash\_map::const\_iterator](../dotnet/hash-map-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[hash\_map::const\_reference](../dotnet/hash-map-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[hash\_map::const\_reverse\_iterator](../dotnet/hash-map-const-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso constante para la secuencia controlada.|  
|[hash\_map::difference\_type](../dotnet/hash-map-difference-type-stl-clr.md)|El tipo de distancia a \(firmada posiblemente\) entre dos elementos.|  
|[hash\_map::generic\_container](../dotnet/hash-map-generic-container-stl-clr.md)|El tipo de interfaz genérica para el contenedor.|  
|[hash\_map::generic\_iterator](../dotnet/hash-map-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[hash\_map::generic\_reverse\_iterator](../dotnet/hash-map-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[hash\_map::generic\_value](../dotnet/hash-map-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[hash\_map::hasher](../dotnet/hash-map-hasher-stl-clr.md)|El delegado de hash para una clave.|  
|[hash\_map::iterator](../dotnet/hash-map-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[hash\_map::key\_compare](../dotnet/hash-map-key-compare-stl-clr.md)|El delegado de ordenación para dos claves.|  
|[hash\_map::key\_type](../dotnet/hash-map-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[hash\_map::mapped\_type](../dotnet/hash-map-mapped-type-stl-clr.md)|El tipo del valor asignado asociado a cada clave.|  
|[hash\_map::reference](../dotnet/hash-map-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[hash\_map::reverse\_iterator](../dotnet/hash-map-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la secuencia controlada.|  
|[hash\_map::size\_type](../dotnet/hash-map-size-type-stl-clr.md)|El tipo de distancia \(no negativa\) de a entre dos elementos.|  
|[hash\_map::value\_compare](../dotnet/hash-map-value-compare-stl-clr.md)|El delegado de ordenación por dos valores de elemento.|  
|[hash\_map::value\_type](../dotnet/hash-map-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[hash\_map::begin](../dotnet/hash-map-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[hash\_map::bucket\_count](../dotnet/hash-map-bucket-count-stl-clr.md)|Cuenta el número de depósitos.|  
|[hash\_map::clear](../dotnet/hash-map-clear-stl-clr.md)|Quita todos los elementos.|  
|[hash\_map::count](../dotnet/hash-map-count-stl-clr.md)|Cuenta los elementos que coinciden con una clave especificada.|  
|[hash\_map::empty](../dotnet/hash-map-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[hash\_map::end](../dotnet/hash-map-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[hash\_map::equal\_range](../dotnet/hash-map-equal-range-stl-clr.md)|Encuentra el intervalo que coincide con una clave especificada.|  
|[hash\_map::erase](../dotnet/hash-map-erase-stl-clr.md)|Quita los elementos en las posiciones especificadas.|  
|[hash\_map::find](../dotnet/hash-map-find-stl-clr.md)|Busca un elemento que coincida con una clave especificada.|  
|[hash\_map::hash\_delegate](../dotnet/hash-map-hash-delegate-stl-clr.md)|Copia el delegado de hash para una clave.|  
|[hash\_map::hash\_map](../dotnet/hash-map-hash-map-stl-clr.md)|Construye un objeto contenedor.|  
|[hash\_map::insert](../dotnet/hash-map-insert-stl-clr.md)|Agrega elementos.|  
|[hash\_map::key\_comp](../dotnet/hash-map-key-comp-stl-clr.md)|Copia el delegado de ordenación para dos claves.|  
|[hash\_map::load\_factor](../dotnet/hash-map-load-factor-stl-clr.md)|Cuenta los elementos multimedia por el depósito.|  
|[hash\_map::lower\_bound](../dotnet/hash-map-lower-bound-stl-clr.md)|Encuentra el inicio del intervalo que coincide con una clave especificada.|  
|[hash\_map::make\_value](../dotnet/hash-map-make-value-stl-clr.md)|Construye un objeto value.|  
|[hash\_map::max\_load\_factor](../dotnet/hash-map-max-load-factor-stl-clr.md)|Obtiene o establece elementos máximos por el depósito.|  
|[hash\_map::rbegin](../dotnet/hash-map-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[hash\_map::rehash](../dotnet/hash-map-rehash-stl-clr.md)|Recompila la tabla hash.|  
|[hash\_map::rend](../dotnet/hash-map-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[hash\_map::size](../dotnet/hash-map-size-stl-clr.md)|Cuenta el número de elementos.|  
|[hash\_map::swap](../dotnet/hash-map-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[hash\_map::to\_array](../dotnet/hash-map-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
|[hash\_map::upper\_bound](../dotnet/hash-map-upper-bound-stl-clr.md)|Encuentra el final del intervalo que coincide con una clave especificada.|  
|[hash\_map::value\_comp](../dotnet/hash-map-value-comp-stl-clr.md)|Copia el delegado de ordenación por dos valores de elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[hash\_map::operator\=](../dotnet/hash-map-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[hash\_map::operator](../dotnet/hash-map-operator-stl-clr.md)|Asigna una clave a su valor asignado asociado.|  
  
## Interfaces  
  
|Interfaz|Descripción|  
|--------------|-----------------|  
|<xref:System.ICloneable>|Dupliquen un objeto.|  
|<xref:System.Collections.IEnumerable>|Secuencia a través de los elementos.|  
|<xref:System.Collections.ICollection>|Mantenga el grupo de elementos.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Secuencia mediante elementos escritos.|  
|<xref:System.Collections.Generic.ICollection%601>|Mantenga el grupo de elementos escritos.|  
|<xref:System.Collections.Generic.IDictionary%602>|Mantenga el grupo {clave, valor} de pares.|  
|IHashKey\<, value\>|Mantenga el contenedor genérico.|  
  
## Comentarios  
 El objeto asigna y libera el almacenamiento de la secuencia que controla mientras los nodos individuales en una lista vinculada bidireccional.  El acceso de la velocidad, el objeto también mantiene una matriz de la variar\- longitud de punteros de la lista \(la tabla hash\), administrar eficazmente el conjunto aparece como secuencia de sublistas, o depósitos.  Nunca insertar elementos en un depósito mantener orden modificando los vínculos entre los nodos, copiando el contenido de un nodo a otro.  Eso significa que puede insertar y quitar elementos libremente sin elementos restantes que modifican.  
  
 El objeto orders cada depósito que controla llamando a un objeto almacenado de delegado de [hash\_set::key\_compare](../dotnet/hash-set-key-compare-stl-clr.md)escrito.  Puede especificar el objeto almacenado de delegado cuando se construye el hash\_set; si no especifica ningún objeto delegado, el valor predeterminado es la comparación `operator<=(key_type, key_type)`.  
  
 Tiene acceso al objeto almacenado de delegado llamando a la función [hash\_set::key\_comp](../dotnet/hash-set-key-comp-stl-clr.md)`()`miembro.  Este tipo de objeto delegado debe definir el equivalente de ordenación entre las teclas de [hash\_set::key\_type](../dotnet/hash-set-key-type-stl-clr.md)escrito.  Es decir, para cualquier dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.  
  
 Si `key_comp()(X, Y) && key_comp()(Y, X)` es true, el `X` y `Y` se dice que tienen orden equivalente.  
  
 Las reglas de ordenación que se comporte como `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` o `operator==(key_type, key_type)` define el orden eqivalent.  
  
 Observe que el contenedor garantiza sólo los elementos cuyas claves tienen equivalente de ordenación \(y que hash al mismo valor entero\) adyacentes en un depósito.  A diferencia de la clase de plantilla [hash\_multimap](../dotnet/hash-multimap-stl-clr.md), un objeto de clase de plantilla `hash_map` garantiza que las claves para todos los elementos son únicas. \(Ninguna dos claves tienen orden equivalente\).  
  
 El objeto determina qué depósito debe contener una clave de ordenación determinada llamando a un objeto almacenado de delegado de [hash\_set::hasher](../dotnet/hash-set-hasher-stl-clr.md)escrito.  Tiene acceso a este objeto almacenado llamando a la función [hash\_set::hash\_delegate](../dotnet/hash-set-hash-delegate-stl-clr.md)`()` miembro para obtener un valor entero que depende del valor de clave.  Puede especificar el objeto almacenado de delegado cuando se construye el hash\_set; si no especifica ningún objeto delegado, el valor predeterminado es la función `System::Object::hash_value(key_type)`.  Es decir, para cualquier clave `X` y `Y`:  
  
 `hash_delegate()(X)` devuelve el mismo resultado entero en cada llamada.  
  
 Si `X` y `Y` tiene ordenación equivalente, después `hash_delegate()(X)` debe devolver el mismo resultado entero que `hash_delegate()(Y)`.  
  
 Cada elemento contiene una clave independiente y un valor asignado.  La secuencia se representan de forma que permita búsqueda, la inserción, y la eliminación de un elemento arbitrario con varias operaciones que sea independiente del número de elementos de la secuencia \(tiempo constante\) \-\- por lo menos en el mejor de los casos.  Por otra parte, inserta un elemento no invalida ningún iterador, y quitar un elemento reemplaza solo los iteradores que señalan en el elemento quitado.  
  
 Si los valores hash no se distribuyen uniformemente, sin embargo, una tabla hash puede degenerar.  Al final \-\- para una función hash que siempre devuelve el mismo valor \-\- la búsqueda, la inserción, y la eliminación son proporcionales al número de elementos de la secuencia \(tiempo lineal\).  El contenedor se esfuerza para elegir una función hash razonable, un tamaño erróneo de depósito, y un tamaño de tabla hash \(número total de depósitos\), pero puede reemplazar cualquiera o todas estas opciones.  Vea, por ejemplo, las funciones [hash\_set::max\_load\_factor](../dotnet/hash-set-max-load-factor-stl-clr.md) y [hash\_set::rehash](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Un hash\_map admite iteradores bidireccionales, que significa que se puede pasar a los elementos adyacentes dado un iterador que señale un elemento de la secuencia controlada.  Un nodo principal especial corresponde al iterador devuelto por [hash\_map::end](../dotnet/hash-map-end-stl-clr.md)`()`.  Puede reducir este iterador para lograr el último elemento de la secuencia controlada, si existe.  Puede incrementar un iterador de hash\_map para lograr el nodo principal, y a continuación comparará el igual a `end()`.  Pero no puede desreferenciar el iterador devuelto por `end()`.  
  
 Observe que no puede hacer referencia a un elemento de hash\_map determinado directamente su posición numérica \-\- esto requiere un iterador de acceso aleatorio.  
  
 Un iterador de hash\_map almacena un identificador al nodo asociado de hash\_map, que a su vez almacena un identificador para el contenedor asociado.  Puede usar iteradores únicamente con los objetos contenedores asociados.  Un iterador de hash\_map sigue siendo válido siempre y cuando el nodo asociado de hash\_map está asociado a algún hash\_map.  Por otra parte, un iterador válido es dereferencable \-\- puede utilizarlo para obtener acceso o modificar el valor del elemento que señala \-\- siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento denomina destructor por el valor almacenado.  Destruyendo el contenedor borra todos los elementos.  Así, un contenedor cuyo tipo de elemento es una clase de referencia se asegura que ningún elemento sobrevivan al contenedor.  La nota, sin embargo, que un contenedor de identificadores hace `not` destruye sus elementos.  
  
## Requisitos  
 cliext \<\/hash\_map de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)