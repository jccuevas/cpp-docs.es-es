---
title: "multiset (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/set> (encabezado) [STL/CLR]"
  - "<set> (encabezado) [STL/CLR]"
  - "multiset (clase) [STL/CLR]"
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que controla una secuencia de la variar\- longitud de elementos con acceso bidireccional.  Utiliza el contenedor `multiset` para administrar una secuencia de elementos como \(casi\) equilibró el árbol orden de nodos, cada un elemento que almacena.  
  
 En la descripción siguiente, `GValue` es igual que `GKey`, que a su vez es igual que `Key` a menos que este último es un tipo de referencia, en este caso es `Key^`.  
  
## Sintaxis  
  
```  
template<typename Key>  
    ref class multiset  
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
|[multiset::const\_iterator](../dotnet/multiset-const-iterator-stl-clr.md)|El tipo de un iterador constante para la secuencia controlada.|  
|[multiset::const\_reference](../dotnet/multiset-const-reference-stl-clr.md)|El tipo de una referencia constante a un elemento.|  
|[multiset::const\_reverse\_iterator](../dotnet/multiset-const-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso constante para la secuencia controlada.|  
|[multiset::difference\_type](../dotnet/multiset-difference-type-stl-clr.md)|El tipo de distancia a \(firmada posiblemente\) entre dos elementos.|  
|[multiset::generic\_container](../dotnet/multiset-generic-container-stl-clr.md)|El tipo de interfaz genérica para el contenedor.|  
|[multiset::generic\_iterator](../dotnet/multiset-generic-iterator-stl-clr.md)|El tipo de un iterador para la interfaz genérica para el contenedor.|  
|[multiset::generic\_reverse\_iterator](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la interfaz genérica para el contenedor.|  
|[multiset::generic\_value](../dotnet/multiset-generic-value-stl-clr.md)|El tipo de un elemento de la interfaz genérica para el contenedor.|  
|[multiset::iterator](../dotnet/multiset-iterator-stl-clr.md)|El tipo de un iterador para la secuencia controlada.|  
|[multiset::key\_compare](../dotnet/multiset-key-compare-stl-clr.md)|El delegado de ordenación para dos claves.|  
|[multiset::key\_type](../dotnet/multiset-key-type-stl-clr.md)|El tipo de una clave de ordenación.|  
|[multiset::reference](../dotnet/multiset-reference-stl-clr.md)|El tipo de una referencia a un elemento.|  
|[multiset::reverse\_iterator](../dotnet/multiset-reverse-iterator-stl-clr.md)|El tipo de un iterador inverso para la secuencia controlada.|  
|[multiset::size\_type](../dotnet/multiset-size-type-stl-clr.md)|El tipo de distancia \(no negativa\) de a entre dos elementos.|  
|[multiset::value\_compare](../dotnet/multiset-value-compare-stl-clr.md)|El delegado de ordenación por dos valores de elemento.|  
|[multiset::value\_type](../dotnet/multiset-value-type-stl-clr.md)|El tipo de un elemento.|  
  
|Función de miembro|Descripción|  
|------------------------|-----------------|  
|[multiset::begin](../dotnet/multiset-begin-stl-clr.md)|Designa el principio de la secuencia controlada.|  
|[multiset::clear](../dotnet/multiset-clear-stl-clr.md)|Quita todos los elementos.|  
|[multiset::count](../dotnet/multiset-count-stl-clr.md)|Cuenta los elementos que coinciden con una clave especificada.|  
|[multiset::empty](../dotnet/multiset-empty-stl-clr.md)|Comprueba si no hay elementos presentes.|  
|[multiset::end](../dotnet/multiset-end-stl-clr.md)|Designa el final de la secuencia controlada.|  
|[multiset::equal\_range](../dotnet/multiset-equal-range-stl-clr.md)|Encuentra el intervalo que coincide con una clave especificada.|  
|[multiset::erase](../dotnet/multiset-erase-stl-clr.md)|Quita los elementos en las posiciones especificadas.|  
|[multiset::find](../dotnet/multiset-find-stl-clr.md)|Busca un elemento que coincida con una clave especificada.|  
|[multiset::insert](../dotnet/multiset-insert-stl-clr.md)|Agrega elementos.|  
|[multiset::key\_comp](../dotnet/multiset-key-comp-stl-clr.md)|Copia el delegado de ordenación para dos claves.|  
|[multiset::lower\_bound](../dotnet/multiset-lower-bound-stl-clr.md)|Encuentra el inicio del intervalo que coincide con una clave especificada.|  
|[multiset::make\_value](../dotnet/multiset-make-value-stl-clr.md)|Construye un objeto value.|  
|[multiset::multiset](../dotnet/multiset-multiset-stl-clr.md)|Construye un objeto contenedor.|  
|[multiset::rbegin](../dotnet/multiset-rbegin-stl-clr.md)|Designa el principio de la secuencia controlada inversa.|  
|[multiset::rend](../dotnet/multiset-rend-stl-clr.md)|Designa el final de la secuencia controlada inversa.|  
|[multiset::size](../dotnet/multiset-size-stl-clr.md)|Cuenta el número de elementos.|  
|[multiset::swap](../dotnet/multiset-swap-stl-clr.md)|Intercambia el contenido de dos contenedores.|  
|[multiset::to\_array](../dotnet/multiset-to-array-stl-clr.md)|Copia la secuencia controlada a una nueva matriz.|  
|[multiset::upper\_bound](../dotnet/multiset-upper-bound-stl-clr.md)|Encuentra el final del intervalo que coincide con una clave especificada.|  
|[multiset::value\_comp](../dotnet/multiset-value-comp-stl-clr.md)|Copia el delegado de ordenación por dos valores de elemento.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|[multiset::operator\=](../dotnet/multiset-operator-assign-stl-clr.md)|Reemplaza la secuencia controlada.|  
|[operator\!\= \(multiset\)](../dotnet/operator-inequality-multiset-stl-clr.md)|Determina si un objeto de `multiset` no es igual a otro objeto de `multiset` .|  
|[operator\< \(multiset\)](../dotnet/operator-less-than-multiset-stl-clr.md)|Determina si un objeto de `multiset` es menor que otro objeto de `multiset` .|  
|[operator\<\= \(multiset\)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)|Determina si un objeto de `multiset` menor o igual que otro objeto de `multiset` .|  
|[operator\=\= \(multiset\)](../dotnet/operator-equality-multiset-stl-clr.md)|Determina si un objeto de `multiset` es igual a otro objeto de `multiset` .|  
|[operator\> \(multiset\)](../dotnet/operator-greater-than-multiset-stl-clr.md)|Determina si un objeto de `multiset` es mayor que otro objeto de `multiset` .|  
|[operator\>\= \(multiset\)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)|Determina si un objeto de `multiset` mayor o igual que otro objeto de `multiset` .|  
  
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
  
 El objeto pide la secuencia que controla llamando a un objeto almacenado de delegado de [multiset::key\_compare](../dotnet/multiset-key-compare-stl-clr.md)escrito.  Puede especificar el objeto almacenado de delegado cuando se construye el conjunto múltiple; si no especifica ningún objeto delegado, el valor predeterminado es la comparación `operator<(key_type, key_type)`.  Tiene acceso a este objeto almacenado llamando a la función [multiset::key\_comp](../dotnet/multiset-key-comp-stl-clr.md)`()`miembro.  
  
 Este tipo de objeto delegado debe imponer orden débil estricto sobre las teclas de [multiset::key\_type](../dotnet/multiset-key-type-stl-clr.md)escrito.  Es decir, para cualquier dos claves `X` y `Y`:  
  
 `key_comp()(X, Y)` devuelve el mismo resultado booleano en cada llamada.  
  
 Si `key_comp()(X, Y)` es true, el `key_comp()(Y, X)` debe ser false.  
  
 Si `key_comp()(X, Y)` es true, el `X` se secuenciado antes de `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` es true, el `X` y `Y` se dice que tienen orden equivalente.  
  
 Para cualquier elemento `X` que preceda `Y` en la secuencia controlada, `key_comp()(Y, X)` es false. \(Para el objeto predeterminado de delegado, las teclas nunca disminuyen en valor.\) A diferencia de la clase de plantilla [set](../dotnet/set-stl-clr.md), un objeto de clase de plantilla `multiset` no requiere que las claves para todos los elementos son únicas. \(Dos o más claves pueden tener orden equivalente\).  
  
 Cada elemento actúa como un ey y valor.  La secuencia se representan de forma que permita búsqueda, la inserción, y la eliminación de un elemento arbitrario con varias operaciones proporcionales al logaritmo del número de elementos de la secuencia \(tiempo logarítmico\).  Por otra parte, inserta un elemento no invalida ningún iterador, y quitar un elemento reemplaza solo los iteradores que señalan en el elemento quitado.  
  
 Un conjunto múltiple admite iteradores bidireccionales, que significa que se puede pasar a los elementos adyacentes dado un iterador que señale un elemento de la secuencia controlada.  Un nodo principal especial corresponde al iterador devuelto por [multiset::end](../dotnet/multiset-end-stl-clr.md)`()`.  Puede reducir este iterador para lograr el último elemento de la secuencia controlada, si existe.  Puede incrementar un iterador de conjunto múltiple para lograr el nodo principal, y a continuación comparará el igual a `end()`.  Pero no puede desreferenciar el iterador devuelto por `end()`.  
  
 Observe que no puede hacer referencia a un elemento de conjunto múltiple determinado directamente su posición numérica \-\- esto requiere un iterador de acceso aleatorio.  
  
 Un iterador de conjunto múltiple almacena un identificador al nodo asociado de conjunto múltiple, que a su vez almacena un identificador para el contenedor asociado.  Puede usar iteradores únicamente con los objetos contenedores asociados.  Un iterador de conjunto múltiple sigue siendo válido siempre y cuando el nodo asociado de conjunto múltiple está asociado a algún conjunto múltiple.  Por otra parte, un iterador válido es dereferencable \-\- puede utilizarlo para obtener acceso o modificar el valor del elemento que señala \-\- siempre y cuando no es igual a `end()`.  
  
 Borrar o quitar un elemento denomina destructor por el valor almacenado.  Destruyendo el contenedor borra todos los elementos.  Así, un contenedor cuyo tipo de elemento es una clase de referencia se asegura que ningún elemento sobrevivan al contenedor.  La nota, sin embargo, que un contenedor de identificadores hace `not` destruye sus elementos.  
  
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [Biblioteca STL\/CLR](../dotnet/stl-clr-library-reference.md)