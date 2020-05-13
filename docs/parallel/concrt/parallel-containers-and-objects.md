---
title: Contenedores y objetos paralelos
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: f3fb2bb57c8bcf65de0a7f74f2992050d8257429
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363043"
---
# <a name="parallel-containers-and-objects"></a>Contenedores y objetos paralelos

La biblioteca de patrones paralelos (PPL) incluye varios contenedores y objetos que proporcionan acceso seguro para subprocesos a sus elementos.

Un *contenedor simultáneo* proporciona acceso seguro para simultaneidad a las operaciones más importantes. Aquí, la seguridad para simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de inicialización de elementos, o de un orden de recorrido determinado. La funcionalidad de estos contenedores se asemeja a las proporcionadas por la biblioteca estándar C++. Por ejemplo, la clase [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) es similar a la clase `concurrent_vector` [std::vector,](../../standard-library/vector-class.md) excepto que la clase permite anexar elementos en paralelo. Use contenedores simultáneos cuando tenga código paralelo que requiera acceso de lectura y escritura al mismo contenedor.

Un *objeto simultáneo* se comparte simultáneamente entre los componentes. Un proceso que calcula el estado de un objeto simultáneo en paralelo produce el mismo resultado que otro proceso que calcula el mismo estado en serie. La clase [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) es un ejemplo de un tipo de objeto simultáneo. La `combinable` clase le permite realizar cálculos en paralelo y, a continuación, combinar esos cálculos en un resultado final. Utilice objetos simultáneos cuando, de lo contrario, utilice un mecanismo de sincronización, por ejemplo, una exclusión mutua, para sincronizar el acceso a una variable o recurso compartido.

## <a name="sections"></a><a name="top"></a>Secciones

En este tema se describen los siguientes objetos y contenedores paralelos en detalle.

Contenedores simultáneos:

