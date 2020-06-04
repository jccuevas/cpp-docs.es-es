---
title: Algoritmos paralelos
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: a31787172c89e23e5eb32aa203b9f541584c0f68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363202"
---
# <a name="parallel-algorithms"></a>Algoritmos paralelos

La biblioteca de patrones paralelos (PPL) proporciona algoritmos que realizan simultáneamente el trabajo en colecciones de datos. Estos algoritmos se asemejan a los proporcionados por la biblioteca estándar C++.

Los algoritmos paralelos se componen de la funcionalidad existente en el Runtime de simultaneidad. Por ejemplo, el algoritmo [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) utiliza un objeto [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) para realizar las iteraciones de bucle paralelo. Las `parallel_for` particiones de algoritmo funcionan de manera óptima dado el número disponible de recursos informáticos.

## <a name="sections"></a><a name="top"></a>Secciones

- [El algoritmo parallel_for](#parallel_for)

- [El algoritmo parallel_for_each](#parallel_for_each)

- [El algoritmo parallel_invoke](#parallel_invoke)

- [Los algoritmos parallel_transform y parallel_reduce](#parallel_transform_reduce)

  - [El algoritmo parallel_transform](#parallel_transform)

  - [El algoritmo parallel_reduce](#parallel_reduce)

  - [Ejemplo: realizar una asignación y una reducción en paralelo](#map_reduce_example)

- [Repartir el trabajo](#partitions)

- [Ordenación paralela](#parallel_sorting)

  - [Elegir un algoritmo de ordenación](#choose_sort)

## <a name="the-parallel_for-algorithm"></a><a name="parallel_for"></a>El algoritmo parallel_for

El algoritmo [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) realiza repetidamente la misma tarea en paralelo. Cada una de estas tareas se parametriza mediante un valor de iteración. Este algoritmo es útil cuando tiene un cuerpo de bucle que no comparte recursos entre iteraciones de ese bucle.

El `parallel_for` algoritmo particiona las tareas de una manera óptima para la ejecución en paralelo. Utiliza un algoritmo de robo de trabajo y el robo de rango para equilibrar estas particiones cuando las cargas de trabajo están desequilibradas. Cuando una iteración de bucle se bloquea de forma cooperativa, el tiempo de ejecución redistribuye el intervalo de iteraciones que se asigna al subproceso actual a otros subprocesos o procesadores. De forma similar, cuando un subproceso completa un intervalo de iteraciones, el tiempo de ejecución redistribuye el trabajo de otros subprocesos a ese subproceso. El `parallel_for` algoritmo también admite *el paralelismo anidado.* Cuando un bucle paralelo contiene otro bucle paralelo, el tiempo de ejecución coordina los recursos de procesamiento entre los cuerpos del bucle de una manera eficaz para la ejecución en paralelo.

El `parallel_for` algoritmo tiene varias versiones sobrecargadas. La primera versión toma un valor inicial, un valor final y una función de trabajo (una expresión lambda, un objeto de función o un puntero de función). La segunda versión toma un valor inicial, un valor final, un valor por el que se va a paso y una función de trabajo. La primera versión de esta función utiliza 1 como valor de paso. Las versiones restantes toman objetos de `parallel_for` particionador, lo que le permite especificar cómo deben los intervalos de particiones entre subprocesos. Los particionadores se explican con mayor detalle en la sección Trabajo de [partición](#partitions) en este documento.

Puede convertir `for` muchos bucles `parallel_for`para utilizar . Sin `parallel_for` embargo, el `for` algoritmo difiere de la instrucción de las siguientes maneras:

- El `parallel_for` `parallel_for` algoritmo no ejecuta las tareas en un orden predeterminado.

- El `parallel_for` algoritmo no admite condiciones de terminación arbitrarias. El `parallel_for` algoritmo se detiene cuando el valor `last`actual de la variable de iteración es uno menor que .

- El `_Index_type` parámetro type debe ser un tipo entero. Este tipo entero se puede firmar o sin firmar.

- La iteración del bucle debe ser directa. El `parallel_for` algoritmo produce una excepción de tipo [std::invalid_argument](../../standard-library/invalid-argument-class.md) si el `_Step` parámetro es menor que 1.

- El mecanismo de control `parallel_for` de excepciones para `for` el algoritmo difiere del de un bucle. Si se producen varias excepciones simultáneamente en un cuerpo de bucle paralelo, `parallel_for`el tiempo de ejecución propaga solo una de las excepciones al subproceso que llamó a . Además, cuando una iteración de bucle produce una excepción, el tiempo de ejecución no detiene inmediatamente el bucle general. En su lugar, el bucle se coloca en el estado cancelado y el tiempo de ejecución descarta las tareas que aún no se han iniciado. Para obtener más información sobre el control de excepciones y los algoritmos paralelos, vea Control de [excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Aunque `parallel_for` el algoritmo no admite condiciones de terminación arbitrarias, puede usar la cancelación para detener todas las tareas. Para obtener más información acerca de la cancelación, consulte [Cancelación en la PPL](cancellation-in-the-ppl.md).

> [!NOTE]
> El costo de programación que resulta del equilibrio de carga y la compatibilidad con características como la cancelación podría no superar las ventajas de ejecutar el cuerpo del bucle en paralelo, especialmente cuando el cuerpo del bucle es relativamente pequeño. Puede minimizar esta sobrecarga mediante un particionador en el bucle paralelo. Para obtener más información, consulte Trabajo de [particionamiento](#partitions) más adelante en este documento.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `parallel_for` muestra la estructura básica del algoritmo. Este ejemplo imprime en la consola cada valor del intervalo [1, 5] en paralelo.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
1 2 4 3 5
```

Dado `parallel_for` que el algoritmo actúa en cada elemento en paralelo, el orden en que se imprimen los valores en la consola variará.

Para obtener un ejemplo `parallel_for` completo que utiliza el algoritmo, vea [Cómo: escribir un bucle de parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Superior](#top)]

## <a name="the-parallel_for_each-algorithm"></a><a name="parallel_for_each"></a>El algoritmo parallel_for_each

El algoritmo [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) realiza tareas en un contenedor iterativo, como las proporcionadas por la biblioteca estándar C++, en paralelo. Usa la misma lógica de creación de particiones que el algoritmo `parallel_for`.

El `parallel_for_each` algoritmo se asemeja al algoritmo [std::for_each](../../standard-library/algorithm-functions.md#for_each) de `parallel_for_each` la biblioteca estándar C+++, excepto que el algoritmo ejecuta las tareas simultáneamente. Al igual que `parallel_for_each` otros algoritmos paralelos, no ejecuta las tareas en un orden específico.

Aunque `parallel_for_each` el algoritmo funciona tanto en iteradores de avance como en iteradores de acceso aleatorio, funciona mejor con los iteradores de acceso aleatorio.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `parallel_for_each` muestra la estructura básica del algoritmo. En este ejemplo se imprime en la consola cada valor de un objeto [std::array](../../standard-library/array-class-stl.md) en paralelo.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
4 5 1 2 3
```

Dado `parallel_for_each` que el algoritmo actúa en cada elemento en paralelo, el orden en que se imprimen los valores en la consola variará.

Para obtener un ejemplo `parallel_for_each` completo que utiliza el algoritmo, vea [Cómo: escribir un bucle de parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Superior](#top)]

## <a name="the-parallel_invoke-algorithm"></a><a name="parallel_invoke"></a>El algoritmo parallel_invoke

El algoritmo [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) ejecuta un conjunto de tareas en paralelo. No se devuelve hasta que finaliza cada tarea. Este algoritmo es útil cuando tiene varias tareas independientes que desea ejecutar al mismo tiempo.

El `parallel_invoke` algoritmo toma como parámetros una serie de funciones de trabajo (funciones lambda, objetos de función o punteros de función). El `parallel_invoke` algoritmo está sobrecargado para tomar entre dos y diez parámetros. Cada función a `parallel_invoke` la que pase debe tomar cero parámetros.

Al igual que `parallel_invoke` otros algoritmos paralelos, no ejecuta las tareas en un orden específico. En el tema [Paralelismo](../../parallel/concrt/task-parallelism-concurrency-runtime.md) de tareas se explica cómo se relaciona el `parallel_invoke` algoritmo con las tareas y los grupos de tareas.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se `parallel_invoke` muestra la estructura básica del algoritmo. Este ejemplo llama `twice` simultáneamente a la función en tres variables locales e imprime el resultado en la consola.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
108 11.2 HelloHello
```

Para obtener ejemplos `parallel_invoke` completos que utilizan el algoritmo, vea [Cómo: usar parallel_invoke para escribir una rutina](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) de ordenación paralela y [Cómo: usar parallel_invoke para ejecutar operaciones paralelas](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Superior](#top)]

## <a name="the-parallel_transform-and-parallel_reduce-algorithms"></a><a name="parallel_transform_reduce"></a>Los algoritmos parallel_transform y parallel_reduce

Los algoritmos [concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) y [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) son versiones paralelas de los algoritmos de biblioteca estándar [c++ std::transform](../../standard-library/algorithm-functions.md#transform) y [std::accumulate](../../standard-library/numeric-functions.md#accumulate), respectivamente. Las versiones de Runtime de simultaneidad se comportan como las versiones de la biblioteca estándar de C++, excepto que el orden de operación no se determina porque se ejecutan en paralelo. Utilice estos algoritmos cuando trabaje con un conjunto que sea lo suficientemente grande como para obtener beneficios de rendimiento y escalabilidad al procesarse en paralelo.

> [!IMPORTANT]
> Los `parallel_transform` `parallel_reduce` algoritmos y solo admiten iteradores de acceso aleatorio, bidireccionales y directos porque estos iteradores producen direcciones de memoria estables. Además, estos iteradores deben producir valores no`const` L.

### <a name="the-parallel_transform-algorithm"></a><a name="parallel_transform"></a>El algoritmo de parallel_transform

Puede utilizar `parallel transform` el algoritmo para realizar muchas operaciones de paralelización de datos. Por ejemplo, puede:

- Ajuste el brillo de una imagen y realice otras operaciones de procesamiento de imágenes.

- Sume o tome el producto de punto entre dos vectores y realice otros cálculos numéricos en vectores.

- Realice el seguimiento de rayos 3D, donde cada iteración hace referencia a un píxel que se debe representar.

En el ejemplo siguiente se muestra la `parallel_transform` estructura básica que se utiliza para llamar al algoritmo. Este ejemplo niega cada elemento de un objeto[vectorial](../../standard-library/vector-class.md) std:: de dos maneras. La primera forma utiliza una expresión lambda. La segunda forma utiliza [std::negate](../../standard-library/negate-struct.md), que deriva de [std::unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> En este ejemplo se `parallel_transform`muestra el uso básico de . Dado que la función de trabajo no realiza una cantidad significativa de trabajo, no se espera un aumento significativo en el rendimiento en este ejemplo.

El `parallel_transform` algoritmo tiene dos sobrecargas. La primera sobrecarga toma un rango de entrada y una función unaria. La función unaria puede ser una expresión lambda que toma un argumento, un objeto de función o un tipo que deriva de `unary_function`. La segunda sobrecarga toma dos rangos de entrada y una función binaria. La función binaria puede ser una expresión lambda que toma dos argumentos, un objeto de función o un tipo que deriva de [std::binary_function](../../standard-library/binary-function-struct.md). En el ejemplo siguiente se ilustran estas diferencias.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> El iterador que proporcione `parallel_transform` para la salida de debe superponerse completamente el iterador de entrada o no superponerse en absoluto. El comportamiento de este algoritmo no se especifica si los iteradores de entrada y salida se superponen parcialmente.

### <a name="the-parallel_reduce-algorithm"></a><a name="parallel_reduce"></a>El algoritmo parallel_reduce

El `parallel_reduce` algoritmo es útil cuando tiene una secuencia de operaciones que satisfacen la propiedad asociativa. (Este algoritmo no requiere la propiedad conmutativa.) Estas son algunas de las `parallel_reduce`operaciones que puede realizar con:

- Multiplique secuencias de matrices para producir una matriz.

- Multiplique un vector por una secuencia de matrices para producir un vector.

- Calcular la longitud de una secuencia de cadenas.

- Combine una lista de elementos, como cadenas, en un elemento.

En el siguiente ejemplo básico `parallel_reduce` se muestra cómo utilizar el algoritmo para combinar una secuencia de cadenas en una cadena. Al igual que `parallel_transform`con los ejemplos de , no se esperan mejoras de rendimiento en este ejemplo básico.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

En muchos casos, puede `parallel_reduce` pensar como abreviatura para `parallel_for_each` el uso del algoritmo junto con la clase [concurrency::combinable.](../../parallel/concrt/reference/combinable-class.md)

### <a name="example-performing-map-and-reduce-in-parallel"></a><a name="map_reduce_example"></a>Ejemplo: Realizar mapas y reducir en paralelo

Una operación de *mapa* aplica una función a cada valor de una secuencia. Una operación de *reducción* combina los elementos de una secuencia en un valor. Puede utilizar las funciones C++ Standard Library [std::transform](../../standard-library/algorithm-functions.md#transform) y [std::accumulate](../../standard-library/numeric-functions.md#accumulate) para realizar operaciones de asignación y reducción. Sin embargo, para muchos `parallel_transform` problemas, puede utilizar el algoritmo `parallel_reduce` para realizar la operación de mapa en paralelo y el algoritmo realizar la operación de reducción en paralelo.

En el ejemplo siguiente se compara el tiempo que se tarda en calcular la suma de los números primos en serie y en paralelo. La fase de mapa transforma los valores no primos en 0 y la fase de reducción suma los valores.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Para obtener otro ejemplo que realiza una operación de asignación y reducción en paralelo, vea [Cómo: realizar operaciones de asignación y reducción en paralelo](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Superior](#top)]

## <a name="partitioning-work"></a><a name="partitions"></a>Trabajo de partición

Para paralelizar una operación en un origen de datos, un paso esencial es *dividir* el origen en varias secciones a las que se puede tener acceso simultáneamente por varios subprocesos. Un particionador especifica cómo un algoritmo paralelo debe particionar intervalos entre subprocesos. Como se explicó anteriormente en este documento, la PPL utiliza un mecanismo de particionamiento predeterminado que crea una carga de trabajo inicial y, a continuación, utiliza un algoritmo de robo de trabajo y el robo de rango para equilibrar estas particiones cuando las cargas de trabajo están desequilibradas. Por ejemplo, cuando una iteración de bucle completa un intervalo de iteraciones, el tiempo de ejecución redistribuye el trabajo de otros subprocesos a ese subproceso. Sin embargo, para algunos escenarios, es posible que desee especificar un mecanismo de partición diferente que se adapte mejor a su problema.

Los `parallel_for` `parallel_for_each`algoritmos `parallel_transform` , , y proporcionan versiones `_Partitioner`sobrecargadas que toman un parámetro adicional, . Este parámetro define el tipo de particionador que divide el trabajo. Estos son los tipos de particionadores que la PPL define:

[concurrency::affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Divide el trabajo en un número fijo de intervalos (normalmente el número de subprocesos de trabajo que están disponibles para trabajar en el bucle). Este tipo de `static_partitioner`particionador se asemeja a , pero mejora la afinidad de caché por la forma en que asigna intervalos a subprocesos de trabajo. Este tipo de particionador puede mejorar el rendimiento cuando se ejecuta un bucle sobre el mismo conjunto de datos varias veces (por ejemplo, un bucle dentro de un bucle) y los datos se ajustan a la memoria caché. Este particionador no participa completamente en la cancelación. Tampoco utiliza la semántica de bloqueo cooperativo y, por lo tanto, no se puede utilizar con bucles paralelos que tienen una dependencia directa.

[concurrency::auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Divide el trabajo en un número inicial de intervalos (normalmente el número de subprocesos de trabajo que están disponibles para trabajar en el bucle). El tiempo de ejecución utiliza este tipo de forma predeterminada `_Partitioner` cuando no se llama a un algoritmo paralelo sobrecargado que toma un parámetro. Cada rango se puede dividir en subintervalos y, por lo lo que, permite que se produzca el equilibrio de carga. Cuando se completa un intervalo de trabajo, el tiempo de ejecución redistribuye subintervalos de trabajo de otros subprocesos a ese subproceso. Utilice este particionador si la carga de trabajo no está comprendida en una de las otras categorías o si necesita soporte completo para la cancelación o el bloqueo cooperativo.

[concurrency::simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Las divisiones funcionan en rangos de tal forma que cada intervalo tenga al menos el número de iteraciones especificadas por el tamaño de fragmento especificado. Este tipo de particionador participa en el equilibrio de carga; sin embargo, el tiempo de ejecución no divide los intervalos en subintervalos. Para cada trabajador, el tiempo de ejecución comprueba la `_Chunk_size` cancelación y realiza el equilibrio de carga una vez completadas las iteraciones.

[concurrency::static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Divide el trabajo en un número fijo de intervalos (normalmente el número de subprocesos de trabajo que están disponibles para trabajar en el bucle). Este tipo de particionador puede mejorar el rendimiento porque no utiliza el robo de trabajo y, por lo tanto, tiene menos sobrecarga. Utilice este tipo de particionador cuando cada iteración de un bucle paralelo realice una cantidad fija y uniforme de trabajo y no necesite compatibilidad con la cancelación o el bloqueo cooperativo de reenvío.

> [!WARNING]
> Los `parallel_for_each` `parallel_transform` algoritmos y solo admiten contenedores que utilizan iteradores de acceso aleatorio (como std::[vector](../../standard-library/vector-class.md)) para los particionadores estáticos, simples y de afinidad. El uso de contenedores que utilizan iteradores bidireccionales y de reenvío produce un error en tiempo de compilación. El particionador `auto_partitioner`predeterminado, , admite los tres tipos de iterador.

Normalmente, estos particionadores se utilizan de `affinity_partitioner`la misma manera, excepto para . La mayoría de los tipos de particionador no mantienen el estado y el tiempo de ejecución no los modifica. Por lo tanto, puede crear estos objetos de particionador en el sitio de llamada, como se muestra en el ejemplo siguiente.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Sin embargo, `affinity_partitioner` debe pasar un`const`objeto como una referencia de valor l que no sea de , para que el algoritmo pueda almacenar el estado de los bucles futuros para que se reutilicen. En el ejemplo siguiente se muestra una aplicación básica que realiza la misma operación en un conjunto de datos en paralelo varias veces. El uso `affinity_partitioner` de puede mejorar el rendimiento porque es probable que la matriz se ajuste a la memoria caché.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> Tenga cuidado al modificar el código existente que se `static_partitioner` `affinity_partitioner`basa en la semántica de bloqueo cooperativo que se va a usar o . Estos tipos de particionador no utilizan el equilibrio de carga o el robo de rango y, por lo tanto, pueden alterar el comportamiento de la aplicación.

La mejor manera de determinar si se debe usar un particionador en un escenario determinado es experimentar y medir cuánto tiempo tardan las operaciones en completarse en cargas representativas y configuraciones de equipo. Por ejemplo, el particionamiento estático podría proporcionar un aumento significativo de la velocidad en un equipo de varios núcleos que tenga solo unos pocos núcleos, pero podría dar como resultado una ralentización de los equipos que tienen relativamente muchos núcleos.

[[Superior](#top)]

## <a name="parallel-sorting"></a><a name="parallel_sorting"></a>Clasificación paralela

La PPL proporciona tres algoritmos de ordenación: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)y [concurrency::parallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Estos algoritmos de ordenación son útiles cuando tiene un conjunto de datos que puede beneficiarse de la ordenación en paralelo. En particular, ordenar en paralelo es útil cuando se tiene un conjunto de datos grande o cuando se utiliza una operación de comparación costosa desde el momento para ordenar los datos. Cada uno de estos algoritmos ordena los elementos en su lugar.

Los `parallel_sort` `parallel_buffered_sort` algoritmos y los son algoritmos basados en comparación. Es decir, comparan elementos por valor. El `parallel_sort` algoritmo no tiene requisitos de memoria adicionales y es adecuado para la clasificación de uso general. El `parallel_buffered_sort` algoritmo puede `parallel_sort`funcionar mejor que , pero requiere espacio O(N).

El `parallel_radixsort` algoritmo está basado en hash. Es decir, utiliza claves enteras para ordenar los elementos. Mediante el uso de claves, este algoritmo puede calcular directamente el destino de un elemento en lugar de usar comparaciones. Al `parallel_buffered_sort`igual que , este algoritmo requiere espacio O(N).

En la tabla siguiente se resumen las propiedades importantes de los tres algoritmos de ordenación paralelos.

|Algoritmo|Descripción|Mecanismo de clasificación|Ordenar la estabilidad|Requisitos de memoria|Complejidad del tiempo|Acceso al iterador|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Ordenación basada en comparación de propósito general.|Basado en comparación (ascendente)|Inestable|None|O((N/P)log(N/P) + 2N((P-1)/P))|Random|
|`parallel_buffered_sort`|Ordenación basada en comparación de propósito general más rápida que requiere espacio O(N).|Basado en comparación (ascendente)|Inestable|Requiere espacio Adicional O(N)|O((N/P)log(N))|Random|
|`parallel_radixsort`|Ordenación basada en claves enteras que requiere espacio O(N).|Basado en hash|Stable|Requiere espacio Adicional O(N)|O(N/P)|Random|

La siguiente ilustración muestra las propiedades importantes de los tres algoritmos de ordenación paralelos de forma más gráfica.

![Comparación de los algoritmos de ordenación](../../parallel/concrt/media/concrt_parallel_sorting.png "Comparación de los algoritmos de ordenación")

Estos algoritmos de ordenación paralelos siguen las reglas de cancelación y control de excepciones. Para obtener más información acerca de la cancelación y el control de excepciones en el Runtime de simultaneidad, vea [Cancelar algoritmos paralelos](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) y control de [excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
> Estos algoritmos de ordenación paralelos admiten la semántica de movimiento. Puede definir un operador de asignación de movimiento para permitir que las operaciones de intercambio se realicen de forma más eficaz. Para obtener más información acerca de la semántica de movimiento y el operador de asignación de movimiento, vea Declarador de referencia de [valor R: &&](../../cpp/rvalue-reference-declarator-amp-amp.md)y [Mover constructores y mover operadores de asignación (C++).](../../cpp/move-constructors-and-move-assignment-operators-cpp.md) Si no proporciona un operador de asignación de movimiento o una función de intercambio, los algoritmos de ordenación utilizan el constructor de copia.

En el siguiente ejemplo `parallel_sort` básico se `vector` `int` muestra cómo utilizar para ordenar un de valores. De forma `parallel_sort` predeterminada, utiliza [std::less](../../standard-library/less-struct.md) para comparar valores.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

En este ejemplo se muestra cómo proporcionar una función de comparación personalizada. Utiliza el método [std::complex::real](../../standard-library/complex-class.md#real) para ordenar los valores [de doble>std::complex\<en](../../standard-library/complex-double.md) orden ascendente.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

En este ejemplo se muestra cómo `parallel_radixsort` proporcionar una función hash al algoritmo. En este ejemplo se ordenan los puntos 3D. Los puntos se ordenan en función de su distancia desde un punto de referencia.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

A modo de ejemplo, en este ejemplo se utiliza un conjunto de datos relativamente pequeño. Puede aumentar el tamaño inicial del vector para experimentar con mejoras de rendimiento en conjuntos de datos más grandes.

En este ejemplo se utiliza una expresión lambda como función hash. También puede utilizar una de las implementaciones integradas de la[clase hash](../../standard-library/hash-class.md) std:: o definir su propia especialización. También puede utilizar un objeto de función hash personalizado, como se muestra en este ejemplo:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

La función hash debe devolver un tipo entero ([std:is_integral::value](../../standard-library/is-integral-class.md) debe ser **true**). Este tipo entero debe `size_t`ser convertible al tipo .

### <a name="choosing-a-sorting-algorithm"></a><a name="choose_sort"></a>Elegir un algoritmo de clasificación

En muchos `parallel_sort` casos, proporciona el mejor equilibrio entre velocidad y rendimiento de memoria. Sin embargo, a medida que aumenta el tamaño del conjunto de datos, `parallel_buffered_sort` el `parallel_radixsort` número de procesadores disponibles o la complejidad de la función de comparación, o puede funcionar mejor. La mejor manera de determinar qué algoritmo de ordenación usar en un escenario determinado es experimentar y medir cuánto tiempo se tarda en ordenar los datos típicos en configuraciones de equipo representativas. Tenga en cuenta las siguientes directrices al elegir una estrategia de clasificación.

- El tamaño del conjunto de datos. En este documento, un conjunto de datos *pequeño* contiene menos de 1.000 elementos, un conjunto de datos *medio* contiene entre 10.000 y 100.000 elementos y un conjunto de datos *grande* contiene más de 100.000 elementos.

- La cantidad de trabajo que realiza la función de comparación o la función hash.

- La cantidad de recursos informáticos disponibles.

- Las características del conjunto de datos. Por ejemplo, un algoritmo podría funcionar bien para los datos que ya están casi ordenados, pero no tan bien para los datos que no están completamente ordenados.

- El tamaño del trozo. El `_Chunk_size` argumento opcional especifica cuándo el algoritmo cambia de una implementación de ordenación paralela a una serie a medida que subdivide la ordenación general en unidades de trabajo más pequeñas. Por ejemplo, si proporciona 512, el algoritmo cambia a la implementación en serie cuando una unidad de trabajo contiene 512 o menos elementos. Una implementación en serie puede mejorar el rendimiento general porque elimina la sobrecarga necesaria para procesar datos en paralelo.

Puede que no valga la pena ordenar un conjunto de datos pequeño en paralelo, incluso cuando tiene un gran número de recursos informáticos disponibles o la función de comparación o función hash realiza una cantidad relativamente grande de trabajo. Puede utilizar la función [std::sort](../../standard-library/algorithm-functions.md#sort) para ordenar conjuntos de datos pequeños. (`parallel_sort` `parallel_buffered_sort` y `sort` llamar cuando se especifica un tamaño de `parallel_buffered_sort` fragmento que es mayor que el conjunto de datos; sin embargo, tendría que asignar espacio O(N), que podría tardar más tiempo debido a la contención de bloqueo o la asignación de memoria.)

Si debe conservar la memoria o el asignador de `parallel_sort` memoria está sujeto a contención de bloqueo, utilícelo para ordenar un conjunto de datos de tamaño mediano. `parallel_sort`no requiere espacio adicional; los otros algoritmos requieren espacio O(N).

Se `parallel_buffered_sort` utiliza para ordenar conjuntos de datos de tamaño medio y cuando la aplicación cumple el requisito de espacio O(N) adicional. `parallel_buffered_sort`puede ser especialmente útil cuando tiene un gran número de recursos informáticos o una función de comparación costosa o una función hash.

Se `parallel_radixsort` utiliza para ordenar conjuntos de datos grandes y cuando la aplicación cumple el requisito de espacio O(N) adicional. `parallel_radixsort`puede ser especialmente útil cuando la operación de comparación equivalente es más costosa o cuando ambas operaciones son costosas.

> [!CAUTION]
> La implementación de una buena función hash requiere que conozca el intervalo del conjunto de datos y cómo se transforma cada elemento del conjunto de datos en un valor sin signo correspondiente. Dado que la operación hash funciona en valores sin signo, considere una estrategia de ordenación diferente si no se pueden generar valores hash sin signo.

En el ejemplo siguiente `sort`se `parallel_sort` `parallel_buffered_sort`compara `parallel_radixsort` el rendimiento de , , , y con el mismo conjunto grande de datos aleatorios.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

En este ejemplo, que supone que es aceptable asignar espacio O(N) durante la ordenación, `parallel_radixsort` realiza lo mejor en este conjunto de datos en esta configuración del equipo.

[[Superior](#top)]

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Cómo: Escribir un bucle parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Muestra cómo utilizar `parallel_for` el algoritmo para realizar la multiplicación de matrices.|
|[Cómo: Escribir un bucle parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Muestra cómo utilizar `parallel_for_each` el algoritmo para calcular el recuento de números primos en un objeto [std::array](../../standard-library/array-class-stl.md) en paralelo.|
|[Cómo: Usar parallel.invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Muestra cómo usar el algoritmo `parallel_invoke` para mejorar el rendimiento del algoritmo de ordenación bitónica.|
|[Cómo: Usar parallel_invoke para ejecutar operaciones paralelas](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Muestra cómo usar el algoritmo `parallel_invoke` para mejorar el rendimiento de un programa que realiza varias operaciones en un origen de datos compartido.|
|[Cómo: Realizar operaciones de asignación y reducción en paralelo](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Muestra cómo utilizar `parallel_transform` `parallel_reduce` los algoritmos y para realizar un mapa y reducir la operación que cuenta las apariciones de palabras en archivos.|
|[Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Describe la PPL, que proporciona un modelo de programación imperativo que promueve la escalabilidad y la facilidad de uso para el desarrollo de aplicaciones simultáneas.|
|[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)|Explica el rol de cancelación en la PPL, cómo cancelar el trabajo paralelo y cómo determinar cuándo se cancela un grupo de tareas.|
|[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Explica el rol de control de excepciones en el Runtime de simultaneidad.|

## <a name="reference"></a>Referencia

[parallel_for (función)](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each (función)](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke (Función)](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner (clase)](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner (clase)](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner (clase)](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner (clase)](../../parallel/concrt/reference/static-partitioner-class.md)

[Función parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort (función)](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort (función)](reference/concurrency-namespace-functions.md#parallel_radixsort)
