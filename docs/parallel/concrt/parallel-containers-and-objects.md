---
title: "Contenedores y objetos paralelos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos paralelos"
  - "contenedores paralelos"
  - "contenedores simultáneos"
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores y objetos paralelos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La biblioteca de modelos paralelos (PPL) incluye varios contenedores y objetos que proporcionan acceso seguro para subprocesos a sus elementos.  
  
 Un *contenedor simultáneo* proporciona acceso seguro para simultaneidad a las operaciones más importantes. La funcionalidad de estos contenedores se parece a las proporcionadas por la biblioteca de plantillas estándar (STL). Por ejemplo, el [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) clase es similar a la [std:: vector](vector%20Class.md) clase, salvo que la `concurrent_vector` clase le permite anexar elementos en paralelo. Utilice contenedores simultáneos si cuenta con código paralelo que requiere acceso de lectura y escritura en el mismo contenedor.  
  
 Un *objeto simultáneo* se comparte simultáneamente entre los componentes. Un proceso que calcula el estado de un objeto simultáneo en paralelo genera el mismo resultado que otro proceso que calcula el mismo estado en serie. El [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) clase es un ejemplo de un tipo de objeto simultáneo. La `combinable` clase le permite realizar cálculos en paralelo y, a continuación, combinar estos cálculos en un resultado final. Utilice objetos simultáneos si usaría un mecanismo de sincronización, por ejemplo, una exclusión mutua, para sincronizar el acceso a una variable compartida o un recurso.  
  
##  <a name="a-nametopa-sections"></a><a name="top"></a> Secciones  
 En este tema se describe los siguientes contenedores paralelos y objetos de detalle.  
  
 Contenedores simultáneos:  
  
