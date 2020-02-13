---
title: Contenedores y objetos paralelos
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 04b38fdc66a5c37a1780deaae4ae165f63238d93
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142907"
---
# <a name="parallel-containers-and-objects"></a>Contenedores y objetos paralelos

La biblioteca de patrones de procesamiento paralelo (PPL) incluye varios contenedores y objetos que proporcionan acceso seguro para subprocesos a sus elementos.

Un *contenedor simultáneo* proporciona acceso seguro para simultaneidad a las operaciones más importantes. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado. La funcionalidad de estos contenedores es similar a la proporcionada por la C++ biblioteca estándar. Por ejemplo, la clase [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) es similar a la clase [STD:: Vector](../../standard-library/vector-class.md) , salvo que la clase `concurrent_vector` permite anexar elementos en paralelo. Use contenedores simultáneos cuando tenga código paralelo que requiera acceso de lectura y escritura al mismo contenedor.

Un *objeto simultáneo* se comparte simultáneamente entre los componentes. Un proceso que calcula el estado de un objeto simultáneo en paralelo produce el mismo resultado que otro proceso que calcula el mismo estado en serie. La clase [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) es un ejemplo de un tipo de objeto simultáneo. La clase `combinable` permite realizar cálculos en paralelo y, a continuación, combinar estos cálculos en un resultado final. Use objetos simultáneos cuando, de lo contrario, usaría un mecanismo de sincronización, por ejemplo, una exclusión mutua, para sincronizar el acceso a una variable o un recurso compartido.

## <a name="top"></a> Secciones

En este tema se describen los siguientes contenedores y objetos paralelos en detalle.

Contenedores simultáneos:

