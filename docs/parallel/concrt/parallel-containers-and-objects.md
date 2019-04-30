---
title: Contenedores y objetos paralelos
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: bcf3ead9fe945ecb2246fdb28b7f67cd51b1238b
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346328"
---
# <a name="parallel-containers-and-objects"></a>Contenedores y objetos paralelos

La biblioteca de patrones paralelos (PPL) incluye varios contenedores y objetos que proporcionan acceso seguro para subprocesos a sus elementos.

Un *contenedor simultáneo* proporciona acceso seguro para simultaneidad a las operaciones más importantes. La funcionalidad de estos contenedores se parece a las proporcionadas por la biblioteca estándar de C++. Por ejemplo, el [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) es similar a la [std:: vector](../../standard-library/vector-class.md) clase salvo que el `concurrent_vector` clase le permite anexar elementos en paralelo. Utilice contenedores simultáneos cuando haya código paralelo que requiere acceso de lectura y escritura en el mismo contenedor.

Un *objeto simultáneo* comparten al mismo tiempo los componentes. Un proceso que calcula el estado de un objeto simultáneo en paralelo, produce el mismo resultado que otro proceso que calcula el mismo estado en serie. El [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) clase es un ejemplo de un tipo de objeto simultáneo. La `combinable` clase le permite realizar cálculos en paralelo y, a continuación, combine estos cálculos en un resultado final. Utilizar objetos simultáneos que se utilizaría en caso contrario, un mecanismo de sincronización, por ejemplo, una exclusión mutua, para sincronizar el acceso a una variable compartida o un recurso.

##  <a name="top"></a> Secciones

En este tema se describe los siguientes contenedores y objetos paralelos en detalle.

Contenedores simultáneos:

- [concurrent_vector (clase)](#vector)

   - [Diferencias entre concurrent_vector y vector](#vector-differences)

   - [Operaciones seguras para simultaneidad](#vector-safety)

   - [Seguridad de las excepciones](#vector-exceptions)

- [concurrent_queue (clase)](#queue)

   - [Diferencias entre concurrent_queue y cola](#queue-differences)

   - [Operaciones seguras para simultaneidad](#queue-safety)

   - [Compatibilidad de los iteradores](#queue-iterators)

- [concurrent_unordered_map (clase)](#unordered_map)

   - [Unordered_map y diferencias entre concurrent_unordered_map)](#map-differences)

   - [Operaciones seguras para simultaneidad](#map-safety)

- [concurrent_unordered_multimap (clase)](#unordered_multimap)

- [concurrent_unordered_set (clase)](#unordered_set)

- [concurrent_unordered_multiset (clase)](#unordered_multiset)

Objetos simultáneos:

- [combinable (clase)](#combinable)

   - [Los métodos y las características](#combinable-features)

   - [Ejemplos](#combinable-examples)

##  <a name="vector"></a> concurrent_vector (clase)

El [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) es una clase de contenedor de secuencia que, al igual que el [std:: vector](../../standard-library/vector-class.md) class, le permite acceder de forma aleatoria a sus elementos. La `concurrent_vector` clase permite anexar segura para simultaneidad y el elemento de acceso a las operaciones. Anexar las operaciones no invalidan existentes punteros o iteradores. Las operaciones de acceso y recorrido de iterador también son seguras para simultaneidad.

###  <a name="vector-differences"></a> Diferencias entre concurrent_vector y vector

El `concurrent_vector` se parezca la clase el `vector` clase. La complejidad de anexión, acceso a elementos y operaciones de acceso de iterador en un `concurrent_vector` objeto son los mismos que para un `vector` objeto. Los siguientes puntos muestran dónde `concurrent_vector` difiere `vector`:

- Anexar, acceso de elemento, acceso de iterador y las operaciones de recorrido de iterador en un `concurrent_vector` objeto son seguras para simultaneidad.

- Puede agregar elementos al final de un `concurrent_vector` objeto. El `concurrent_vector` clase no proporciona el `insert` método.

- Un `concurrent_vector` no usa el objeto [semántica de transferencia](../../cpp/rvalue-reference-declarator-amp-amp.md) cuando se anexa a él.

- El `concurrent_vector` clase no proporciona la `erase` o `pop_back` métodos. Igual que con `vector`, utilice el [borrar](reference/concurrent-vector-class.md#clear) método para quitar todos los elementos de un `concurrent_vector` objeto.

- El `concurrent_vector` no almacena sus elementos forma contigua en la memoria. Por lo tanto, no puede usar el `concurrent_vector` clase en todas las formas en que puede usar una matriz. Por ejemplo, para una variable denominada `v` typu `concurrent_vector`, la expresión `&v[0]+2` produce un comportamiento indefinido.

- El `concurrent_vector` clase define la [grow_by](reference/concurrent-vector-class.md#grow_by) y [grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least) métodos. Estos métodos son similares a los [cambiar el tamaño de](reference/concurrent-vector-class.md#resize) método, salvo que son seguras para simultaneidad.

- Un `concurrent_vector` objeto no reubica sus elementos cuando se anexa a él o cambiar su tamaño. Esto permite punteros existentes e iteradores sigan siendo válidos durante las operaciones simultáneas.

- El tiempo de ejecución no define una versión especializada de `concurrent_vector` tipo `bool`.

###  <a name="vector-safety"></a> Operaciones seguras para simultaneidad

Todos los métodos que anexar o aumentan el tamaño de un `concurrent_vector` de objeto, o tener acceso a un elemento en un `concurrent_vector` de objetos, que son seguras para simultaneidad. La excepción a esta regla es la `resize` método.

En la tabla siguiente se muestra el común `concurrent_vector` métodos y operadores que son seguras para simultaneidad.

||||
|-|-|-|
|[at](reference/concurrent-vector-class.md#at)|[end](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[begin](reference/concurrent-vector-class.md#begin)|[front](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[back](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[capacity](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[size](reference/concurrent-vector-class.md#size)|

Las operaciones que el runtime proporciona para ofrecer compatibilidad con la biblioteca estándar de C++, por ejemplo, `reserve`, no son seguras para simultaneidad. La tabla siguiente muestran los métodos y operadores que no son seguras para simultaneidad comunes.

|||
|-|-|
|[assign](reference/concurrent-vector-class.md#assign)|[reserve](reference/concurrent-vector-class.md#reserve)|
|[clear](reference/concurrent-vector-class.md#clear)|[resize](reference/concurrent-vector-class.md#resize)|
|[operator=](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

Las operaciones que modifican el valor de los elementos existentes no son seguras para simultaneidad. Usar un objeto de sincronización, como un [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objeto para sincronizar simultáneas de lectura y las operaciones de escritura al mismo elemento de datos. Para obtener más información acerca de los objetos de sincronización, consulte [estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md).

Cuando convierta código existente que usa `vector` usar `concurrent_vector`, operaciones simultáneas pueden hacer que el comportamiento de la aplicación para cambiar. Por ejemplo, considere el siguiente programa que realiza dos tareas simultáneamente en un `concurrent_vector` objeto. La primera tarea anexa elementos adicionales a un `concurrent_vector` objeto. La segunda tarea calcula la suma de todos los elementos en el mismo objeto.

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

Aunque el `end` método es seguro para simultaneidad, una llamada simultánea activa a la [push_back](reference/concurrent-vector-class.md#push_back) método hace que el valor devuelto por `end` a cambiar. El número de elementos que atraviesa el iterador es indeterminado. Por lo tanto, este programa puede producir un resultado diferente cada vez que se ejecuta.

###  <a name="vector-exceptions"></a> Seguridad de las excepciones

Si una operación de crecimiento o asignación produce una excepción, el estado de la `concurrent_vector` objeto deja de ser válido. El comportamiento de un `concurrent_vector` no está definido el objeto que se encuentra en un estado no válido a menos que se indique lo contrario. Sin embargo, el destructor siempre libera la memoria que asigna el objeto, incluso si el objeto está en un estado no válido.

El tipo de datos de los elementos del vector, `T`, debe cumplir los requisitos siguientes. En caso contrario, el comportamiento de la `concurrent_vector` clase es indefinida.

- El destructor no debe producir.

- Si se produce el constructor predeterminado o de copia, el destructor no debe declararse mediante el `virtual` palabra clave y deben trabajar correctamente con memoria inicializa a cero.

[[Arriba](#top)]

##  <a name="queue"></a> concurrent_queue (clase)

El [Concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) clase, al igual que el [std:: Queue](../../standard-library/queue-class.md) class, le permite obtener acceso a sus elementos anteriores y posteriores. La `concurrent_queue` clase segura para simultaneidad de permite poner en cola y las operaciones de eliminación de cola. La `concurrent_queue` clase también proporciona compatibilidad de los iteradores que no es segura para simultaneidad.

###  <a name="queue-differences"></a> Diferencias entre concurrent_queue y cola

El `concurrent_queue` se parezca la clase el `queue` clase. Los siguientes puntos muestran dónde `concurrent_queue` difiere `queue`:

- Enqueue y dequeue operaciones en un `concurrent_queue` objeto son seguras para simultaneidad.

- La `concurrent_queue` clase proporciona compatibilidad de los iteradores que no es segura para simultaneidad.

- El `concurrent_queue` clase no proporciona la `front` o `pop` métodos. El `concurrent_queue` clase reemplaza estos métodos definiendo el [try_pop](reference/concurrent-queue-class.md#try_pop) método.

- El `concurrent_queue` clase no proporciona el `back` método. Por lo tanto, no puede hacer referencia al final de la cola.

- El `concurrent_queue` clase proporciona el [unsafe_size](reference/concurrent-queue-class.md#unsafe_size) método en lugar de la `size` método. El `unsafe_size` método no es seguro para simultaneidad.

###  <a name="queue-safety"></a> Operaciones seguras para simultaneidad

Todos los métodos que ponen en cola a o quitar de la cola de un `concurrent_queue` objeto son seguras para simultaneidad.

En la tabla siguiente se muestra el común `concurrent_queue` métodos y operadores que son seguras para simultaneidad.

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

Aunque el `empty` método es seguro para simultaneidad, una operación simultánea puede hacer que aumente o disminuya antes de la cola de la `empty` devuelve del método.

La tabla siguiente muestran los métodos y operadores que no son seguras para simultaneidad comunes.

|||
|-|-|
|[clear](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

###  <a name="queue-iterators"></a> Compatibilidad de los iteradores

El `concurrent_queue` proporciona iteradores que no son seguras para simultaneidad. Se recomienda usar estos iteradores únicamente para la depuración.

Un `concurrent_queue` iterador atraviesa los elementos en la dirección de avance. En la tabla siguiente se muestra a los operadores que admite cada iterador.

|Operador|Descripción|
|--------------|-----------------|
|`operator++`|Avanza al siguiente elemento de la cola. Este operador se sobrecarga para proporcionar la semántica de incremento previo y posterior al incremento.|
|`operator*`|Recupera una referencia al elemento actual.|
|`operator->`|Recupera un puntero al elemento actual.|

[[Arriba](#top)]

##  <a name="unordered_map"></a> concurrent_unordered_map (clase)

El [Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) es una clase de contenedor asociativo que, al igual que el [std:: unordered_map](../../standard-library/unordered-map-class.md) class, que controla una secuencia de longitud variable de elementos de tipo [std:: Pair\<const Key, Ty >](../../standard-library/pair-structure.md). Piense en una asignación no ordenada como un diccionario que puede agregar un par de clave y valor a o buscar un valor por clave. Esta clase es útil cuando tiene varios subprocesos o tareas que deben tener acceso a un contenedor compartido, inserte en ella o actualizarlo al mismo tiempo.

El ejemplo siguiente muestra la estructura básica para el uso de `concurrent_unordered_map`. En este ejemplo inserta las teclas de carácter en el intervalo ['a', ' i']. Dado que el orden de operaciones es indeterminado, el valor final de cada clave también es indeterminado. Sin embargo, es seguro realizar las inserciones en paralelo.

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

Para obtener un ejemplo que usa `concurrent_unordered_map` para realizar una asignación y reducir las operaciones en paralelo, vea [Cómo: Realizar la asignación y reducir las operaciones en paralelo](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

###  <a name="map-differences"></a> Unordered_map y diferencias entre concurrent_unordered_map)

El `concurrent_unordered_map` se parezca la clase el `unordered_map` clase. Los siguientes puntos muestran dónde `concurrent_unordered_map` difiere `unordered_map`:

- El `erase`, `bucket`, `bucket_count`, y `bucket_size` se denominan métodos `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`, y `unsafe_bucket_size`, respectivamente. El `unsafe_` convención de nomenclatura indica que estos métodos no son seguras para simultaneidad. Para obtener más información acerca de la seguridad de simultaneidad, consulte [operaciones seguras para simultaneidad](#map-safety).

- Las operaciones de inserción no invalidan existentes punteros o iteradores, ni cambian el orden de los elementos que ya existen en el mapa. Insertar y recorrer las operaciones pueden realizarse al mismo tiempo.

- `concurrent_unordered_map` admite reenviar sólo la iteración.

- Inserción no invalidan ni actualizar los iteradores devueltos por `equal_range`. Inserción puede anexar elementos iguales al final del intervalo. El iterador begin apunta a un elemento igual.

Para ayudar a evitar un interbloqueo, ningún método de `concurrent_unordered_map` mantiene un bloqueo cuando lo llama el asignador de memoria, las funciones hash u otro código definido por el usuario. Además, debe asegurarse de que la función hash siempre se evalúa como claves iguales en el mismo valor. Las funciones hash mejor distribuyen claves uniformemente en el espacio de código hash.

###  <a name="map-safety"></a> Operaciones seguras para simultaneidad

La `concurrent_unordered_map` clase permite las operaciones de inserción y el acceso a elementos seguras para simultaneidad. Las operaciones de inserción no invalidan existentes punteros o iteradores. Las operaciones de acceso y recorrido de iterador también son seguras para simultaneidad. En la tabla siguiente se muestra la frecuente `concurrent_unordered_map` métodos y operadores que son seguras para simultaneidad.

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|

Aunque el `count` método se puede llamar de forma segura de subprocesos en ejecución al mismo tiempo, distintos subprocesos pueden recibir resultados diferentes si simultáneamente se inserta un nuevo valor en el contenedor.

En la tabla siguiente se muestra los métodos utilizados con frecuencia y operadores que no son seguras para simultaneidad.

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq)

Además de estos métodos, cualquier método que comienza con `unsafe_` también no es segura para simultaneidad.

[[Arriba](#top)]

##  <a name="unordered_multimap"></a> concurrent_unordered_multimap (clase)

El [concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) se parezca la clase el `concurrent_unordered_map` excepto en que permite varios valores asignar a la misma clave de clase. También difiere de `concurrent_unordered_map` de las maneras siguientes:

- El [concurrent_unordered_multimap::insert](reference/concurrent-unordered-multimap-class.md#insert) método devuelve un iterador en lugar de `std::pair<iterator, bool>`.

- El `concurrent_unordered_multimap` no proporciona la clase `operator[]` ni `at` método.

El ejemplo siguiente muestra la estructura básica para el uso de `concurrent_unordered_multimap`. En este ejemplo inserta las teclas de carácter en el intervalo ['a', ' i']. `concurrent_unordered_multimap` permite que una clave a tener varios valores.

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[Arriba](#top)]

##  <a name="unordered_set"></a> concurrent_unordered_set (clase)

El [concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) se parezca la clase el `concurrent_unordered_map` clase salvo en que administra los valores en lugar de pares de clave y valor. El `concurrent_unordered_set` no proporciona la clase `operator[]` ni `at` método.

El ejemplo siguiente muestra la estructura básica para el uso de `concurrent_unordered_set`. En este ejemplo inserta los valores de caracteres en el intervalo ['a', ' i']. Es seguro realizar las inserciones en paralelo.

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[Arriba](#top)]

##  <a name="unordered_multiset"></a> concurrent_unordered_multiset (clase)

El [concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) se parezca la clase el `concurrent_unordered_set` clase excepto en que permite valores duplicados. También difiere de `concurrent_unordered_set` de las maneras siguientes:

- El [concurrent_unordered_multiset::insert](reference/concurrent-unordered-multiset-class.md#insert) método devuelve un iterador en lugar de `std::pair<iterator, bool>`.

- El `concurrent_unordered_multiset` no proporciona la clase `operator[]` ni `at` método.

El ejemplo siguiente muestra la estructura básica para el uso de `concurrent_unordered_multiset`. En este ejemplo inserta los valores de caracteres en el intervalo ['a', ' i']. `concurrent_unordered_multiset` permite un valor que se produzcan varias veces.

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[Arriba](#top)]

##  <a name="combinable"></a> combinable (clase)

El [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) clase proporciona almacenamiento local de subprocesos reutilizable que permite realizar cálculos específicos y, a continuación, fusionar mediante combinación estos cálculos en un resultado final. Puede pensar en un objeto `combinable` como una variable de reducción.

La `combinable` clase es útil si tiene un recurso que se comparte entre varios subprocesos o tareas. La `combinable` clase ayuda a eliminar el estado compartido, ya que proporciona acceso a los recursos compartidos de forma libre de bloqueo. Por lo tanto, esta clase proporciona una alternativa al uso de un mecanismo de sincronización, por ejemplo, una exclusión mutua, para sincronizar el acceso a los datos compartidos desde varios subprocesos.

###  <a name="combinable-features"></a> Los métodos y las características

En la tabla siguiente se muestra algunos de los métodos importantes de la `combinable` clase. Para obtener más información acerca de todos los `combinable` métodos de la clase, vea [combinable (clase)](../../parallel/concrt/reference/combinable-class.md).

|Método|Descripción|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|Recupera una referencia a la variable local que está asociada con el contexto del subproceso actual.|
|[clear](reference/combinable-class.md#clear)|Quita todas las variables locales del subproceso de la `combinable` objeto.|
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|Usa la función proporcionada se combinan para generar un valor final del conjunto de todos los cálculos locales del subproceso.|

El `combinable` es una clase de plantilla que se parametriza en el resultado combinado final. Si se llama al constructor predeterminado, el `T` tipo de parámetro de plantilla debe tener un constructor predeterminado y un constructor de copias. Si el `T` tipo de parámetro de plantilla no tiene un constructor predeterminado, llame a la versión sobrecargada del constructor que toma una función de inicialización como su parámetro.

Puede almacenar datos adicionales en un `combinable` objeto después de llamar a la [combinar](reference/combinable-class.md#combine) o [combine_each](reference/combinable-class.md#combine_each) métodos. También puede llamar a la `combine` y `combine_each` métodos varias veces. Si ningún valor local en un `combinable` objeto los cambios, el `combine` y `combine_each` métodos generan el mismo resultado cada vez que se les llama.

###  <a name="combinable-examples"></a> Ejemplos

Para obtener ejemplos sobre cómo usar el `combinable` de clases, vea los temas siguientes:

- [Cómo: Usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [Cómo: Usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[Arriba](#top)]

## <a name="related-topics"></a>Temas relacionados

[Cómo: Usar contenedores paralelos para aumentar la eficacia](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
Se muestra cómo usar contenedores paralelos para almacenar de forma eficaz y tener acceso a datos en paralelo.

[Cómo: Usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
Se muestra cómo usar el `combinable` clase para eliminar el estado compartido y mejorar el rendimiento.

[Cómo: Usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
Se muestra cómo usar un `combine` función para combinar conjuntos de datos locales de subproceso.

[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Describe la biblioteca PPL, que proporciona un modelo de programación imperativo que favorece la escalabilidad y facilidad de uso para desarrollar aplicaciones simultáneas.

## <a name="reference"></a>Referencia

[concurrent_vector (clase)](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue (clase)](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map (clase)](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap (clase)](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set (clase)](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset (clase)](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable (clase)](../../parallel/concrt/reference/combinable-class.md)
