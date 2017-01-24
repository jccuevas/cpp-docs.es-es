---
title: "hash_set (Clase) | Microsoft Docs"
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
  - "hash_set/stdext::hash_set"
  - "std::hash_set"
  - "std.hash_set"
  - "stdext::hash_set"
  - "hash_set"
  - "stdext.hash_set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_set (clase)"
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
caps.latest.revision: 22
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash_set (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  Esta API está obsoleta.  La alternativa es la [unordered\_set \(Clase\)](../standard-library/unordered-set-class.md).  
  
 La clase de contenedor hash\_set es una extensión de la biblioteca de plantillas estándar \(STL\) y se usa para el almacenamiento y la recuperación rápida de datos de una colección en la que los valores de los elementos contenidos son únicos y actúan como valores clave.  
  
## Sintaxis  
  
```  
template <  
   class Key,   
   class Traits=hash_compare<Key, less<Key> >,   
   class Allocator=allocator<Key>   
>  
class hash_set  
```  
  
#### Parámetros  
 `Key`  
 Tipo de datos de elemento que se almacenará en hash\_set.  
  
 `Traits`  
 Tipo que incluye dos objetos de función: uno de clase compare que es un predicado binario capaz de comparar dos valores de elemento como claves de ordenación para determinar su orden relativo y una función hash que es un predicado unario que asigna valores de clave de los elementos a enteros sin signo de tipo **size\_t**.  Este argumento es opcional y `hash_compare`*\<Key,* **less***\<Key\> \>* es el valor predeterminado.  
  
 `Allocator`  
 Tipo que representa el objeto de asignador almacenado que encapsula los detalles sobre la asignación y desasignación de memoria de hash\_set.  Este argumento es opcional y el valor predeterminado es **allocator***\<Key\>.*  
  
## Comentarios  
 El hash\_set es:  
  
-   Un contenedor asociativo de tamaño variable que admite la recuperación eficaz de valores de elemento según un valor de clave asociado.  Es más, es un contenedor asociativo simple porque los valores de elemento son sus valores de clave.  
  
-   Reversible, porque proporciona un iterador bidireccional para tener acceso a sus elementos.  
  
-   Con algoritmo hash, ya que sus elementos se agrupan en depósitos en función del valor de una función hash aplicada a los valores de clave de los elementos.  
  
-   Único en el sentido de que cada uno de sus elementos debe tener una clave única.  Puesto que hash\_set también es un contenedor asociativo simple, sus elementos también son únicos.  
  
-   Una clase de plantilla, porque la funcionalidad que proporciona es genérica y, por tanto, independiente del tipo específico de datos contenido como elementos o claves.  Los tipos de datos que se usarán para los elementos y las claves se especifican como parámetros en la plantilla de clase junto con la función de comparación y el asignador.  
  
 La ventaja principal de los algoritmos hash sobre la ordenación es su mayor eficacia; un algoritmo hash que se ejecuta correctamente realiza inserciones, eliminaciones y búsquedas en un tiempo promedio constante en comparación con un tiempo proporcional al logaritmo del número de elementos del contenedor en el caso de las técnicas de ordenación.  El valor de un elemento de un conjunto no se puede cambiar directamente.  Lo que se debe hacer es eliminar los valores antiguos e insertar elementos con nuevos valores.  
  
 En general, la elección del tipo de contenedor se debe tomar según el tipo de búsqueda y de inserción que necesite la aplicación.  Los contenedores asociativos con algoritmo hash están optimizados para las operaciones de búsqueda, inserción y eliminación.  Las funciones miembro que admiten explícitamente estas operaciones son eficaces cuando se usan con una función hash bien diseñada, las realizan en un tiempo que es una constante promedio y no dependen del número de elementos del contenedor.  Una función hash bien diseñada genera una distribución uniforme de valores hash y minimiza el número de colisiones; se produce una colisión cuando se asignan valores de clave distintos al mismo valor hash.  En el peor de los casos, con la peor función hash posible, el número de operaciones es proporcional al número de elementos de la secuencia \(tiempo lineal\).  
  
 El hash\_set debe ser el contenedor asociativo preferido cuando la aplicación cumpla las condiciones que asocian los valores a sus claves.  Los elementos de un hash\_set son únicos y actúan como sus propios criterios de ordenación.  Un modelo para este tipo de estructura es una lista ordenada, por ejemplo, de palabras en las que las palabras pueden aparecer solo una vez.  Si se permiten varias repeticiones de las palabras, la estructura de contenedor adecuada sería hash\_multiset.  Si los valores necesitan estar asociados a una lista de palabras clave únicas, un hash\_map sería una estructura adecuada para contener estos datos.  Si, por el contrario, las claves no son únicas, un hash\_multimap sería el contenedor preferido.  
  
 El hash\_set ordena la secuencia que controla llamando a un objeto **Traits** hash almacenado de tipo [value\_compare](../Topic/hash_set::value_compare.md).  Se puede obtener acceso a este objeto almacenado llamando a la función miembro [key\_comp](../Topic/hash_set::key_comp.md).  Este tipo de objeto de función debe comportarse igual que un objeto de clase *hash\_compare\<Key, less\<Key\> \>.* En concreto, para todos los valores `_Key` de tipo Key, la llamada Trait\(`_Key`\) produce una distribución de valores de tipo size\_t.  
  
 En general, se debe poder comparar si los elementos son menores que otros para poder establecer este orden; de este modo, dados dos elementos cualesquiera, se puede determinar que son equivalentes \(en el sentido de que ninguno es menor que el otro\) o que uno es menor que el otro.  Esto produce una ordenación entre los elementos no equivalentes.  En un sentido más técnico, la función de comparación es un predicado binario que induce una ordenación débil estricta en el sentido matemático estándar.  Un predicado binario *f*\(*x*,*y*\) es un objeto de función que tiene dos objetos de argumento x e y, y un valor devuelto de true o false.  Una ordenación impuesta en un hash\_set es una ordenación débil estricta si el predicado binario es irreflexivo, antisimétrico y transitivo, y si la equivalencia es transitiva, donde dos objetos *x* e *y* se definen como equivalentes cuando *f*\(*x*,*y*\) y *f*\(*y*,*x*\) son false.  Si la condición más fuerte de igualdad entre las claves reemplaza la de equivalencia, la ordenación se convierte en total \(en el sentido de que todos los elementos se ordenan entre sí\) y las claves coincidentes serán indiscernibles unas de otras.  
  
 El orden real de los elementos de la secuencia controlada depende de la función hash, la función de ordenación y el tamaño actual de la tabla hash almacenada en el objeto contenedor.  No se puede determinar el tamaño actual de la tabla hash, por lo que en general no se puede predecir el orden de los elementos de la secuencia controlada.  La inserción de elementos no invalida ningún iterador y al quitar elementos solo se invalidan los iteradores que habían apuntado específicamente a los elementos quitados.  
  
 El iterador proporcionado por la clase hash\_set es un iterador bidireccional, pero las funciones miembro de clase [insert](../Topic/hash_set::insert.md) y [hash\_set](../Topic/hash_set::hash_set.md) tienen versiones que toman como parámetros de plantilla un iterador de entrada más débil, cuyos requisitos de funcionalidad son más mínimos que los garantizados por la clase de iteradores bidireccionales.  Los distintos conceptos de iterador forman una familia relacionada por los refinamientos de su funcionalidad.  Cada concepto de iterador tiene su propio conjunto de requisitos, y los algoritmos que funcionan con ellos deben limitar sus suposiciones a los requisitos proporcionados por ese tipo de iterador.  Se puede suponer que se puede desreferenciar un iterador de entrada para hacer referencia a un objeto y que se puede incrementar hasta el iterador siguiente de la secuencia.  Se trata de un conjunto mínimo de funcionalidad, pero es suficiente para poder comunicarse sobre un intervalo de iteradores \(`_First`, `_Last`\) en el contexto de las funciones miembro de clase.  
  
 En Visual C\+\+ .NET 2003, los miembros de los archivos de encabezado [\<hash\_map\>](../standard-library/hash-map.md) y [\<hash\_set\>](../standard-library/hash-set.md) ya no están en el espacio de nombres std, sino que se han movido al espacio de nombres stdext.  Vea [El espacio de nombres stdext](../standard-library/stdext-namespace.md) para obtener más información.  
  
### Constructores  
  
|||  
|-|-|  
|[hash\_set](../Topic/hash_set::hash_set.md)|Construye un `hash_set` que está vacío o que es una copia de todo o de parte de otro `hash_set`.|  
  
### Definiciones de tipo  
  
|||  
|-|-|  
|[allocator\_type](../Topic/hash_set::allocator_type.md)|Tipo que representa la clase `allocator` para el objeto `hash_set`.|  
|[const\_iterator](../Topic/hash_set::const_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer un elemento `const` en `hash_set`.|  
|[const\_pointer](../Topic/hash_set::const_pointer.md)|Tipo que proporciona un puntero a un elemento `const` en un `hash_set`.|  
|[const\_reference](../Topic/hash_set::const_reference.md)|Tipo que proporciona una referencia a un elemento `const` almacenado en un `hash_set` para leer y realizar operaciones `const`.|  
|[const\_reverse\_iterator](../Topic/hash_set::const_reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer cualquier elemento `const` en `hash_set`.|  
|[difference\_type](../Topic/hash_set::difference_type.md)|Tipo entero con signo que se puede usar para representar el número de elementos de un `hash_set` en un intervalo entre elementos a los que apuntan los iteradores.|  
|[iterator](../Topic/hash_set::iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar cualquier elemento de `hash_set`.|  
|[key\_compare](../Topic/hash_set::key_compare.md)|Tipo que proporciona un objeto de función que puede comparar dos claves de ordenación para determinar el orden relativo de dos elementos en el `hash_set`.|  
|[key\_type](../Topic/hash_set::key_type.md)|Tipo que describe un objeto almacenado como un elemento de un `hash_set` en su capacidad como criterio de ordenación.|  
|[puntero](../Topic/hash_set::pointer.md)|Tipo que proporciona un puntero a un elemento de `hash_set`.|  
|[referencia](../Topic/hash_set::reference.md)|Tipo que proporciona una referencia a un elemento almacenado en un `hash_set`.|  
|[reverse\_iterator](../Topic/hash_set::reverse_iterator.md)|Tipo que proporciona un iterador bidireccional que puede leer o modificar un elemento de `hash_set` invertido.|  
|[size\_type](../Topic/hash_set::size_type.md)|Tipo entero sin signo que puede representar el número de elementos de un `hash_set`.|  
|[value\_compare](../Topic/hash_set::value_compare.md)|Tipo que proporciona dos objetos de función, un predicado binario de la clase compare que puede comparar dos valores de elementos de un `hash_set` para determinar su orden relativo y un predicado unario que aplica un algoritmo hash a los elementos.|  
|[value\_type](../Topic/hash_set::value_type.md)|Tipo que describe un objeto almacenado como un elemento de un `hash_set` en su capacidad como valor.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[begin](../Topic/hash_set::begin.md)|Devuelve un iterador que direcciona el primer elemento del `hash_set`.|  
|[hash\_set::cbegin](../Topic/hash_set::cbegin.md)|Devuelve un iterador constante que direcciona el primer elemento del `hash_set`.|  
|[hash\_set::cend](../Topic/hash_set::cend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_set`.|  
|[desactivada](../Topic/hash_set::clear.md)|Borra todos los elementos de un `hash_set`.|  
|[count](../Topic/hash_set::count.md)|Devuelve el número de elementos de un `hash_set` cuya clave coincide con una clave especificada por un parámetro.|  
|[hash\_set::crbegin](../Topic/hash_set::crbegin.md)|Devuelve un iterador constante que direcciona el primer elemento de `hash_set` invertido.|  
|[hash\_set::crend](../Topic/hash_set::crend.md)|Devuelve un iterador constante que direcciona la ubicación que sigue al último elemento de `hash_set` invertido.|  
|[hash\_set::emplace](../Topic/hash_set::emplace.md)|Inserta en un `hash_set` un elemento construido en contexto.|  
|[hash\_set::emplace\_hint](../Topic/hash_set::emplace_hint.md)|Inserta en un `hash_set` un elemento construido en contexto, con una sugerencia de colocación.|  
|[vacío](../Topic/hash_set::empty.md)|Comprueba si un `hash_set` está vacío.|  
|[end](../Topic/hash_set::end.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_set`.|  
|[equal\_range](../Topic/hash_set::equal_range.md)|Devuelve un par de iteradores, respectivamente, al primer elemento de `hash_set` con una clave que es mayor que una clave especificada, y al primer elemento del `hash_set` con una clave que es igual o mayor que la clave especificada.|  
|[erase](../Topic/hash_set::erase.md)|Quita un elemento o un intervalo de elementos de una clase `hash_set` de las posiciones especificadas o quita los elementos que coinciden con una clave especificada.|  
|[find](../Topic/hash_set::find.md)|Devuelve un iterador que direcciona la ubicación de un elemento en un `hash_set` que tiene una clave equivalente a una clave especificada.|  
|[get\_allocator](../Topic/hash_set::get_allocator.md)|Devuelve una copia del objeto `allocator` utilizado para construir el `hash_set`.|  
|[insertar](../Topic/hash_set::insert.md)|Inserta un elemento o un intervalo de elementos en un `hash_set`.|  
|[key\_comp](../Topic/hash_set::key_comp.md)|Recupera una copia del objeto de comparación utilizado para ordenar claves de un `hash_set`.|  
|[lower\_bound](../Topic/hash_set::lower_bound.md)|Devuelve un iterador al primer elemento de un `hash_set` cuya clave es igual o mayor que una clave especificada.|  
|[max\_size](../Topic/hash_set::max_size.md)|Devuelve la longitud máxima del `hash_set`.|  
|[rbegin](../Topic/hash_set::rbegin.md)|Devuelve un iterador que direcciona el primer elemento de `hash_set` invertido.|  
|[rend](../Topic/hash_set::rend.md)|Devuelve un iterador que direcciona la ubicación que sigue al último elemento de `hash_set` invertido.|  
|[size](../Topic/hash_set::size.md)|Devuelve el número de elementos de `hash_set`.|  
|[swap](../Topic/hash_set::swap.md)|Intercambia los elementos de dos `hash_set`.|  
|[upper\_bound](../Topic/hash_set::upper_bound.md)|Devuelve un iterador al primer elemento de `hash_set` cuyo valor de clave es igual o mayor que el de una clave especificada.|  
|[value\_comp](../Topic/hash_set::value_comp.md)|Recupera una copia del objeto traits hash usado para aplicar un algoritmo hash y ordenar valores de claves de elementos en un `hash_set`.|  
  
### Operadores  
  
|||  
|-|-|  
|[hash\_set::operator\=](../Topic/hash_set::operator=.md)|Reemplaza los elementos de un `hash_set` con una copia de otro `hash_set`.|  
  
## Requisitos  
 **Encabezado:** \<hash\_set\>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)