- [Clase concurrent_vector](#vector)

  - [Diferencias entre concurrent_vector y vector](#vector-differences)

  - [Operaciones seguras para simultaneidad](#vector-safety)

  - [Seguridad de excepciones](#vector-exceptions)

- [Clase concurrent_queue](#queue)

  - [Diferencias entre concurrent_queue y cola](#queue-differences)

  - [Operaciones seguras para simultaneidad](#queue-safety)

  - [Soporte de iterador](#queue-iterators)

- [Clase concurrent_unordered_map](#unordered_map)

  - [Diferencias entre concurrent_unordered_map y unordered_map](#map-differences)

  - [Operaciones seguras para simultaneidad](#map-safety)

- [Clase concurrent_unordered_multimap](#unordered_multimap)

- [Clase concurrent_unordered_set](#unordered_set)

- [Clase concurrent_unordered_multiset](#unordered_multiset)

Objetos simultáneos:

- [clase combinable](#combinable)

  - [Métodos y características](#combinable-features)

  - [Ejemplos](#combinable-examples)

## <a name="concurrent_vector-class"></a><a name="vector"></a>Clase concurrent_vector

La [clase concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) es una clase contenedora de secuencia que, al igual que la clase [std::vector,](../../standard-library/vector-class.md) permite tener acceso aleatorio a sus elementos. La `concurrent_vector` clase habilita las operaciones de acceso de elementos y anexar seguras para simultaneidad. Las operaciones de anexar no invalidan los punteros o iteradores existentes. Las operaciones de acceso de iterador y recorrido también son seguras para simultaneidad. Aquí, la seguridad para simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de inicialización de elementos, o de un orden de recorrido determinado.

### <a name="differences-between-concurrent_vector-and-vector"></a><a name="vector-differences"></a>Diferencias entre concurrent_vector y vector

La `concurrent_vector` clase se parece `vector` mucho a la clase. La complejidad de anexar, acceso a elementos y operaciones de acceso de iterador en un `concurrent_vector` objeto son las mismas que para un `vector` objeto. Los siguientes puntos ilustran dónde `concurrent_vector` difiere de: `vector`

- Anexar, acceso a elementos, acceso de `concurrent_vector` iterador y operaciones de recorrido de iterador en un objeto son seguras para simultaneidad.

- Puede agregar elementos solo al `concurrent_vector` final de un objeto. La `concurrent_vector` clase no `insert` proporciona el método.

- Un `concurrent_vector` objeto no utiliza [la semántica](../../cpp/rvalue-reference-declarator-amp-amp.md) de movimiento cuando se anexa a él.

- La `concurrent_vector` clase no `erase` proporciona `pop_back` los métodos or. Al `vector`igual que con , utilice el `concurrent_vector` método [clear](reference/concurrent-vector-class.md#clear) para quitar todos los elementos de un objeto.

- La `concurrent_vector` clase no almacena sus elementos de forma contigua en la memoria. Por lo tanto, `concurrent_vector` no puede utilizar la clase de todas las maneras en que puede utilizar una matriz. Por ejemplo, para `v` una `concurrent_vector`variable denominada `&v[0]+2` type , la expresión produce un comportamiento indefinido.

- La `concurrent_vector` clase define los métodos [grow_by](reference/concurrent-vector-class.md#grow_by) y [grow_to_at_least.](reference/concurrent-vector-class.md#grow_to_at_least) Estos métodos son similares al método [de cambio](reference/concurrent-vector-class.md#resize) de tamaño, excepto que son seguros para simultaneidad.

- Un `concurrent_vector` objeto no reubica sus elementos cuando se anexa a él o cambiar su tamaño. Esto permite que los punteros e iteradores existentes sigan siendo válidos durante las operaciones simultáneas.

- El tiempo de ejecución no `concurrent_vector` define `bool`una versión especializada de para el tipo .

### <a name="concurrency-safe-operations"></a><a name="vector-safety"></a>Operaciones seguras para simultaneidad

Todos los métodos que anexan `concurrent_vector` o aumentan el tamaño `concurrent_vector` de un objeto, o tienen acceso a un elemento de un objeto, son seguros para simultaneidad. Aquí, la seguridad para simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de inicialización de elementos, o de un orden de recorrido determinado. La excepción a `resize` esta regla es el método.

En la tabla `concurrent_vector` siguiente se muestran los métodos y operadores comunes que son seguros para simultaneidad.

||||
|-|-|-|
|[En](reference/concurrent-vector-class.md#at)|[Final](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[Comenzar](reference/concurrent-vector-class.md#begin)|[Frente](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[Atrás](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[Capacidad](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[Vacío](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[Tamaño](reference/concurrent-vector-class.md#size)|

Las operaciones que el tiempo de ejecución proporciona para `reserve`la compatibilidad con la biblioteca estándar de C+++ , por ejemplo, , no son seguras para simultaneidad. En la tabla siguiente se muestran los métodos y operadores comunes que no son seguros para simultaneidad.

|||
|-|-|
|[Asignar](reference/concurrent-vector-class.md#assign)|[Reserva](reference/concurrent-vector-class.md#reserve)|
|[Claro](reference/concurrent-vector-class.md#clear)|[resize](reference/concurrent-vector-class.md#resize)|
|[operador](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Las operaciones que modifican el valor de los elementos existentes no son seguras para simultaneidad. Utilice un objeto de sincronización como un objeto [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) para sincronizar operaciones simultáneas de lectura y escritura con el mismo elemento de datos. Para obtener más información acerca de los objetos de sincronización, vea Estructuras de datos de [sincronización](../../parallel/concrt/synchronization-data-structures.md).

Al convertir código existente `vector` que `concurrent_vector`usa , las operaciones simultáneas pueden hacer que cambie el comportamiento de la aplicación. Por ejemplo, considere el siguiente programa que realiza `concurrent_vector` simultáneamente dos tareas en un objeto. La primera tarea anexa elementos adicionales a un `concurrent_vector` objeto. La segunda tarea calcula la suma de todos los elementos del mismo objeto.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Aunque `end` el método es seguro para simultaneidad, una llamada simultánea al `end` método [push_back](reference/concurrent-vector-class.md#push_back) hace que cambie el valor devuelto por. El número de elementos que recorre el iterador es indeterminado. Por lo tanto, este programa puede producir un resultado diferente cada vez que se ejecuta. Cuando el tipo de elemento no es trivial, es posible `push_back` `end` que exista una condición de carrera entre y las llamadas. El `end` método puede devolver un elemento que está asignado, pero no se inicializa completamente.

### <a name="exception-safety"></a><a name="vector-exceptions"></a>Seguridad de excepciones

Si una operación de crecimiento o asignación `concurrent_vector` produce una excepción, el estado del objeto deja de ser válido. El comportamiento `concurrent_vector` de un objeto que se encuentra en un estado no válido es indefinido a menos que se indique lo contrario. Sin embargo, el destructor siempre libera la memoria que el objeto asigna, incluso si el objeto está en un estado no válido.

El tipo de datos `T`de los elementos vectoriales, , debe cumplir los siguientes requisitos. De lo contrario, `concurrent_vector` el comportamiento de la clase es indefinido.

- El destructor no debe lanzar.

- Si se produce el constructor predeterminado o de copia, `virtual` el destructor no debe declararse mediante la palabra clave y debe funcionar correctamente con memoria inicializada en cero.

[[Superior](#top)]

## <a name="concurrent_queue-class"></a><a name="queue"></a>Clase concurrent_queue

La [clase concurrency::concurrent_queue,](../../parallel/concrt/reference/concurrent-queue-class.md) al igual que la clase [std::queue,](../../standard-library/queue-class.md) permite tener acceso a sus elementos front y back. La `concurrent_queue` clase habilita las operaciones de cola y dequeue seguras para simultaneidad. Aquí, la seguridad para simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de inicialización de elementos, o de un orden de recorrido determinado. La `concurrent_queue` clase también proporciona compatibilidad con iterantes que no es seguro para simultaneidad.

### <a name="differences-between-concurrent_queue-and-queue"></a><a name="queue-differences"></a>Diferencias entre concurrent_queue y cola

La `concurrent_queue` clase se parece `queue` mucho a la clase. Los siguientes puntos ilustran dónde `concurrent_queue` difiere de: `queue`

- Las operaciones de cola `concurrent_queue` y decola ción en un objeto son seguras para simultaneidad.

- La `concurrent_queue` clase proporciona compatibilidad con iterador que no es seguro para simultaneidad.

- La `concurrent_queue` clase no `front` proporciona `pop` los métodos or. La `concurrent_queue` clase reemplaza estos métodos definiendo el [método try_pop.](reference/concurrent-queue-class.md#try_pop)

- La `concurrent_queue` clase no `back` proporciona el método. Por lo tanto, no puede hacer referencia al final de la cola.

- La `concurrent_queue` clase proporciona el método `size` [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) en lugar del método. El `unsafe_size` método no es seguro para simultaneidad.

### <a name="concurrency-safe-operations"></a><a name="queue-safety"></a>Operaciones seguras para simultaneidad

Todos los métodos que se `concurrent_queue` ponen en cola o quitan la cola de un objeto son seguros para simultaneidad. Aquí, la seguridad para simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de inicialización de elementos, o de un orden de recorrido determinado.

En la tabla `concurrent_queue` siguiente se muestran los métodos y operadores comunes que son seguros para simultaneidad.

|||
|-|-|
|[Vacío](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Aunque `empty` el método es seguro para simultaneidad, una operación simultánea `empty` puede hacer que la cola crezca o se reduzca antes de que se devuelva el método.

En la tabla siguiente se muestran los métodos y operadores comunes que no son seguros para simultaneidad.

|||
|-|-|
|[Claro](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="iterator-support"></a><a name="queue-iterators"></a>Soporte de iterador

Proporciona `concurrent_queue` iteradores que no son seguros para simultaneidad. Se recomienda usar estos iteradores solo para la depuración.

Un `concurrent_queue` iterador solo atraviesa los elementos en la dirección de avance. En la tabla siguiente se muestran los operadores que admite cada iterador.

|Operator|Descripción|
|--------------|-----------------|
|`operator++`|Avanza al siguiente elemento de la cola. Este operador está sobrecargado para proporcionar semántica previa y posterior al incremento.|
|`operator*`|Recupera una referencia al elemento actual.|
|`operator->`|Recupera un puntero al elemento actual.|

[[Superior](#top)]

## <a name="concurrent_unordered_map-class"></a><a name="unordered_map"></a>Clase concurrent_unordered_map

La clase [concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) es una clase contenedora asociativa que, al igual que la clase [std::unordered_map,](../../standard-library/unordered-map-class.md) controla una secuencia de longitud variable de elementos de tipo [std::pair\<const Key, Ty>](../../standard-library/pair-structure.md). Piense en un mapa desordenado como un diccionario al que puede agregar un par de clave y valor o buscar un valor por clave. Esta clase es útil cuando tiene varios subprocesos o tareas que tienen que tener acceso simultáneamente a un contenedor compartido, insertar en él o actualizarlo.

En el ejemplo siguiente se `concurrent_unordered_map`muestra la estructura básica para utilizar . En este ejemplo se insertan teclas de caracteres en el intervalo ['a', 'i']. Dado que el orden de las operaciones es indeterminado, el valor final de cada clave también es indeterminado. Sin embargo, es seguro realizar las inserciones en paralelo.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Para obtener un `concurrent_unordered_map` ejemplo que se utiliza para realizar una operación de asignación y reducir en paralelo, vea [Cómo: realizar operaciones](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)de asignación y reducir en paralelo .

### <a name="differences-between-concurrent_unordered_map-and-unordered_map"></a><a name="map-differences"></a>Diferencias entre concurrent_unordered_map y unordered_map

La `concurrent_unordered_map` clase se parece `unordered_map` mucho a la clase. Los siguientes puntos ilustran dónde `concurrent_unordered_map` difiere de: `unordered_map`

- Los `erase` `bucket`métodos , `bucket_count`, , `unsafe_bucket_count`y `unsafe_bucket_size` `bucket_size` , se denominan `unsafe_erase`, `unsafe_bucket`, , y , respectivamente. La `unsafe_` convención de nomenclatura indica que estos métodos no son seguros para simultaneidad. Para obtener más información acerca de la seguridad de simultaneidad, vea [Operaciones seguras para simultaneidad](#map-safety).

- Las operaciones de inserción no invalidan los punteros o iteradores existentes ni cambian el orden de los elementos que ya existen en el mapa. Las operaciones de inserción y poligonal pueden producirse simultáneamente.

- `concurrent_unordered_map`solo admite iteración hacia delante.

- La inserción no invalida ni actualiza `equal_range`los iteradores devueltos por . La inserción puede anexar elementos desiguales al final del intervalo. El iterador begin apunta a un elemento igual.

Para ayudar a evitar el `concurrent_unordered_map` interbloqueo, ningún método de bloqueo contiene un bloqueo cuando llama al asignador de memoria, funciones hash u otro código definido por el usuario. Además, debe asegurarse de que la función hash siempre evalúa las claves iguales al mismo valor. Las mejores funciones hash distribuyen las claves uniformemente a través del espacio de código hash.

### <a name="concurrency-safe-operations"></a><a name="map-safety"></a>Operaciones seguras para simultaneidad

La `concurrent_unordered_map` clase habilita las operaciones de inserción y acceso a elementos seguras para simultaneidad. Las operaciones de inserción no invalidan los punteros o iteradores existentes. Las operaciones de acceso de iterador y recorrido también son seguras para simultaneidad. Aquí, la seguridad para simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de inicialización de elementos, o de un orden de recorrido determinado. En la tabla siguiente `concurrent_unordered_map` se muestran los métodos y operadores más utilizados que son seguros para simultaneidad.

|||||
|-|-|-|-|
|[En](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insertar](reference/concurrent-unordered-map-class.md#insert)|`size`|

Aunque `count` se puede llamar al método de forma segura desde subprocesos en ejecución simultánea, diferentes subprocesos pueden recibir resultados diferentes si se inserta simultáneamente un nuevo valor en el contenedor.

En la tabla siguiente se muestran los métodos y operadores más utilizados que no son seguros para simultaneidad.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operador](reference/concurrent-unordered-map-class.md#operator_eq)

Además de estos métodos, `unsafe_` cualquier método que comience con tampoco es seguro para simultaneidad.

[[Superior](#top)]

## <a name="concurrent_unordered_multimap-class"></a><a name="unordered_multimap"></a>Clase concurrent_unordered_multimap

La clase [concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) es `concurrent_unordered_map` muy similar a la clase, excepto que permite que varios valores se asignen a la misma clave. También difiere de `concurrent_unordered_map` las siguientes maneras:

- El método [concurrent_unordered_multimap::insert](reference/concurrent-unordered-multimap-class.md#insert) devuelve `std::pair<iterator, bool>`un iterador en lugar de .

- La `concurrent_unordered_multimap` clase no `operator[]` proporciona `at` ni el método.

En el ejemplo siguiente se `concurrent_unordered_multimap`muestra la estructura básica para utilizar . En este ejemplo se insertan teclas de caracteres en el intervalo ['a', 'i']. `concurrent_unordered_multimap`permite que una clave tenga varios valores.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Superior](#top)]

## <a name="concurrent_unordered_set-class"></a><a name="unordered_set"></a>Clase concurrent_unordered_set

La clase [concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) se `concurrent_unordered_map` parece mucho a la clase, excepto que administra valores en lugar de pares de clave y valor. La `concurrent_unordered_set` clase no `operator[]` proporciona `at` ni el método.

En el ejemplo siguiente se `concurrent_unordered_set`muestra la estructura básica para utilizar . En este ejemplo se insertan valores de caracteres en el intervalo ['a', 'i']. Es seguro realizar las inserciones en paralelo.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Superior](#top)]

## <a name="concurrent_unordered_multiset-class"></a><a name="unordered_multiset"></a>Clase concurrent_unordered_multiset

La [clase concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) se `concurrent_unordered_set` parece mucho a la clase, excepto que permite valores duplicados. También difiere de `concurrent_unordered_set` las siguientes maneras:

- El método [concurrent_unordered_multiset::insert](reference/concurrent-unordered-multiset-class.md#insert) devuelve `std::pair<iterator, bool>`un iterador en lugar de .

- La `concurrent_unordered_multiset` clase no `operator[]` proporciona `at` ni el método.

En el ejemplo siguiente se `concurrent_unordered_multiset`muestra la estructura básica para utilizar . En este ejemplo se insertan valores de caracteres en el intervalo ['a', 'i']. `concurrent_unordered_multiset`permite que un valor se produzca varias veces.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Superior](#top)]

## <a name="combinable-class"></a><a name="combinable"></a>clase combinable

La clase [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) proporciona almacenamiento local de subprocesos reutilizable que le permite realizar cálculos detallados y, a continuación, combinar esos cálculos en un resultado final. Puede pensar en un objeto `combinable` como una variable de reducción.

La `combinable` clase es útil cuando tiene un recurso que se comparte entre varios subprocesos o tareas. La `combinable` clase le ayuda a eliminar el estado compartido proporcionando acceso a los recursos compartidos de forma sin bloqueos. Por lo tanto, esta clase proporciona una alternativa al uso de un mecanismo de sincronización, por ejemplo, una exclusión mutua, para sincronizar el acceso a los datos compartidos desde varios subprocesos.

### <a name="methods-and-features"></a><a name="combinable-features"></a>Métodos y características

En la tabla siguiente se muestran algunos de los métodos importantes de la `combinable` clase. Para obtener más `combinable` información acerca de todos los métodos de clase, vea [clase combinable](../../parallel/concrt/reference/combinable-class.md).

|Método|Descripción|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Recupera una referencia a la variable local asociada al contexto de subproceso actual.|
|[Claro](reference/combinable-class.md#clear)|Quita todas las variables locales de subproceso del `combinable` objeto.|
|[Combinar](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Utiliza la función combine proporcionada para generar un valor final a partir del conjunto de todos los cálculos locales de subprocesos.|

La `combinable` clase es una clase de plantilla que se parametriza en el resultado combinado final. Si se llama al `T` constructor predeterminado, el tipo de parámetro de plantilla debe tener un constructor predeterminado y un constructor de copia. Si `T` el tipo de parámetro de plantilla no tiene un constructor predeterminado, llame a la versión sobrecargada del constructor que toma una función de inicialización como parámetro.

Puede almacenar datos adicionales `combinable` en un objeto después de llamar a los métodos [combine](reference/combinable-class.md#combine) o [combine_each.](reference/combinable-class.md#combine_each) También puede llamar `combine` `combine_each` a los métodos y varias veces. Si no cambia `combinable` ningún valor `combine` local `combine_each` en un objeto, los métodos y producen el mismo resultado cada vez que se llama a ellos.

### <a name="examples"></a><a name="combinable-examples"></a>Ejemplos

Para obtener ejemplos sobre `combinable` cómo utilizar la clase, consulte los temas siguientes:

- [Cómo: Usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Cómo: Usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Superior](#top)]

## <a name="related-topics"></a>Temas relacionados

[Cómo: Usar contenedores paralelos para aumentar la eficacia](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Muestra cómo usar contenedores paralelos para almacenar y tener acceso a datos de forma eficaz en paralelo.

[Cómo: Usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Muestra cómo usar `combinable` la clase para eliminar el estado compartido y, por lo continuación, mejorar el rendimiento.

[Cómo: Usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Muestra cómo utilizar `combine` una función para combinar conjuntos locales de subprocesos de datos.

[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Describe la PPL, que proporciona un modelo de programación imperativo que promueve la escalabilidad y la facilidad de uso para el desarrollo de aplicaciones simultáneas.

## <a name="reference"></a>Referencia

[Clase concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)

[Clase concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)

[Clase concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[Clase concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[Clase concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[Clase concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[clase combinable](../../parallel/concrt/reference/combinable-class.md)
