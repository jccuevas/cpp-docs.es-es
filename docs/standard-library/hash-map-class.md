---
title: "hash_map (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdext::hash_map"
  - "hash_map/stdext::hash_map"
  - "std.hash_map"
  - "stdext.hash_map"
  - "std::hash_map"
  - "hash_map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_map (clase)"
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
caps.latest.revision: 25
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash_map (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Esta API está obsoleta.  La alternativa es la [unordered\_map \(Clase\)](../standard-library/unordered-map-class.md).  
  
 Almacena y recupera datos rápidamente de una colección en la que cada elemento es un par que tiene una clave de ordenación cuyo valor es único y un valor de datos asociado.  
  
## Sintaxis  
  
```  
template <  
   class Key,   
   class Type,   
   class Traits=hash_compare<Key, less<Key> >,   
   class Allocator=allocator<pair <const Key, Type> >   
>  
class hash_map  
```  
  
#### Parámetros  
 `Key`  
 Tipo de datos de clave que se almacenará en hash\_map.  
  
 `Type`  
 Tipo de datos de elemento que se almacenará en hash\_map.  
  
 `Traits`  
 Tipo que incluye dos objetos de función: uno de clase compare que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo y una función hash que es un predicado unario que asigna valores de clave de los elementos a enteros sin signo de tipo `size_t`.  Este argumento es opcional, y hash\_compare\<`Key`, less\<`Key`\> \> es el valor predeterminado.  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles acerca de la asignación y desasignación de memoria de hash\_map.  Este argumento es opcional y el valor predeterminado es allocator\<pair \<const `Key`, `Type`\>\>.  
  
## Comentarios  
 hash\_map es:  
  
-   Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.  
  
-   Reversible, porque proporciona un iterador bidireccional para tener acceso a sus elementos.  
  
-   Con algoritmo hash, ya que sus elementos se agrupan en depósitos en función del valor de una función hash aplicada a los valores de clave de los elementos.  
  
-   Único en el sentido de que cada uno de sus elementos debe tener una clave única.  
  
-   Un contenedor asociativo de pares, ya que los valores de datos de sus elementos son distintos de sus valores de clave.  
  
-   Una clase de plantilla, porque la funcionalidad que proporciona es genérica y por tanto independiente del tipo específico de datos contenido como elementos o claves.  Los tipos de datos que se usarán para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.  
  
 La ventaja principal de los algoritmos hash sobre la ordenación es su mayor eficacia; un algoritmo hash que se ejecuta correctamente realiza inserciones, eliminaciones y búsquedas en un tiempo promedio constante en comparación con un tiempo proporcional al logaritmo del número de elementos del contenedor en el caso de las técnicas de ordenación.  El valor de un elemento de hash\_map se puede cambiar directamente, pero no su valor de clave asociado.  En su lugar, se deben eliminar los valores de clave asociados a los antiguos elementos e insertar los nuevos valores de clave asociados a los elementos nuevos.  
  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación.  Los contenedores asociativos con algoritmo hash están optimizados para las operaciones de búsqueda, inserción y eliminación.  Las funciones miembro que admiten explícitamente estas operaciones son eficaces cuando se usan con una función hash bien diseñada, las realizan en un tiempo que es una constante promedio y no dependen del número de elementos del contenedor.  Una función hash bien diseñada genera una distribución uniforme de valores hash y minimiza el número de colisiones; se produce una colisión cuando se asignan valores de clave distintos al mismo valor hash.  En el peor de los casos, con la peor función hash posible, el número de operaciones es proporcional al número de elementos de la secuencia \(tiempo lineal\).  
  
 El hash\_map debe ser el contenedor asociativo preferido cuando la aplicación satisfaga las condiciones que asocian los valores a sus claves.  Un modelo de este tipo de estructura es una lista ordenada de palabras clave únicas con valores de cadena asociados que proporcionan, por ejemplo, definiciones.  Si por el contrario las palabras tienen más una definición correcta, de modo que las claves no son únicas, el contenedor más adecuado sería hash\_multimap.  Por otra parte, si solo se va a almacenar la lista de palabras, el contenedor correcto sería hash\_set.  Si se permiten varias repeticiones de las palabras, la estructura de contenedor adecuada sería hash\_multiset.  
  
 El hash\_map ordena la secuencia que controla llamando a un objeto `Traits` hash almacenado de clase [value\_compare](../standard-library/value-compare-class.md).  Se puede obtener acceso a este objeto almacenado llamando a la función miembro [key\_comp](../Topic/hash_map::key_comp.md).  Este tipo de objeto de función debe comportarse igual que un objeto de clase [hash\_compare](../standard-library/hash-compare-class.md)\<Key, less\<Key\>\>.  En concreto, para todos los valores `Key` de tipo `Key`, la llamada a `Traits`\(`Key` \) produce una distribución de valores de tipo `size_t`.  
  
 En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes \(en el sentido de que ninguno es menor que el otro\) o que uno es menor que el otro.  Esto produce una ordenación entre los elementos no equivalentes.  En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar.  Un predicado binario f\(x y\) es un objeto de función que tiene dos objetos de argumento `x` e `y`, y un valor devuelto de `true` o `false`.  Una ordenación impuesta en un hash\_map es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos x e y se definen como equivalentes cuando tanto f\(x, y\) como f\(y, x\) son false.  Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total \(en el sentido de que todos los elementos se ordenan entre sí\) y las claves coincidentes serán indiscernibles unas de otras.  
  
 El orden real de los elementos de la secuencia controlada depende de la función hash, la función de ordenación y el tamaño actual de la tabla hash almacenada en el objeto contenedor.  No se puede determinar el tamaño actual de la tabla hash, por lo que en general no se puede predecir el orden de los elementos de la secuencia controlada.  La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 El iterador proporcionado por la clase hash\_map es un iterador bidireccional, pero las funciones miembro de clase [insert](../Topic/hash_map::insert.md) y [hash\_map](../Topic/hash_map::hash_map.md) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales.  Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad.  Cada concepto de iterador tiene su propio conjunto de requisitos, y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador.  Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia.  Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores `[First, Last)` en el contexto de las funciones miembro de clase.  
  
 En Visual C\+\+ .NET 2003, los miembros de los archivos de encabezado [\<hash\_map\>](../standard-library/hash-map.md) y [\<hash\_set\>](../standard-library/hash-set.md) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext.  Vea [El espacio de nombres stdext](../standard-library/stdext-namespace.md) para obtener más información.  
  
### Constructores  
  
|||  
|-|-|  
|[hash\_map](../Topic/hash_map::hash_map.md)|Construye un `hash_map` que está vacío o que es una copia de todo o de parte de otro `hash_map`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/hash_map::allocator_type.md)|Tipo que representa la clase `allocator` para el objeto `hash_map`.|  
|[const\_iterator](../Topic/hash_map::const_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en `hash_map`.|  
|[const\_pointer](../Topic/hash_map::const_pointer.md)|Tipo que proporciona un puntero a un elemento `const` en un `hash_map`.|  
|[const\_reference](../Topic/hash_map::const_reference.md)|Tipo que proporciona una referencia a un elemento `const` almacenado en un `hash_map` para leer y realizar operaciones `const`.|  
|[const\_reverse\_iterator](../Topic/hash_map::const_reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` en `hash_map`.|  
|[difference\_type](../Topic/hash_map::difference_type.md)|Tipo entero con signo que se puede usar para representar el número de elementos de un `hash_map` en un intervalo entre elementos a los que apuntan los iteradores.|  
|[iterator](../Topic/hash_map::iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de `hash_map`.|  
|[key\_compare](../Topic/hash_map::key_compare.md)|Tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `hash_map`.|  
|[key\_type](../Topic/hash_map::key_type.md)|Tipo que describe el objeto de clave de ordenación que constituye cada elemento de `hash_map`.|  
|[mapped\_type](../Topic/hash_map::mapped_type.md)|Tipo que representa el tipo de datos almacenados en un `hash_map`.|  
|[puntero](../Topic/hash_map::pointer.md)|Tipo que proporciona un puntero a un elemento de `hash_map`.|  
|[referencia](../Topic/hash_map::reference.md)|Tipo que proporciona una referencia a un elemento almacenado en un `hash_map`.|  
|[reverse\_iterator](../Topic/hash_map::reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de `hash_map` invertido.|  
|[size\_type](../Topic/hash_map::size_type.md)|Tipo entero sin signo que puede representar el número de elementos de un `hash_map`.|  
|[value\_type](../Topic/hash_map::value_type.md)|Tipo que proporciona un objeto de función que puede comparar dos elementos como claves de ordenación para determinar su orden relativo en el `hash_map`.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[hash\_map::at](../Topic/hash_map::at.md)|Busca un elemento en un `hash_map` con un valor de clave especificado.|  
|[begin](../Topic/hash_map::begin.md)|Devuelve un iterador que direcciona el primer elemento del `hash_map`.|  
|[hash\_map::cbegin](../Topic/hash_map::cbegin.md)|Devuelve un iterador constante que direcciona el primer elemento del `hash_map`.|  
|[hash\_map::cend](../Topic/hash_map::cend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_map`.|  
|[desactivada](../Topic/hash_map::clear.md)|Borra todos los elementos de un `hash_map`.|  
|[count](../Topic/hash_map::count.md)|Devuelve el número de elementos de un `hash_map` cuya clave coincide con una clave especificada por un parámetro.|  
|[hash\_map::crbegin](../Topic/hash_map::crbegin.md)|Devuelve un iterador constante que direcciona el primer elemento de `hash_map` invertido.|  
|[hash\_map::crend](../Topic/hash_map::crend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_map` invertido.|  
|[hash\_map::emplace](../Topic/hash_map::emplace.md)|Inserta en un `hash_map` un elemento construido en contexto.|  
|[hash\_map::emplace\_hint](../Topic/hash_map::emplace_hint.md)|Inserta en un `hash_map` un elemento construido en contexto, con una sugerencia de colocación.|  
|[vacío](../Topic/hash_map::empty.md)|Comprueba si un `hash_map` está vacío.|  
|[end](../Topic/hash_map::end.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_map`.|  
|[equal\_range](../Topic/hash_map::equal_range.md)|Devuelve un par de iteradores, respectivamente, al primer elemento de `hash_map` cuya clave mayor es que una clave especificada y al primer elemento del `hash_map` cuya clave es igual o mayor que la clave especificada.|  
|[erase](../Topic/hash_map::erase.md)|Quita un elemento o un intervalo de elementos de un `hash_map` de las posiciones especificadas.|  
|[find](../Topic/hash_map::find.md)|Devuelve un iterador que direcciona la ubicación de un elemento en un `hash_map` que tiene una clave equivalente a una clave especificada.|  
|[get\_allocator](../Topic/hash_map::get_allocator.md)|Devuelve una copia del objeto `allocator` utilizado para construir el `hash_map`.|  
|[insertar](../Topic/hash_map::insert.md)|Inserta un elemento o un intervalo de elementos en un `hash_map`.|  
|[key\_comp](../Topic/hash_map::key_comp.md)|Devuelve un iterador al primer elemento de `hash_map` cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[lower\_bound](../Topic/hash_map::lower_bound.md)|Devuelve un iterador al primer elemento de `hash_map` cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[max\_size](../Topic/hash_map::max_size.md)|Devuelve la longitud máxima del `hash_map`.|  
|[rbegin](../Topic/hash_map::rbegin.md)|Devuelve un iterador que direcciona el primer elemento de `hash_map` invertido.|  
|[rend](../Topic/hash_map::rend.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_map` invertido.|  
|[size](../Topic/hash_map::size.md)|Devuelve el número de elementos de `hash_map`.|  
|[swap](../Topic/hash_map::swap.md)|Intercambia los elementos de dos `hash_map`.|  
|[upper\_bound](../Topic/hash_map::upper_bound.md)|Devuelve un iterador al primer elemento de `hash_map` cuyo valor de clave es mayor que el de una clave especificada.|  
|[value\_comp](../Topic/hash_map::value_comp.md)|Recupera una copia del objeto de comparación utilizado para ordenar valores de elemento de `hash_map`.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator&#91;&#93;](../Topic/hash_map::operator.md)|Inserta un elemento en un `hash_map` con un valor de clave especificado.|  
|[hash\_map::operator\=](../Topic/hash_map::operator=.md)|Reemplaza los elementos de un `hash_map` con una copia de otro `hash_map`.|  
  
## Requisitos  
 **Encabezado:** \<hash\_map\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)