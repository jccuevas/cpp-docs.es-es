---
title: Algoritmos paralelos
ms.date: 11/19/2018
helpviewer_keywords:
- parallel algorithms [Concurrency Runtime]
ms.assetid: 045dca7b-4d73-4558-a44c-383b88a28473
ms.openlocfilehash: 3e9cce9af01ea108e6510d42e5eedba8ef05a7a4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142920"
---
# <a name="parallel-algorithms"></a>Algoritmos paralelos

La biblioteca de patrones de procesamiento paralelo (PPL) proporciona algoritmos que realizan el trabajo simultáneamente en colecciones de datos. Estos algoritmos son similares a los proporcionados C++ por la biblioteca estándar.

Los algoritmos paralelos se componen de la funcionalidad existente en el Runtime de simultaneidad. Por ejemplo, el algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) usa un objeto [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) para realizar las iteraciones del bucle paralelo. Las particiones del algoritmo de `parallel_for` funcionan de manera óptima en función del número de recursos informáticos disponibles.

## <a name="top"></a> Secciones

- [Algoritmo de parallel_for](#parallel_for)

- [Algoritmo de parallel_for_each](#parallel_for_each)

- [Algoritmo de parallel_invoke](#parallel_invoke)

- [Algoritmos parallel_transform y parallel_reduce](#parallel_transform_reduce)

    - [Algoritmo de parallel_transform](#parallel_transform)

    - [Algoritmo de parallel_reduce](#parallel_reduce)

    - [Ejemplo: realización de la asignación y reducción en paralelo](#map_reduce_example)

- [Trabajo de creación de particiones](#partitions)

- [Ordenación paralela](#parallel_sorting)

    - [Elegir un algoritmo de ordenación](#choose_sort)

## <a name="parallel_for"></a>Algoritmo de parallel_for

El algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) realiza repetidamente la misma tarea en paralelo. Cada una de estas tareas se parametriza mediante un valor de iteración. Este algoritmo es útil cuando se tiene un cuerpo de bucle que no comparte recursos entre iteraciones de ese bucle.

El algoritmo `parallel_for` crea particiones de las tareas de forma óptima para la ejecución en paralelo. Utiliza un algoritmo de robo de trabajo y un robo de intervalo para equilibrar estas particiones cuando se desequilibran las cargas de trabajo. Cuando una iteración de bucle se bloquea de forma cooperativa, el Runtime redistribuye el intervalo de iteraciones que se asignan al subproceso actual a otros subprocesos o procesadores. Del mismo modo, cuando un subproceso completa un intervalo de iteraciones, el tiempo de ejecución redistribuye el trabajo de otros subprocesos a ese subproceso. El algoritmo `parallel_for` también admite *Paralelismo anidado*. Cuando un bucle paralelo contiene otro bucle paralelo, el tiempo de ejecución coordina los recursos de procesamiento entre los cuerpos de bucle de una forma eficaz para la ejecución en paralelo.

El algoritmo `parallel_for` tiene varias versiones sobrecargadas. La primera versión toma un valor inicial, un valor final y una función de trabajo (una expresión lambda, un objeto de función o un puntero de función). La segunda versión toma un valor inicial, un valor final, un valor por el que se va a recorrer y una función de trabajo. La primera versión de esta función usa 1 como valor de paso. Las versiones restantes toman objetos de particionador, que le permiten especificar cómo se deben particionar los intervalos de `parallel_for` entre subprocesos. Los particionadores se explican con más detalle en la sección [trabajo de partición](#partitions) en este documento.

Puede convertir muchos bucles `for` para utilizar `parallel_for`. Sin embargo, el algoritmo de `parallel_for` difiere de la instrucción `for` de las siguientes maneras:

- El algoritmo de `parallel_for` `parallel_for` no ejecuta las tareas en un orden determinado previamente.

- El algoritmo `parallel_for` no admite condiciones de terminación arbitrarias. El algoritmo de `parallel_for` se detiene cuando el valor actual de la variable de iteración es uno menos que `last`.

- El parámetro de tipo `_Index_type` debe ser un tipo entero. Este tipo entero puede ser con o sin signo.

- La iteración del bucle debe reenviarse. El algoritmo `parallel_for` produce una excepción de tipo [STD:: invalid_argument](../../standard-library/invalid-argument-class.md) si el parámetro `_Step` es menor que 1.

- El mecanismo de control de excepciones para el algoritmo `parallel_for` difiere del de un bucle `for`. Si se producen varias excepciones simultáneamente en un cuerpo de bucle paralelo, el tiempo de ejecución propaga solo una de las excepciones al subproceso que llamó a `parallel_for`. Además, cuando una iteración de bucle produce una excepción, el tiempo de ejecución no detiene inmediatamente el bucle total. En su lugar, el bucle se coloca en el estado cancelado y el tiempo de ejecución descarta cualquier tarea que no se haya iniciado todavía. Para obtener más información sobre el control de excepciones y los algoritmos paralelos, vea [control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Aunque el algoritmo de `parallel_for` no admite condiciones de terminación arbitrarias, puede utilizar la cancelación para detener todas las tareas. Para obtener más información sobre la cancelación, vea [cancelación en la biblioteca PPL](cancellation-in-the-ppl.md).

> [!NOTE]
> El costo de programación que resulta del equilibrio de carga y de la compatibilidad con características como la cancelación podría no superar las ventajas de ejecutar el cuerpo del bucle en paralelo, especialmente cuando el cuerpo del bucle es relativamente pequeño. Puede minimizar esta sobrecarga con un particionador en el bucle paralelo. Para obtener más información, vea creación de [particiones](#partitions) en el trabajo más adelante en este documento.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica del algoritmo `parallel_for`. En este ejemplo se imprime en la consola cada valor en el intervalo [1, 5] en paralelo.

[!code-cpp[concrt-parallel-for-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_1.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
1 2 4 3 5
```

Dado que el algoritmo `parallel_for` actúa en cada elemento en paralelo, variará el orden en que se imprimen los valores en la consola.

Para obtener un ejemplo completo que usa el algoritmo `parallel_for`, vea [Cómo: escribir un bucle de parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md).

[[Arriba](#top)]

## <a name="parallel_for_each"></a>Algoritmo de parallel_for_each

El algoritmo [Concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) realiza tareas en un contenedor iterativo, como los que proporciona la C++ biblioteca estándar, en paralelo. Usa la misma lógica de creación de particiones que el algoritmo `parallel_for`.

El algoritmo `parallel_for_each` es similar al C++ algoritmo [std:: For_each](../../standard-library/algorithm-functions.md#for_each) de la biblioteca estándar, con la excepción de que el algoritmo `parallel_for_each` ejecuta las tareas simultáneamente. Al igual que otros algoritmos paralelos, `parallel_for_each` no ejecuta las tareas en un orden específico.

Aunque el algoritmo de `parallel_for_each` funciona en iteradores hacia delante e iteradores de acceso aleatorio, se comporta mejor con los iteradores de acceso aleatorio.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica del algoritmo `parallel_for_each`. En este ejemplo se imprime en la consola cada valor de un objeto [STD:: Array](../../standard-library/array-class-stl.md) en paralelo.

[!code-cpp[concrt-parallel-for-each-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_2.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
4 5 1 2 3
```

Dado que el algoritmo `parallel_for_each` actúa en cada elemento en paralelo, variará el orden en que se imprimen los valores en la consola.

Para obtener un ejemplo completo que usa el algoritmo `parallel_for_each`, vea [Cómo: escribir un bucle de parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md).

[[Arriba](#top)]

## <a name="parallel_invoke"></a>Algoritmo de parallel_invoke

El algoritmo [Concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) ejecuta un conjunto de tareas en paralelo. No vuelve hasta que finaliza cada tarea. Este algoritmo es útil cuando tiene varias tareas independientes que desea ejecutar al mismo tiempo.

El algoritmo `parallel_invoke` toma como sus parámetros una serie de funciones de trabajo (funciones lambda, objetos de función o punteros de función). El algoritmo de `parallel_invoke` se sobrecarga para llevar entre dos y diez parámetros. Cada función que pase a `parallel_invoke` debe tomar cero parámetros.

Al igual que otros algoritmos paralelos, `parallel_invoke` no ejecuta las tareas en un orden específico. El tema [paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md) explica cómo se relaciona el algoritmo de `parallel_invoke` con las tareas y los grupos de tareas.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra la estructura básica del algoritmo `parallel_invoke`. Este ejemplo llama a la función `twice` en tres variables locales e imprime el resultado en la consola.

[!code-cpp[concrt-parallel-invoke-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_3.cpp)]

En este ejemplo se produce la siguiente salida:

```Output
108 11.2 HelloHello
```

Para obtener ejemplos completos que usan el algoritmo de `parallel_invoke`, vea [Cómo: usar parallel_invoke para escribir una rutina de ordenación paralela](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md) y [cómo: usar Parallel_invoke para ejecutar operaciones paralelas](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md).

[[Arriba](#top)]

## <a name="parallel_transform_reduce"></a>Algoritmos parallel_transform y parallel_reduce

Los algoritmos [Concurrency::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) y [concurrency::p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) son versiones paralelas de C++ los algoritmos de la biblioteca estándar [STD:: transform](../../standard-library/algorithm-functions.md#transform) y [STD:: ACCUMULATE](../../standard-library/numeric-functions.md#accumulate), respectivamente. Las versiones Runtime de simultaneidad se comportan como las versiones de la C++ biblioteca estándar, salvo que el orden de la operación no se determina porque se ejecutan en paralelo. Use estos algoritmos cuando trabaje con un conjunto que sea lo suficientemente grande como para que las ventajas de rendimiento y escalabilidad se procesen en paralelo.

> [!IMPORTANT]
> Los algoritmos `parallel_transform` y `parallel_reduce` admiten solo iteradores de acceso aleatorio, bidireccionales y hacia delante porque estos iteradores generan direcciones de memoria estables. Además, estos iteradores deben generar valores l que no sean de`const`.

### <a name="parallel_transform"></a>Algoritmo de parallel_transform

Puede usar el algoritmo de `parallel transform` para realizar muchas operaciones de paralelización de datos. Por ejemplo, puede:

- Ajustar el brillo de una imagen y realizar otras operaciones de procesamiento de imágenes.

- Sumar o tomar el producto de punto entre dos vectores y realizar otros cálculos numéricos en vectores.

- Realice un seguimiento de rayos 3D, donde cada iteración hace referencia a un píxel que se debe representar.

En el ejemplo siguiente se muestra la estructura básica que se usa para llamar al algoritmo `parallel_transform`. En este ejemplo se niega cada elemento de un objeto STD::[Vector](../../standard-library/vector-class.md) de dos maneras. La primera forma utiliza una expresión lambda. La segunda forma utiliza [STD:: Negate](../../standard-library/negate-struct.md), que deriva de [std:: unary_function](../../standard-library/unary-function-struct.md).

[!code-cpp[concrt-basic-parallel-transform#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_4.cpp)]

> [!WARNING]
> En este ejemplo se muestra el uso básico de `parallel_transform`. Dado que la función de trabajo no realiza una cantidad significativa de trabajo, en este ejemplo no se espera un aumento significativo del rendimiento.

El algoritmo `parallel_transform` tiene dos sobrecargas. La primera sobrecarga toma un intervalo de entrada y una función unaria. La función unaria puede ser una expresión lambda que toma un argumento, un objeto de función o un tipo que deriva de `unary_function`. La segunda sobrecarga toma dos intervalos de entrada y una función binaria. La función binaria puede ser una expresión lambda que toma dos argumentos, un objeto de función o un tipo que deriva de [STD:: binary_function](../../standard-library/binary-function-struct.md). En el ejemplo siguiente se muestran estas diferencias.

[!code-cpp[concrt-parallel-transform-vectors#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_5.cpp)]

> [!IMPORTANT]
> El iterador que se proporciona para la salida de `parallel_transform` debe superponerse por completo al iterador de entrada o no superponerse en absoluto. El comportamiento de este algoritmo no se especifica si los iteradores de entrada y salida se superponen parcialmente.

### <a name="parallel_reduce"></a>Algoritmo de parallel_reduce

El algoritmo `parallel_reduce` es útil cuando se tiene una secuencia de operaciones que satisface la propiedad asociativa. (Este algoritmo no requiere la propiedad conmutable). Estas son algunas de las operaciones que puede realizar con `parallel_reduce`:

- Multiplica las secuencias de matrices para generar una matriz.

- Multiplica un vector por una secuencia de matrices para generar un vector.

- Calcula la longitud de una secuencia de cadenas.

- Combine una lista de elementos, como cadenas, en un elemento.

En el siguiente ejemplo básico se muestra cómo usar el algoritmo `parallel_reduce` para combinar una secuencia de cadenas en una cadena. Al igual que con los ejemplos de `parallel_transform`, no se esperan mejoras de rendimiento en este ejemplo básico.

[!code-cpp[concrt-basic-parallel-reduce#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_6.cpp)]

En muchos casos, puede pensar en `parallel_reduce` como una abreviatura para el uso del algoritmo de `parallel_for_each` junto con la clase [Concurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) .

### <a name="map_reduce_example"></a>Ejemplo: realización de la asignación y reducción en paralelo

Una operación de *asignación* aplica una función a cada valor de una secuencia. Una operación de *reducción* combina los elementos de una secuencia en un valor. Puede usar las funciones C++ [STD:: transform](../../standard-library/algorithm-functions.md#transform) y [STD:: ACCUMULATE](../../standard-library/numeric-functions.md#accumulate) de la biblioteca estándar para realizar operaciones de asignación y reducción. Sin embargo, para muchos problemas, puede usar el algoritmo de `parallel_transform` para realizar la operación de asignación en paralelo y el algoritmo de `parallel_reduce` realizar la operación de reducción en paralelo.

En el ejemplo siguiente se compara el tiempo que se tarda en calcular la suma de los números primos en serie y en paralelo. La fase de asignación transforma los valores no primos en 0 y la fase de reducción suma los valores.

[!code-cpp[concrt-parallel-map-reduce-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_7.cpp)]

Para obtener otro ejemplo que realiza una operación de asignación y reducción en paralelo, vea [Cómo: realizar operaciones de asignación y reducción en paralelo](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md).

[[Arriba](#top)]

## <a name="partitions"></a>Trabajo de creación de particiones

Para ejecutar una operación en paralelo en un origen de datos, un paso esencial es *particionar* el origen en varias secciones a las que pueden tener acceso simultáneamente varios subprocesos. Un particionador especifica cómo un algoritmo paralelo debe particionar los intervalos entre los subprocesos. Como se explicó anteriormente en este documento, la biblioteca PPL usa un mecanismo de particionamiento predeterminado que crea una carga de trabajo inicial y, a continuación, usa un algoritmo de robo de trabajo y un robo de intervalo para equilibrar estas particiones cuando las cargas de trabajo están desequilibradas. Por ejemplo, cuando una iteración de bucle completa un intervalo de iteraciones, el tiempo de ejecución redistribuye el trabajo de otros subprocesos a ese subproceso. Sin embargo, en algunos casos, es posible que desee especificar un mecanismo de creación de particiones diferente que se adapte mejor a su problema.

Los algoritmos `parallel_for`, `parallel_for_each`y `parallel_transform` proporcionan versiones sobrecargadas que toman un parámetro adicional, `_Partitioner`. Este parámetro define el tipo de particionador que divide el trabajo. Estos son los tipos de particionadores que define PPL:

[Concurrency:: affinity_partitioner](../../parallel/concrt/reference/affinity-partitioner-class.md)<br/>
Divide el trabajo en un número fijo de intervalos (normalmente, el número de subprocesos de trabajo que están disponibles para trabajar en el bucle). Este tipo de particionador se parece a `static_partitioner`, pero mejora la afinidad de caché por la forma en que asigna los intervalos a los subprocesos de trabajo. Este tipo de particionador puede mejorar el rendimiento cuando se ejecuta un bucle en el mismo conjunto de datos varias veces (por ejemplo, un bucle dentro de un bucle) y los datos caben en la memoria caché. Este particionador no participa completamente en la cancelación. Tampoco utiliza la semántica de bloqueo cooperativo y, por lo tanto, no se puede usar con bucles paralelos que tienen una dependencia de avance.

[Concurrency:: auto_partitioner](../../parallel/concrt/reference/auto-partitioner-class.md)<br/>
Divide el trabajo en un número inicial de intervalos (normalmente, el número de subprocesos de trabajo que están disponibles para trabajar en el bucle). El tiempo de ejecución usa este tipo de forma predeterminada cuando no se llama a un algoritmo paralelo sobrecargado que toma un parámetro `_Partitioner`. Cada intervalo puede dividirse en subintervalos y, por tanto, permite que se produzca el equilibrio de carga. Cuando se completa un intervalo de trabajo, el tiempo de ejecución redistribuye los subintervalos de trabajo de otros subprocesos a ese subproceso. Use este particionador si la carga de trabajo no se encuentra en una de las otras categorías o si necesita compatibilidad total para la cancelación o el bloqueo cooperativo.

[Concurrency:: simple_partitioner](../../parallel/concrt/reference/simple-partitioner-class.md)<br/>
Divide el trabajo en intervalos de modo que cada intervalo tenga al menos el número de iteraciones especificado por el tamaño de fragmento determinado. Este tipo de particionador participa en el equilibrio de carga; sin embargo, el tiempo de ejecución no divide los intervalos en subintervalos. Para cada trabajo, el tiempo de ejecución comprueba la cancelación y realiza el equilibrio de carga después de que se completen `_Chunk_size` iteraciones.

[Concurrency:: static_partitioner](../../parallel/concrt/reference/static-partitioner-class.md)<br/>
Divide el trabajo en un número fijo de intervalos (normalmente, el número de subprocesos de trabajo que están disponibles para trabajar en el bucle). Este tipo de particionador puede mejorar el rendimiento porque no utiliza robo de trabajo y, por tanto, tiene menos sobrecarga. Utilice este tipo de particionador cuando cada iteración de un bucle paralelo realiza una cantidad de trabajo fija y uniforme y no se requiere compatibilidad para la cancelación o el bloqueo cooperativo.

> [!WARNING]
> Los algoritmos `parallel_for_each` y `parallel_transform` solo admiten contenedores que usan iteradores de acceso aleatorio (como STD::[Vector](../../standard-library/vector-class.md)) para los particionadores estáticos, simples y de afinidad. El uso de contenedores que usan iteradores bidireccionales y hacia delante produce un error en tiempo de compilación. El particionador predeterminado, `auto_partitioner`, admite los tres tipos de iterador.

Normalmente, estos particionadores se usan de la misma manera, salvo `affinity_partitioner`. La mayoría de los tipos de particionador no mantienen el estado y no se modifican en tiempo de ejecución. Por lo tanto, puede crear estos objetos de particionador en el sitio de llamada, tal y como se muestra en el ejemplo siguiente.

[!code-cpp[concrt-static-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_8.cpp)]

Sin embargo, debe pasar un objeto de `affinity_partitioner` como una referencia de valor l que no sea`const`para que el algoritmo pueda almacenar el estado de los bucles futuros que se reutilizarán. En el ejemplo siguiente se muestra una aplicación básica que realiza la misma operación en un conjunto de datos en paralelo varias veces. El uso de `affinity_partitioner` puede mejorar el rendimiento porque es probable que la matriz quepa en la memoria caché.

[!code-cpp[concrt-affinity-partitioner#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_9.cpp)]

> [!CAUTION]
> Tenga cuidado al modificar el código existente que se basa en la semántica de bloqueo cooperativo para usar `static_partitioner` o `affinity_partitioner`. Estos tipos de particionador no usan equilibrio de carga ni robo de intervalo y, por lo tanto, pueden modificar el comportamiento de la aplicación.

La mejor manera de determinar si se usa un particionador en un escenario determinado es experimentar y medir cuánto tiempo tardan en completarse las operaciones con las cargas y configuraciones de equipo representativas. Por ejemplo, el particionamiento estático podría proporcionar un aumento significativo de la velocidad en un equipo de varios núcleos que tenga solo unos pocos núcleos, pero podría dar como resultado una ralentización de los equipos que tienen relativamente muchos núcleos.

[[Arriba](#top)]

## <a name="parallel_sorting"></a>Ordenación paralela

La biblioteca PPL proporciona tres algoritmos de ordenación: [Concurrency::p arallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::p arallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort)y [Concurrency::p arallel_radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Estos algoritmos de ordenación son útiles cuando se tiene un conjunto de datos que se puede beneficiar de que se ordene en paralelo. En concreto, la ordenación en paralelo es útil cuando se tiene un conjunto de datos grande o cuando se usa una operación de comparación de cálculo costosa para ordenar los datos. Cada uno de estos algoritmos ordena los elementos en su lugar.

Los algoritmos `parallel_sort` y `parallel_buffered_sort` son algoritmos basados en comparación. Es decir, comparan los elementos por valor. El algoritmo `parallel_sort` no tiene requisitos de memoria adicionales y es adecuado para la ordenación de uso general. El algoritmo de `parallel_buffered_sort` puede funcionar mejor que `parallel_sort`, pero requiere espacio O (N).

El algoritmo `parallel_radixsort` está basado en hash. Es decir, usa claves enteras para ordenar elementos. Mediante el uso de claves, este algoritmo puede calcular directamente el destino de un elemento en lugar de usar comparaciones. Como `parallel_buffered_sort`, este algoritmo requiere O (N) espacio.

En la tabla siguiente se resumen las propiedades importantes de los tres algoritmos de ordenación paralelos.

|Algoritmo|Descripción|Mecanismo de ordenación|Estabilidad de orden|Requisitos de memoria|Complejidad de tiempo|Acceso de iterador|
|---------------|-----------------|-----------------------|--------------------|-------------------------|---------------------|---------------------|
|`parallel_sort`|Ordenación basada en comparación de uso general.|Basado en comparación (ascendente)|Inestable|None|O ((N/P) log (N/P) + 2N ((P-1)/P)|Random|
|`parallel_buffered_sort`|Ordenación basada en comparación de uso general más rápida que requiere O (N) espacio.|Basado en comparación (ascendente)|Inestable|Requiere espacio adicional O (N)|O ((N/P) log (N))|Random|
|`parallel_radixsort`|Ordenación basada en claves entera que requiere espacio O (N).|Basado en hash|Stable|Requiere espacio adicional O (N)|O (N/P)|Random|

En la ilustración siguiente se muestran las propiedades importantes de los tres algoritmos de ordenación paralelos más gráficamente.

![Comparación de los algoritmos de ordenación](../../parallel/concrt/media/concrt_parallel_sorting.png "Comparación de los algoritmos de ordenación")

Estos algoritmos de ordenación paralelas siguen las reglas de cancelación y control de excepciones. Para obtener más información sobre la cancelación y el control de excepciones en el Runtime de simultaneidad, vea [Cancelar algoritmos paralelos](../../parallel/concrt/cancellation-in-the-ppl.md#algorithms) y [control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

> [!TIP]
> Estos algoritmos de ordenación paralelos admiten la semántica de movimiento. Puede definir un operador de asignación de movimiento para permitir que las operaciones de intercambio se realicen de forma más eficaz. Para obtener más información sobre la semántica de movimiento y el operador de asignación de movimiento, vea [declarador de referencia de valor r: & &](../../cpp/rvalue-reference-declarator-amp-amp.md)y [constructores de movimiento y operadores de asignación de movimiento (C++)](../../cpp/move-constructors-and-move-assignment-operators-cpp.md). Si no proporciona un operador de asignación de movimiento o una función de intercambio, los algoritmos de ordenación utilizan el constructor de copias.

En el siguiente ejemplo básico se muestra cómo usar `parallel_sort` para ordenar una `vector` de valores `int`. De forma predeterminada, `parallel_sort` usa [STD:: less](../../standard-library/less-struct.md) para comparar valores.

[!code-cpp[concrt-basic-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_10.cpp)]

En este ejemplo se muestra cómo proporcionar una función de comparación personalizada. Usa el método [STD:: Complex:: real](../../standard-library/complex-class.md#real) para ordenar los valores de la > de tipo [STD:: Complex\<doble](../../standard-library/complex-double.md) en orden ascendente.

[!code-cpp[concrt-basic-parallel-sort#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_11.cpp)]

En este ejemplo se muestra cómo proporcionar una función hash al algoritmo `parallel_radixsort`. En este ejemplo se ordenan los puntos 3D. Los puntos se ordenan en función de su distancia desde un punto de referencia.

[!code-cpp[concrt-parallel-sort-points#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_12.cpp)]

En la ilustración, este ejemplo utiliza un conjunto de datos relativamente pequeño. Puede aumentar el tamaño inicial del vector para experimentar con mejoras de rendimiento en conjuntos de datos de mayor tamaño.

En este ejemplo se usa una expresión lambda como función hash. También puede usar una de las implementaciones integradas de la clase STD::[hash](../../standard-library/hash-class.md) o definir su propia especialización. También puede usar un objeto de función hash personalizado, tal como se muestra en este ejemplo:

[!code-cpp[concrt-parallel-sort-points#2](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_13.cpp)]

[!code-cpp[concrt-parallel-sort-points#3](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_14.cpp)]

La función hash debe devolver un tipo entero ([STD:: is_integral:: el valor](../../standard-library/is-integral-class.md) debe ser **true**). Este tipo entero se debe poder convertir al tipo `size_t`.

### <a name="choose_sort"></a>Elegir un algoritmo de ordenación

En muchos casos, `parallel_sort` proporciona el mejor equilibrio entre velocidad y rendimiento de la memoria. Sin embargo, a medida que aumenta el tamaño del conjunto de datos, el número de procesadores disponibles o la complejidad de la función de comparación, `parallel_buffered_sort` o `parallel_radixsort` pueden funcionar mejor. La mejor manera de determinar qué algoritmo de ordenación usar en un escenario determinado es experimentar y medir cuánto tiempo se tarda en ordenar los datos típicos en configuraciones de equipo representativas. Tenga en cuenta las siguientes directrices al elegir una estrategia de ordenación.

- Tamaño del conjunto de datos. En este documento, un conjunto de información *pequeño* contiene menos de 1.000 elementos, un conjunto de caracteres *mediano* contiene entre los elementos 10.000 y 100.000, y un conjunto de caracteres *grande* contiene más de 100.000 elementos.

- La cantidad de trabajo que realiza la función de comparación o la función hash.

- La cantidad de recursos informáticos disponibles.

- Características del conjunto de datos. Por ejemplo, un algoritmo podría funcionar bien para los datos que ya están ordenados, pero no también para los datos que están completamente sin ordenar.

- Tamaño del fragmento. El argumento opcional `_Chunk_size` especifica cuándo cambia el algoritmo de una implementación de ordenación paralela a una serie, ya que divide la ordenación global en unidades de trabajo más pequeñas. Por ejemplo, si proporciona 512, el algoritmo cambia a la implementación en serie cuando una unidad de trabajo contiene 512 o menos elementos. Una implementación en serie puede mejorar el rendimiento general porque elimina la sobrecarga necesaria para procesar los datos en paralelo.

Es posible que no merezca la pena ordenar un conjunto de valores pequeño en paralelo, incluso si tiene un gran número de recursos informáticos disponibles o si la función de comparación o función hash realiza una cantidad de trabajo relativamente grande. Puede usar la función [STD:: Sort](../../standard-library/algorithm-functions.md#sort) para ordenar conjuntos de valores pequeños. (`parallel_sort` y `parallel_buffered_sort` llamada a `sort` cuando se especifica un tamaño de fragmento mayor que el conjunto de objetos; sin embargo, `parallel_buffered_sort` tendría que asignar espacio de O (N), lo que podría tardar más tiempo debido a la contención de bloqueos o a la asignación de memoria.

Si debe conservar memoria o si el asignador de memoria está sujeto a la contención de bloqueos, use `parallel_sort` para ordenar un conjunto de DataSet de tamaño medio. `parallel_sort` no requiere ningún espacio adicional; los otros algoritmos requieren O (N) espacio.

Use `parallel_buffered_sort` para ordenar conjuntos de valores de tamaño medio y cuando la aplicación cumpla el requisito de espacio O (N) adicional. `parallel_buffered_sort` puede ser especialmente útil cuando se tiene un gran número de recursos informáticos o una función de comparación o función hash costosa.

Use `parallel_radixsort` para ordenar grandes conjuntos de valores y cuando la aplicación cumpla el requisito de espacio adicional O (N). `parallel_radixsort` puede ser especialmente útil cuando la operación de comparación equivalente es más costosa o cuando ambas operaciones son costosas.

> [!CAUTION]
> La implementación de una función hash correcta requiere que sepa el intervalo del conjunto de elementos y cómo cada elemento del conjunto de elementos se transforme en un valor sin signo correspondiente. Dado que la operación hash funciona en valores sin signo, considere la posibilidad de usar una estrategia de ordenación diferente si no se pueden generar valores hash sin signo.

En el ejemplo siguiente se compara el rendimiento de `sort`, `parallel_sort`, `parallel_buffered_sort`y `parallel_radixsort` con el mismo conjunto grande de datos aleatorios.

[!code-cpp[concrt-choosing-parallel-sort#1](../../parallel/concrt/codesnippet/cpp/parallel-algorithms_15.cpp)]

En este ejemplo, en el que se da por supuesto que es aceptable asignar O (N) espacio durante la ordenación, `parallel_radixsort` se comporta mejor en este conjunto de resultados en esta configuración de equipo.

[[Arriba](#top)]

## <a name="related-topics"></a>Temas relacionados

|Título|Descripción|
|-----------|-----------------|
|[Procedimiento para escribir un bucle parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)|Muestra cómo usar el algoritmo `parallel_for` para realizar la multiplicación de matrices.|
|[Procedimiento para escribir un bucle parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)|Muestra cómo usar el algoritmo `parallel_for_each` para calcular el recuento de números primos en un objeto [STD:: Array](../../standard-library/array-class-stl.md) en paralelo.|
|[Procedimiento para usar parallel.invoke para escribir una rutina de ordenación en paralelo](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)|Muestra cómo usar el algoritmo `parallel_invoke` para mejorar el rendimiento del algoritmo de ordenación bitónica.|
|[Procedimiento para usar parallel.invoke para ejecutar operaciones paralelas](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)|Muestra cómo usar el algoritmo `parallel_invoke` para mejorar el rendimiento de un programa que realiza varias operaciones en un origen de datos compartido.|
|[Procedimiento para realizar operaciones de asignación y reducción en paralelo](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Muestra cómo usar los algoritmos `parallel_transform` y `parallel_reduce` para realizar una operación de asignación y reducción que cuenta las apariciones de las palabras en los archivos.|
|[Biblioteca de patrones de procesamiento paralelo (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Describe la biblioteca PPL, que proporciona un modelo de programación imperativo que promueve la escalabilidad y la facilidad de uso para desarrollar aplicaciones simultáneas.|
|[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)|Explica el rol de cancelación en la biblioteca PPL, cómo cancelar el trabajo paralelo y cómo determinar cuándo se cancela un grupo de tareas.|
|[Control de excepciones](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Explica el rol del control de excepciones en el Runtime de simultaneidad.|

## <a name="reference"></a>Referencia

[parallel_for función)](reference/concurrency-namespace-functions.md#parallel_for)

[parallel_for_each función)](reference/concurrency-namespace-functions.md#parallel_for_each)

[parallel_invoke función)](reference/concurrency-namespace-functions.md#parallel_invoke)

[affinity_partitioner (clase)](../../parallel/concrt/reference/affinity-partitioner-class.md)

[auto_partitioner (clase)](../../parallel/concrt/reference/auto-partitioner-class.md)

[simple_partitioner (clase)](../../parallel/concrt/reference/simple-partitioner-class.md)

[static_partitioner (clase)](../../parallel/concrt/reference/static-partitioner-class.md)

[parallel_sort función)](reference/concurrency-namespace-functions.md#parallel_sort)

[parallel_buffered_sort función)](reference/concurrency-namespace-functions.md#parallel_buffered_sort)

[parallel_radixsort función)](reference/concurrency-namespace-functions.md#parallel_radixsort)