-   [Clase concurrent_vector](#vector)  
  
    -   [Diferencias entre concurrent_vector y vector](#vector-differences)  
  
    -   [Operaciones seguras para simultaneidad](#vector-safety)  
  
    -   [Seguridad de las excepciones](#vector-exceptions)  
  
-   [Clase concurrent_queue](#queue)  
  
    -   [Diferencias entre concurrent_queue y cola](#queue-differences)  
  
    -   [Operaciones seguras para simultaneidad](#queue-safety)  
  
    -   [Compatibilidad de iterador](#queue-iterators)  
  
-   [concurrent_unordered_map (clase)](#unordered_map)  
  
    -   [Unordered_map y las diferencias entre concurrent_unordered_map](#map-differences)  
  
    -   [Operaciones seguras para simultaneidad](#map-safety)  
  
-   [concurrent_unordered_multimap (clase)](#unordered_multimap)  
  
-   [concurrent_unordered_set (clase)](#unordered_set)  
  
-   [concurrent_unordered_multiset (clase)](#unordered_multiset)  
  
 Objetos simultáneos:  
  
-   [combinable (clase)](#combinable)  
  
    -   [Métodos y características](#combinable-features)  
  
    -   [Ejemplos](#combinable-examples)  
  
##  <a name="a-namevectora-concurrentvector-class"></a><a name="vector"></a> Clase concurrent_vector  
 El [Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) clase es una clase de contenedor de secuencia que, al igual que el [std:: vector](vector%20Class.md) clase, que permite el acceso de forma aleatoria a sus elementos. La `concurrent_vector` clase permite anexar seguro para simultaneidad y elemento de acceso a las operaciones. Anexar las operaciones no invalidan los iteradores ni punteros existentes. Operaciones de acceso y recorrido de iterador también son seguras para simultaneidad.  
  
###  <a name="a-namevector-differencesa-differences-between-concurrentvector-and-vector"></a><a name="vector-differences"></a> Diferencias entre concurrent_vector y vector  
 La `concurrent_vector` clase se parece mucho a la `vector` clase. La complejidad de anexar, el acceso a elementos y operaciones de acceso de iterador en una `concurrent_vector` objeto son los mismos que para un `vector` objeto. Los siguientes puntos muestran dónde `concurrent_vector` difiere de `vector`:  
  
-   Anexar, acceso de elemento, acceso de iterador y las operaciones de recorrido de iterador en una `concurrent_vector` objeto son seguras para simultaneidad.  
  
-   Puede agregar elementos al final de una `concurrent_vector` objeto. La `concurrent_vector` clase no proporciona el `insert` método.  
  
-   Un `concurrent_vector` no utiliza el objeto [semántica de transferencia](../../cpp/rvalue-reference-declarator-amp-amp.md) cuando se anexa a él.  
  
-   La `concurrent_vector` clase no proporciona el `erase` o `pop_back` métodos. Al igual que con `vector`, utilice el [Borrar](../Topic/concurrent_vector::clear%20Method.md) método para quitar todos los elementos de un `concurrent_vector` objeto.  
  
-   La `concurrent_vector` clase almacena sus elementos de forma contigua en la memoria. Por lo tanto, no puede utilizar el `concurrent_vector` clase en todas las formas en que puede usar una matriz. Por ejemplo, para una variable denominada `v` de tipo `concurrent_vector`, la expresión `&v[0]+2` produce un comportamiento indefinido.  
  
-   La `concurrent_vector` clase define la [grow_by](../Topic/concurrent_vector::grow_by%20Method.md) y [grow_to_at_least](../Topic/concurrent_vector::grow_to_at_least%20Method.md) métodos. Estos métodos son similares a los [cambiar el tamaño de](../Topic/concurrent_vector::resize%20Method.md) método, excepto en que son seguras para simultaneidad.  
  
-   Un `concurrent_vector` objeto no reubica sus elementos cuando se anexa a él o cambiar su tamaño. Esto permite punteros existentes e iteradores sigan siendo válidos durante las operaciones simultáneas.  
  
-   El tiempo de ejecución no define una versión especializada de `concurrent_vector` de tipo `bool`.  
  
###  <a name="a-namevector-safetya-concurrency-safe-operations"></a><a name="vector-safety"></a> Operaciones seguras para simultaneidad  
 Todos los métodos que anexar o aumentan el tamaño de una `concurrent_vector` de objeto o acceso a un elemento en un `concurrent_vector` de objetos, que son seguras para simultaneidad. La excepción a esta regla es la `resize` (método).  
  
 La siguiente tabla muestra los comunes `concurrent_vector` métodos y operadores que son seguras para simultaneidad.  
  
||||  
|-|-|-|  
|[en](../Topic/concurrent_vector::at%20Method.md)|[final](../Topic/concurrent_vector::end%20Method.md)|[operador &#91; &#93;](../Topic/concurrent_vector::operatorOperator.md)|  
|[comenzar](../Topic/concurrent_vector::begin%20Method.md)|[parte frontal](../Topic/concurrent_vector::front%20Method.md)|[push_back](../Topic/concurrent_vector::push_back%20Method.md)|  
|[Atrás](../Topic/concurrent_vector::back%20Method.md)|[grow_by](../Topic/concurrent_vector::grow_by%20Method.md)|[rbegin](../Topic/concurrent_vector::rbegin%20Method.md)|  
|[capacidad](../Topic/concurrent_vector::capacity%20Method.md)|[grow_to_at_least](../Topic/concurrent_vector::grow_to_at_least%20Method.md)|[rend](../Topic/concurrent_vector::rend%20Method.md)|  
|[vacía](../Topic/concurrent_vector::empty%20Method.md)|[max_size](../Topic/concurrent_vector::max_size%20Method.md)|[tamaño](../Topic/concurrent_vector::size%20Method.md)|  
  
 Las operaciones que el runtime proporciona para la compatibilidad con STL, por ejemplo, `reserve`, no son seguras para simultaneidad. En la tabla siguiente muestra los métodos y operadores que no son seguras para simultaneidad comunes.  
  
|||  
|-|-|  
|[asignar](../Topic/concurrent_vector::assign%20Method.md)|[reservar](../Topic/concurrent_vector::reserve%20Method.md)|  
|[Borrar](../Topic/concurrent_vector::clear%20Method.md)|[cambiar el tamaño](../Topic/concurrent_vector::resize%20Method.md)|  
|[operador =](../Topic/concurrent_vector::operator=%20Operator.md)|[shrink_to_fit](../Topic/concurrent_vector::shrink_to_fit%20Method.md)|  
  
 Las operaciones que modifican el valor de los elementos existentes no son seguras para simultaneidad. Usar un objeto de sincronización como un [reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objeto sincronizar simultáneas de lectura y escritura al mismo elemento de datos. Para obtener más información acerca de los objetos de sincronización, consulte [estructuras de datos de sincronización](../../parallel/concrt/synchronization-data-structures.md).  
  
 Al convertir código existente que utiliza `vector` usar `concurrent_vector`, operaciones simultáneas pueden hacer que el comportamiento de la aplicación para cambiar. Por ejemplo, considere el siguiente programa que realiza simultáneamente dos tareas en un `concurrent_vector` objeto. La primera tarea anexa los elementos adicionales a un `concurrent_vector` objeto. La segunda tarea calcula la suma de todos los elementos en el mismo objeto.  
  
 [!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_1.cpp)]  
  
 Aunque el `end` método es seguro para simultaneidad, una llamada simultánea activa a la [push_back](../Topic/concurrent_vector::push_back%20Method.md) método hace que el valor devuelto por `end` a cambiar. El número de elementos que recorre el iterador es indeterminado. Por lo tanto, este programa puede producir un resultado diferente cada vez que se ejecuta.  
  
###  <a name="a-namevector-exceptionsa-exception-safety"></a><a name="vector-exceptions"></a> Seguridad de las excepciones  
 Si una operación de crecimiento o de asignación produce una excepción, el estado de la `concurrent_vector` objeto deja de ser válido. El comportamiento de un `concurrent_vector` no está definido el objeto que se encuentra en un estado no válido a menos que se indique lo contrario. Sin embargo, el destructor siempre libera la memoria que asigna el objeto, incluso si el objeto está en un estado no válido.  
  
 El tipo de datos de los elementos de vector, `T`, debe cumplir los requisitos siguientes. De lo contrario, el comportamiento de la `concurrent_vector` clase es indefinida.  
  
-   No debe iniciar el destructor.  
  
-   Si se produce el constructor predeterminado o de copia, el destructor no se debe declarar utilizando la `virtual` (palabra clave) y deben trabajar correctamente con memoria inicializada en cero.  
  
 [[Arriba](#top)]  
  
##  <a name="a-namequeuea-concurrentqueue-class"></a><a name="queue"></a> Clase concurrent_queue  
 El [Concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) clase, igual que el [std:: Queue](../../standard-library/queue-class.md) clase, le permite obtener acceso a sus elementos anteriores y posteriores. La `concurrent_queue` clase habilita seguro para simultaneidad enqueue y dequeue operaciones. La `concurrent_queue` clase también proporciona compatibilidad de iterador que no es seguro para simultaneidad.  
  
###  <a name="a-namequeue-differencesa-differences-between-concurrentqueue-and-queue"></a><a name="queue-differences"></a> Diferencias entre concurrent_queue y cola  
 La `concurrent_queue` clase se parece mucho a la `queue` clase. Los siguientes puntos muestran dónde `concurrent_queue` difiere de `queue`:  
  
-   Enqueue y dequeue operaciones en un `concurrent_queue` objeto son seguras para simultaneidad.  
  
-   La `concurrent_queue` clase proporciona compatibilidad de iterador que no es seguro para simultaneidad.  
  
-   La `concurrent_queue` clase no proporciona el `front` o `pop` métodos. La `concurrent_queue` clase reemplaza estos métodos mediante la definición de la [try_pop](../Topic/concurrent_queue::try_pop%20Method.md) método.  
  
-   La `concurrent_queue` clase no proporciona el `back` método. Por lo tanto, no puede hacer referencia al final de la cola.  
  
-   La `concurrent_queue` clase proporciona el [unsafe_size](../Topic/concurrent_queue::unsafe_size%20Method.md) método en lugar de la `size` (método). El `unsafe_size` método no es seguro para simultaneidad.  
  
###  <a name="a-namequeue-safetya-concurrency-safe-operations"></a><a name="queue-safety"></a> Operaciones seguras para simultaneidad  
 Todos los métodos que ponen o quitan de la cola de un `concurrent_queue` objeto son seguras para simultaneidad.  
  
 La siguiente tabla muestra los comunes `concurrent_queue` métodos y operadores que son seguras para simultaneidad.  
  
|||  
|-|-|  
|[vacía](../Topic/concurrent_queue::empty%20Method.md)|[inserción](../Topic/concurrent_queue::push%20Method.md)|  
|[get_allocator](../Topic/concurrent_queue::get_allocator%20Method.md)|[try_pop](../Topic/concurrent_queue::try_pop%20Method.md)|  
  
 Aunque el `empty` método es seguro para simultaneidad, una operación simultánea puede hacer que la cola crezca o se reduzca antes de la `empty` devuelve del método.  
  
 En la tabla siguiente muestra los métodos y operadores que no son seguras para simultaneidad comunes.  
  
|||  
|-|-|  
|[Borrar](../Topic/concurrent_queue::clear%20Method.md)|[unsafe_end](../Topic/concurrent_queue::unsafe_end%20Method.md)|  
|[unsafe_begin](../Topic/concurrent_queue::unsafe_begin%20Method.md)|[unsafe_size](../Topic/concurrent_queue::unsafe_size%20Method.md)|  
  
###  <a name="a-namequeue-iteratorsa-iterator-support"></a><a name="queue-iterators"></a> Compatibilidad de iterador  
 El `concurrent_queue` proporciona iteradores que no son seguras para simultaneidad. Se recomienda usar estos iteradores únicamente para la depuración.  
  
 Un `concurrent_queue` iterador recorre los elementos de la dirección de avance. La siguiente tabla muestra a los operadores que cada iterador admite.  
  
|Operador|Descripción|  
|--------------|-----------------|  
|[operator ++](http://msdn.microsoft.com/es-es/4cfdd07e-927a-42f8-aaa0-d6881687f413)|Avanza al siguiente elemento de la cola. Este operador se sobrecarga para proporcionar semántica previa y posterior al incremento.|  
|[operador *](http://msdn.microsoft.com/es-es/a0e671fc-76e6-4fb4-b95c-ced4dd2b2017)|Recupera una referencia al elemento actual.|  
|[operator ->](http://msdn.microsoft.com/es-es/41fa393d-ae1e-4a38-bb4b-19e8df709ca9)|Recupera un puntero al elemento actual.|  
  
 [[Arriba](#top)]  
  
##  <a name="a-nameunorderedmapa-concurrentunorderedmap-class"></a><a name="unordered_map"></a> concurrent_unordered_map (clase)  
 El [HYPERLINK "file:///C:\\\Users\\\thompet\\\AppData\\\Local\\\Temp\\\DxEditor\\\DduePreview\\\Default\\\798d7037-df37-4310-858b-6f590bbf6ebf\\\HTM\\\html\\\a217b4ac-af2b-4d41-94eb-09a75ee28622" concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) es una clase de contenedor asociativo que, al igual que el [std:: unordered_map](../../standard-library/unordered-map-class.md) clase, que controla una secuencia de longitud variable de elementos de tipo [std:: Pair \< clave const, Ty >](../../standard-library/pair-structure.md). Considere una asignación no ordenada como un diccionario que puede agregar un par de clave y valor a o buscar un valor por clave. Esta clase es útil cuando tiene varios subprocesos o tareas que deben tener acceso a un contenedor compartido simultáneamente, insertar en él o actualizarlo.  
  
 En el ejemplo siguiente se muestra la estructura básica para el uso de `concurrent_unordered_map`. Este ejemplo inserta teclas de caracteres en el intervalo ['a', ' i']. Dado que el orden de operaciones es indeterminado, el valor final de cada clave también es indeterminado. Sin embargo, es seguro realizar las inserciones en paralelo.  
  
 [!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_2.cpp)]  
  
 Para obtener un ejemplo que utiliza `concurrent_unordered_map` para realizar una asignación y reducir la operación en paralelo, vea [Cómo: realizar la asignación y reducir las operaciones en paralelo](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).  
  
###  <a name="a-namemap-differencesa-differences-between-concurrentunorderedmap-and-unorderedmap"></a><a name="map-differences"></a> Unordered_map y las diferencias entre concurrent_unordered_map  
 La `concurrent_unordered_map` clase se parece mucho a la `unordered_map` clase. Los siguientes puntos muestran dónde `concurrent_unordered_map` difiere de `unordered_map`:  
  
-   El `erase`, `bucket`, `bucket_count`, y `bucket_size` se denominan métodos `unsafe_erase`, `unsafe_bucket`, `unsafe_bucket_count`, y `unsafe_bucket_size`, respectivamente. El `unsafe_` convención de nomenclatura indica que estos métodos no son seguras para simultaneidad. Para obtener más información acerca de la seguridad de simultaneidad, vea [operaciones seguras para simultaneidad](#map-safety).  
  
-   Las operaciones de inserción no invalidan los iteradores ni punteros existentes, ni cambian el orden de los elementos que ya existen en el mapa. Insertar y recorrer las operaciones pueden realizarse simultáneamente.  
  
-   `concurrent_unordered_map` admite reenviar sólo la iteración.  
  
-   Inserción no invalidan ni actualizar los iteradores devueltos por `equal_range`. Inserción puede anexar elementos iguales hasta el final del intervalo. El iterador begin apunta a un elemento igual.  
  
 Para evitar el interbloqueo, ningún método de `concurrent_unordered_map` mantiene un bloqueo cuando lo llama el asignador de memoria, las funciones hash u otro código definido por el usuario. Además, debe asegurarse de que la función hash siempre se evalúa como claves iguales en el mismo valor. Las mejores funciones de hash distribución las claves de manera uniforme en el espacio de código hash.  
  
###  <a name="a-namemap-safetya-concurrency-safe-operations"></a><a name="map-safety"></a> Operaciones seguras para simultaneidad  
 La `concurrent_unordered_map` clase permite operaciones de inserción y acceso a los elementos de seguro para simultaneidad. Las operaciones de inserción no invalidan los iteradores ni punteros existentes. Operaciones de acceso y recorrido de iterador también son seguras para simultaneidad. La siguiente tabla muestra el usado `concurrent_unordered_map` métodos y operadores que son seguras para simultaneidad.  
  
|||||  
|-|-|-|-|  
|[en](../Topic/concurrent_unordered_map::at%20Method.md)|`count`|`find`|[key_eq](../Topic/concurrent_unordered_map::key_eq%20Method.md)|  
|`begin`|`empty`|`get_allocator`|`max_size`|  
|`cbegin`|`end`|`hash_function`|[operador &#91; &#93;](../Topic/concurrent_unordered_map::operatorOperator.md)|  
|`cend`|`equal_range`|[Insertar](../Topic/concurrent_unordered_map::insert%20Method.md)|`size`|  
  
 Aunque el `count` método puede llamarse de forma segura de subprocesos en ejecución simultánea, distintos subprocesos pueden recibir resultados diferentes si simultáneamente se inserta un nuevo valor en el contenedor.  
  
 En la tabla siguiente muestra los métodos utilizados con frecuencia y operadores que no son seguras para simultaneidad.  
  
||||  
|-|-|-|  
|`clear`|`max_load_factor`|`rehash`|  
|`load_factor`|[operador =](../Topic/concurrent_unordered_map::operator=%20Operator.md)|[intercambio](../Topic/concurrent_unordered_map::swap%20Method.md)|  
  
 Además de estos métodos, cualquier método que comienza con `unsafe_` también no es seguro para simultaneidad.  
  
 [[Arriba](#top)]  
  
##  <a name="a-nameunorderedmultimapa-concurrentunorderedmultimap-class"></a><a name="unordered_multimap"></a> concurrent_unordered_multimap (clase)  
 El [concurrency::concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md) se parece mucho la clase la `concurrent_unordered_map` clase salvo que permite varios valores asignar a la misma clave. Difiere de `concurrent_unordered_map` de las maneras siguientes:  
  
-   El [concurrent_unordered_multimap:: Insert](../Topic/concurrent_unordered_multimap::insert%20Method.md) método devuelve un iterador en lugar de `std::pair<iterator, bool>`.  
  
-   La `concurrent_unordered_multimap` clase no proporciona `operator[]` ni `at` método.  
  
 En el ejemplo siguiente se muestra la estructura básica para el uso de `concurrent_unordered_multimap`. Este ejemplo inserta teclas de caracteres en el intervalo ['a', ' i']. `concurrent_unordered_multimap` permite una clave para tener varios valores.  
  
 [!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_3.cpp)]  
  
 [[Arriba](#top)]  
  
##  <a name="a-nameunorderedseta-concurrentunorderedset-class"></a><a name="unordered_set"></a> concurrent_unordered_set (clase)  
 El [concurrency::concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md) se parece mucho la clase la `concurrent_unordered_map` clase salvo en que administra valores en lugar de pares de clave y valor. La `concurrent_unordered_set` clase no proporciona `operator[]` ni `at` método.  
  
 En el ejemplo siguiente se muestra la estructura básica para el uso de `concurrent_unordered_set`. Este ejemplo inserta los valores de caracteres en el intervalo ['a', ' i']. Es seguro realizar las inserciones en paralelo.  
  
 [!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_4.cpp)]  
  
 [[Arriba](#top)]  
  
##  <a name="a-nameunorderedmultiseta-concurrentunorderedmultiset-class"></a><a name="unordered_multiset"></a> concurrent_unordered_multiset (clase)  
 El [concurrency::concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md) se parece mucho la clase la `concurrent_unordered_set` clase salvo que permite valores duplicados. Difiere de `concurrent_unordered_set` de las maneras siguientes:  
  
-   El [concurrent_unordered_multiset:: Insert](../Topic/concurrent_unordered_multiset::insert%20Method.md) método devuelve un iterador en lugar de `std::pair<iterator, bool>`.  
  
-   La `concurrent_unordered_multiset` clase no proporciona `operator[]` ni `at` método.  
  
 En el ejemplo siguiente se muestra la estructura básica para el uso de `concurrent_unordered_multiset`. Este ejemplo inserta los valores de caracteres en el intervalo ['a', ' i']. `concurrent_unordered_multiset` permite un valor aparezca varias veces.  
  
 [!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/CPP/parallel-containers-and-objects_5.cpp)]  
  
 [[Arriba](#top)]  
  
##  <a name="a-namecombinablea-combinable-class"></a><a name="combinable"></a> combinable (clase)  
 El [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) clase proporciona almacenamiento local de subprocesos reutilizable que permite realizar cálculos específicos y, a continuación, combinar estos cálculos en un resultado final. Puede pensar en un objeto `combinable` como una variable de reducción.  
  
 La `combinable` clase es útil si tiene un recurso que se comparte entre varios subprocesos o tareas. La `combinable` clase le ayuda a eliminar el estado compartido al proporcionar acceso a los recursos compartidos de forma libre de bloqueo. Por lo tanto, esta clase proporciona una alternativa al uso de un mecanismo de sincronización, por ejemplo, una exclusión mutua, para sincronizar el acceso a los datos compartidos desde varios subprocesos.  
  
###  <a name="a-namecombinable-featuresa-methods-and-features"></a><a name="combinable-features"></a> Métodos y características  
 La siguiente tabla muestra algunos de los métodos importantes de la `combinable` clase. Para obtener más información acerca de todos los `combinable` métodos de la clase, vea [combinable (clase)](../../parallel/concrt/reference/combinable-class.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[local](../Topic/combinable::local%20Method.md)|Recupera una referencia a la variable local que está asociada con el contexto del subproceso actual.|  
|[Borrar](../Topic/combinable::clear%20Method.md)|Quita todas las variables locales del subproceso de la `combinable` objeto.|  
|[combinar](../Topic/combinable::combine%20Method.md)<br /><br /> [combine_each](../Topic/combinable::combine_each%20Method.md)|Utiliza la función combine proporcionada para generar un valor final del conjunto de todos los cálculos locales de subproceso.|  
  
 El `combinable` es una clase de plantilla que se parametriza en el resultado final combinado. Si se llama al constructor predeterminado, la `T` tipo de parámetro de plantilla debe tener un constructor predeterminado y un constructor de copias. Si el `T` tipo de parámetro de plantilla no tiene un constructor predeterminado, llame a la versión sobrecargada del constructor que toma una función de inicialización como su parámetro.  
  
 Puede almacenar datos adicionales en un `combinable` objeto después de llamar a la [combinar](../Topic/combinable::combine%20Method.md) o [combine_each](../Topic/combinable::combine_each%20Method.md) métodos. También puede llamar a la `combine` y `combine_each` métodos varias veces. Si ningún valor local en un `combinable` objeto los cambios, el `combine` y `combine_each` métodos producen el mismo resultado cada vez que se les llama.  
  
###  <a name="a-namecombinable-examplesa-examples"></a><a name="combinable-examples"></a> Ejemplos  
 Para obtener ejemplos sobre cómo utilizar el `combinable` de clases, vea los temas siguientes:  
  
-   [Cómo: usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
  
-   [Cómo: usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
  
 [[Arriba](#top)]  
  
## <a name="related-topics"></a>Temas relacionados  
 [Cómo: usar contenedores paralelos para aumentar la eficacia](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)  
 Muestra cómo se usan contenedores paralelos para almacenar de forma eficaz y tener acceso a datos en paralelo.  
  
 [Cómo: usar la clase combinable para mejorar el rendimiento](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)  
 Muestra cómo utilizar el `combinable` clase para eliminar el estado compartido y mejorar el rendimiento.  
  
 [Cómo: usar la clase combinable para combinar conjuntos](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)  
 Muestra cómo utilizar un `combine` función para combinar conjuntos de datos locales de subproceso.  
  
 [Biblioteca de modelos paralelos (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)  
 Describe la biblioteca PPL, que proporciona un modelo de programación imperativo que favorece la escalabilidad y facilidad de uso para desarrollar aplicaciones simultáneas.  
  
## <a name="reference"></a>Referencia  
 [Clase concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)  
  
 [Clase concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)  
  
 [concurrent_unordered_map (clase)](../../parallel/concrt/reference/concurrent-unordered-map-class.md)  
  
 [concurrent_unordered_multimap (clase)](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)  
  
 [concurrent_unordered_set (clase)](../../parallel/concrt/reference/concurrent-unordered-set-class.md)  
  
 [concurrent_unordered_multiset (clase)](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)  
  
 [combinable (clase)](../../parallel/concrt/reference/combinable-class.md)