- [concurrent_vector (clase)](#vector)

   - [Diferencias entre concurrent_vector y Vector](#vector-differences)

   - [Operaciones seguras para simultaneidad](#vector-safety)

   - [Seguridad de excepciones](#vector-exceptions)

- [concurrent_queue (clase)](#queue)

   - [Diferencias entre concurrent_queue y Queue](#queue-differences)

   - [Operaciones seguras para simultaneidad](#queue-safety)

   - [Compatibilidad con iteradores](#queue-iterators)

- [concurrent_unordered_map (clase)](#unordered_map)

   - [Diferencias entre concurrent_unordered_map y unordered_map](#map-differences)

   - [Operaciones seguras para simultaneidad](#map-safety)

- [concurrent_unordered_multimap (clase)](#unordered_multimap)

- [concurrent_unordered_set (clase)](#unordered_set)

- [concurrent_unordered_multiset (clase)](#unordered_multiset)

Objetos simultáneos:

- [combinable (clase)](#combinable)

   - [Métodos y características](#combinable-features)

   - [Ejemplos](#combinable-examples)

## <a name="vector"></a>concurrent_vector (clase)

La clase [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) es una clase de contenedor de secuencias que, al igual que la clase [STD:: Vector](../../standard-library/vector-class.md) , permite tener acceso de forma aleatoria a sus elementos. La clase `concurrent_vector` habilita las operaciones de anexión y acceso a elementos con seguridad de simultaneidad. Las operaciones de anexión no invalidan los punteros o iteradores existentes. El acceso a iterador y las operaciones de recorrido también son seguras para simultaneidad. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado.

### <a name="vector-differences"></a>Diferencias entre concurrent_vector y Vector

La clase `concurrent_vector` es muy similar a la clase `vector`. La complejidad de las operaciones append, acceso a elementos y acceso a iterador en un objeto `concurrent_vector` es igual que para un objeto `vector`. Los puntos siguientes muestran dónde difiere `concurrent_vector` de `vector`:

- Append, acceso a elementos, acceso a iterador y las operaciones de recorrido de iterador en un objeto `concurrent_vector` son seguras para simultaneidad.

- Solo puede agregar elementos al final de un objeto de `concurrent_vector`. La clase `concurrent_vector` no proporciona el método `insert`.

- Un objeto `concurrent_vector` no utiliza la [semántica de movimiento](../../cpp/rvalue-reference-declarator-amp-amp.md) cuando se anexa a él.

- La clase `concurrent_vector` no proporciona los métodos `erase` o `pop_back`. Como con `vector`, utilice el método [Clear](reference/concurrent-vector-class.md#clear) para quitar todos los elementos de un objeto `concurrent_vector`.

- La clase `concurrent_vector` no almacena sus elementos de forma contigua en la memoria. Por lo tanto, no se puede utilizar la clase `concurrent_vector` en todas las formas en que se puede utilizar una matriz. Por ejemplo, para una variable denominada `v` de tipo `concurrent_vector`, la expresión `&v[0]+2` produce un comportamiento indefinido.

- La clase `concurrent_vector` define los métodos [grow_by](reference/concurrent-vector-class.md#grow_by) y [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) . Estos métodos son similares al método de [cambio de tamaño](reference/concurrent-vector-class.md#resize) , con la salvedad de que son seguros para simultaneidad.

- Un objeto `concurrent_vector` no reubica sus elementos al anexarlo o cambiar su tamaño. Esto permite que los punteros e iteradores existentes sigan siendo válidos durante las operaciones simultáneas.

- El runtime no define una versión especializada de `concurrent_vector` para el tipo `bool`.

### <a name="vector-safety"></a>Operaciones seguras para simultaneidad

Todos los métodos que anexan o aumentan el tamaño de un objeto `concurrent_vector`, o tienen acceso a un elemento de un objeto `concurrent_vector`, son seguros para simultaneidad. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado. La excepción a esta regla es el método `resize`.

En la tabla siguiente se muestran los métodos y operadores de `concurrent_vector` comunes que son seguros para simultaneidad.

||||
|-|-|-|
|[at](reference/concurrent-vector-class.md#at)|[end](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[begin](reference/concurrent-vector-class.md#begin)|[front](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[back](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[capacidad](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[size](reference/concurrent-vector-class.md#size)|

Las operaciones que el motor en tiempo de ejecución C++ proporciona para la compatibilidad con la biblioteca estándar, por ejemplo, `reserve`, no son seguras para simultaneidad. En la tabla siguiente se muestran los métodos y operadores comunes que no son seguros para simultaneidad.

|||
|-|-|
|[assign](reference/concurrent-vector-class.md#assign)|[reserve](reference/concurrent-vector-class.md#reserve)|
|[clear](reference/concurrent-vector-class.md#clear)|[resize](reference/concurrent-vector-class.md#resize)|
|[operator=](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Las operaciones que modifican el valor de los elementos existentes no son seguras para simultaneidad. Use un objeto de sincronización, como un objeto [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) para sincronizar las operaciones de lectura y escritura simultáneas en el mismo elemento de datos. Para obtener más información sobre los objetos de sincronización, vea [Synchronization Data Structures](../../parallel/concrt/synchronization-data-structures.md).

Al convertir el código existente que usa `vector` para usar `concurrent_vector`, las operaciones simultáneas pueden hacer que el comportamiento de la aplicación cambie. Por ejemplo, considere el siguiente programa que realiza simultáneamente dos tareas en un objeto `concurrent_vector`. La primera tarea anexa elementos adicionales a un objeto `concurrent_vector`. La segunda tarea calcula la suma de todos los elementos del mismo objeto.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Aunque el método `end` es seguro para simultaneidad, una llamada simultánea al método [push_back](reference/concurrent-vector-class.md#push_back) hace que el valor devuelto por `end` cambie. El número de elementos que el iterador atraviesa es indeterminado. Por lo tanto, este programa puede generar un resultado diferente cada vez que se ejecuta. Cuando el tipo de elemento no es trivial, es posible que exista una condición de carrera entre las llamadas `push_back` y `end`. El método `end` puede devolver un elemento que está asignado, pero que no está completamente inicializado.

### <a name="vector-exceptions"></a>Seguridad de excepciones

Si una operación de crecimiento o asignación produce una excepción, el estado del objeto `concurrent_vector` deja de ser válido. El comportamiento de un objeto `concurrent_vector` que se encuentra en un estado no válido es indefinido, a menos que se indique lo contrario. Sin embargo, el destructor siempre libera la memoria que el objeto asigna, incluso si el objeto está en un estado no válido.

El tipo de datos de los elementos de Vector, `T`, debe cumplir los siguientes requisitos. De lo contrario, el comportamiento de la clase `concurrent_vector` es indefinido.

- El destructor no debe iniciar.

- Si se produce el constructor predeterminado o de copia, el destructor no debe declararse mediante la palabra clave `virtual` y debe funcionar correctamente con memoria inicializada en cero.

[[Arriba](#top)]

## <a name="queue"></a>concurrent_queue (clase)

La clase [Concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) , al igual que la clase [STD:: Queue](../../standard-library/queue-class.md) , permite tener acceso a sus elementos delante y detrás. La clase `concurrent_queue` habilita las operaciones de puesta en cola y eliminación de la cola seguras para simultaneidad. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado. La clase `concurrent_queue` también proporciona compatibilidad de iterador que no es segura para simultaneidad.

### <a name="queue-differences"></a>Diferencias entre concurrent_queue y Queue

La clase `concurrent_queue` es muy similar a la clase `queue`. Los puntos siguientes muestran dónde difiere `concurrent_queue` de `queue`:

- Las operaciones enqueue y dequeue en un objeto `concurrent_queue` son seguras para simultaneidad.

- La clase `concurrent_queue` proporciona compatibilidad de iterador que no es segura para simultaneidad.

- La clase `concurrent_queue` no proporciona los métodos `front` o `pop`. La clase `concurrent_queue` reemplaza estos métodos definiendo el método [try_pop](reference/concurrent-queue-class.md#try_pop) .

- La clase `concurrent_queue` no proporciona el método `back`. Por lo tanto, no se puede hacer referencia al final de la cola.

- La clase `concurrent_queue` proporciona el método [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) en lugar del método `size`. El método `unsafe_size` no es seguro para simultaneidad.

### <a name="queue-safety"></a>Operaciones seguras para simultaneidad

Todos los métodos que se ponen en cola o se quitan de un objeto `concurrent_queue` son seguros para simultaneidad. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado.

En la tabla siguiente se muestran los métodos y operadores de `concurrent_queue` comunes que son seguros para simultaneidad.

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Aunque el método `empty` es seguro para simultaneidad, una operación simultánea puede hacer que la cola crezca o se reduzca antes de que se devuelva el método `empty`.

En la tabla siguiente se muestran los métodos y operadores comunes que no son seguros para simultaneidad.

|||
|-|-|
|[clear](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="queue-iterators"></a>Compatibilidad con iteradores

El `concurrent_queue` proporciona iteradores que no son seguros para simultaneidad. Se recomienda usar estos iteradores solo para la depuración.

Un iterador `concurrent_queue` atraviesa elementos solo en la dirección hacia delante. En la tabla siguiente se muestran los operadores que admite cada iterador.

|Operator|Descripción|
|--------------|-----------------|
|`operator++`|Avanza al siguiente elemento de la cola. Este operador se sobrecarga para proporcionar la semántica de incremento previo y posterior al incremento.|
|`operator*`|Recupera una referencia al elemento actual.|
|`operator->`|Recupera un puntero al elemento actual.|

[[Arriba](#top)]

## <a name="unordered_map"></a>concurrent_unordered_map (clase)

La clase [Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) es una clase de contenedor asociativo que, al igual que la clase [std:: unordered_map](../../standard-library/unordered-map-class.md) , controla una secuencia de longitud variable de elementos de tipo [STD::p Air\<const Key, Ty >](../../standard-library/pair-structure.md). Piense en un mapa no ordenado como un diccionario en el que puede Agregar un par clave-valor o buscar un valor por clave. Esta clase es útil cuando hay varios subprocesos o tareas que tienen que acceder simultáneamente a un contenedor compartido, insertar en él o actualizarlo.

En el ejemplo siguiente se muestra la estructura básica del uso de `concurrent_unordered_map`. En este ejemplo se insertan claves de caracteres en el intervalo [' a ', ' i ']. Dado que el orden de las operaciones es indeterminado, el valor final de cada clave también es indeterminado. Sin embargo, es seguro realizar las inserciones en paralelo.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Para obtener un ejemplo en el que se usa `concurrent_unordered_map` para realizar una operación de asignación y reducción en paralelo, vea [Cómo: realizar operaciones de asignación y reducción en paralelo](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

### <a name="map-differences"></a>Diferencias entre concurrent_unordered_map y unordered_map

La clase `concurrent_unordered_map` es muy similar a la clase `unordered_map`. Los puntos siguientes muestran dónde difiere `concurrent_unordered_map` de `unordered_map`:

- Los métodos `erase`, `bucket`, `bucket_count`y `bucket_size` se denominan `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`y `unsafe_bucket_size`, respectivamente. La Convención de nomenclatura de `unsafe_` indica que estos métodos no son seguros para simultaneidad. Para obtener más información sobre la seguridad de simultaneidad, consulte [operaciones seguras de simultaneidad](#map-safety).

- Las operaciones de inserción no invalidan los punteros o iteradores existentes, ni cambian el orden de los elementos que ya existen en el mapa. Las operaciones de inserción y recorrido se pueden producir simultáneamente.

- `concurrent_unordered_map` solo admite la iteración hacia delante.

- La inserción no invalida ni actualiza los iteradores devueltos por `equal_range`. La inserción puede anexar elementos distintos al final del intervalo. El iterador inicial apunta a un elemento igual.

Para ayudar a evitar el interbloqueo, ningún método de `concurrent_unordered_map` contiene un bloqueo cuando llama al asignador de memoria, a las funciones hash u otro código definido por el usuario. Además, debe asegurarse de que la función hash siempre evalúa las mismas claves con el mismo valor. Las mejores funciones hash distribuyen las claves uniformemente en el espacio de código hash.

### <a name="map-safety"></a>Operaciones seguras para simultaneidad

La clase `concurrent_unordered_map` habilita las operaciones de inserción y acceso a elementos con seguridad de simultaneidad. Las operaciones de inserción no invalidan los punteros o iteradores existentes. El acceso a iterador y las operaciones de recorrido también son seguras para simultaneidad. Aquí, la seguridad de simultaneidad significa que los punteros o iteradores siempre son válidos. No es una garantía de la inicialización de elementos o de un orden de cruce determinado. En la tabla siguiente se muestran los métodos y operadores de `concurrent_unordered_map` usados habitualmente que son seguros para simultaneidad.

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|

Aunque se puede llamar al método `count` de forma segura a partir de subprocesos que se ejecutan simultáneamente, los distintos subprocesos pueden recibir resultados diferentes si se inserta un nuevo valor al mismo tiempo en el contenedor.

En la tabla siguiente se muestran los métodos y operadores usados comúnmente que no son seguros para simultaneidad.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq)

Además de estos métodos, cualquier método que comience por `unsafe_` tampoco es seguro para simultaneidad.

[[Arriba](#top)]

## <a name="unordered_multimap"></a>concurrent_unordered_multimap (clase)

La clase [Concurrency:: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) es muy similar a la clase `concurrent_unordered_map`, salvo que permite que varios valores se asignen a la misma clave. También difiere de `concurrent_unordered_map` de las siguientes maneras:

- El método [concurrent_unordered_multimap:: Insert](reference/concurrent-unordered-multimap-class.md#insert) devuelve un iterador en lugar de `std::pair<iterator, bool>`.

- La clase `concurrent_unordered_multimap` no proporciona `operator[]` ni el método `at`.

En el ejemplo siguiente se muestra la estructura básica del uso de `concurrent_unordered_multimap`. En este ejemplo se insertan claves de caracteres en el intervalo [' a ', ' i ']. `concurrent_unordered_multimap` permite que una clave tenga varios valores.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Arriba](#top)]

## <a name="unordered_set"></a>concurrent_unordered_set (clase)

La clase [Concurrency:: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) es muy similar a la clase `concurrent_unordered_map`, salvo que administra los valores en lugar de los pares clave-valor. La clase `concurrent_unordered_set` no proporciona `operator[]` ni el método `at`.

En el ejemplo siguiente se muestra la estructura básica del uso de `concurrent_unordered_set`. En este ejemplo se insertan valores de caracteres en el intervalo [' a ', ' i ']. Es seguro realizar las inserciones en paralelo.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Arriba](#top)]

## <a name="unordered_multiset"></a>concurrent_unordered_multiset (clase)

La clase [Concurrency:: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) es muy similar a la clase `concurrent_unordered_set`, salvo que permite valores duplicados. También difiere de `concurrent_unordered_set` de las siguientes maneras:

- El método [concurrent_unordered_multiset:: Insert](reference/concurrent-unordered-multiset-class.md#insert) devuelve un iterador en lugar de `std::pair<iterator, bool>`.

- La clase `concurrent_unordered_multiset` no proporciona `operator[]` ni el método `at`.

En el ejemplo siguiente se muestra la estructura básica del uso de `concurrent_unordered_multiset`. En este ejemplo se insertan valores de caracteres en el intervalo [' a ', ' i ']. `concurrent_unordered_multiset` permite que se produzca un valor varias veces.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Arriba](#top)]

## <a name="combinable"></a>combinable (clase)

La clase [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) proporciona almacenamiento local de subprocesos reutilizable que permite realizar cálculos específicos y, a continuación, combinar esos cálculos en un resultado final. Puede pensar en un objeto `combinable` como una variable de reducción.

La clase `combinable` es útil cuando se tiene un recurso compartido entre varios subprocesos o tareas. La clase `combinable` ayuda a eliminar el estado compartido al proporcionar acceso a los recursos compartidos sin bloqueos. Por lo tanto, esta clase proporciona una alternativa al uso de un mecanismo de sincronización, por ejemplo, una exclusión mutua, para sincronizar el acceso a los datos compartidos desde varios subprocesos.

### <a name="combinable-features"></a>Métodos y características

En la tabla siguiente se muestran algunos de los métodos importantes de la clase `combinable`. Para obtener más información acerca de todos los métodos de clase `combinable`, vea [clase combinable](../../parallel/concrt/reference/combinable-class.md).

|Método|Descripción|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Recupera una referencia a la variable local que está asociada al contexto del subproceso actual.|
|[clear](reference/combinable-class.md#clear)|Quita todas las variables locales del subproceso del objeto `combinable`.|
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Usa la función de combinación proporcionada para generar un valor final a partir del conjunto de todos los cálculos locales de subprocesos.|

La clase `combinable` es una clase de plantilla que está parametrizada en el resultado final combinado. Si llama al constructor predeterminado, el tipo de parámetro de plantilla `T` debe tener un constructor predeterminado y un constructor de copias. Si el tipo de parámetro de plantilla `T` no tiene un constructor predeterminado, llame a la versión sobrecargada del constructor que toma una función de inicialización como su parámetro.

Puede almacenar datos adicionales en un objeto `combinable` después de llamar a los métodos [combine](reference/combinable-class.md#combine) o [combine_each](reference/combinable-class.md#combine_each) . También puede llamar varias veces a los métodos `combine` y `combine_each`. Si no cambia ningún valor local en un objeto `combinable`, los métodos `combine` y `combine_each` producen el mismo resultado cada vez que se llaman.

### <a name="combinable-examples"></a> Ejemplos

Para obtener ejemplos sobre cómo usar la clase `combinable`, vea los temas siguientes:

- [Procedimiento para usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Procedimiento para usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Arriba](#top)]

## <a name="related-topics"></a>Temas relacionados

[Procedimiento para usar contenedores paralelos para aumentar la eficacia](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Muestra cómo usar contenedores paralelos para almacenar y obtener acceso a los datos en paralelo de forma eficaz.

[Procedimiento para usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Muestra cómo usar la clase `combinable` para eliminar el estado compartido y, por tanto, mejorar el rendimiento.

[Procedimiento para usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Muestra cómo utilizar una función de `combine` para combinar conjuntos de datos locales de subprocesos.

[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Describe la biblioteca PPL, que proporciona un modelo de programación imperativo que promueve la escalabilidad y la facilidad de uso para desarrollar aplicaciones simultáneas.

## <a name="reference"></a>Referencia

[concurrent_vector (clase)](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue (clase)](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map (clase)](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap (clase)](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set (clase)](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset (clase)](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable (clase)](../../parallel/concrt/reference/combinable-class.md)
