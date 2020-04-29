---
title: Información general sobre C++ AMP
ms.date: 11/19/2018
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
ms.openlocfilehash: f0b46065371b8cb70802cfc38b7365fd2db14bf5
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538645"
---
# <a name="c-amp-overview"></a>Información general sobre C++ AMP

C++ Accelerated Massive Parallelism (C++ AMP) acelera la ejecución del código de C++ aprovechando el hardware en paralelo de datos, como una unidad de procesamiento de gráficos (GPU) en una tarjeta gráfica discreta. Mediante el uso de C++ AMP, puede codificar algoritmos de datos multidimensionales para que la ejecución se pueda acelerar mediante el uso de paralelismo en hardware heterogéneo. El modelo de programación de C++ AMP incluye matrices multidimensionales, indexación, transferencia de memoria, disposición en mosaico y una biblioteca de funciones matemáticas. Puede usar las extensiones de lenguaje de C++ AMP para controlar cómo se mueven los datos de la CPU a la GPU y viceversa, de modo que pueda mejorar el rendimiento.

## <a name="system-requirements"></a>Requisitos del sistema

- Windows 7 o posterior

- Windows Server 2008 R2 o posterior

- Hardware de nivel de características 11,0 de DirectX 11 o posterior

- Para la depuración en el emulador de software, se requiere Windows 8 o Windows Server 2012. Para depurar en el hardware, debe instalar los controladores de su tarjeta gráfica. Para obtener más información, vea [depurar código de GPU](/visualstudio/debugger/debugging-gpu-code).

- Nota: AMP no se admite actualmente en ARM64.

## <a name="introduction"></a>Introducción

En los dos ejemplos siguientes se muestran los componentes principales de C++ AMP. Suponga que desea agregar los elementos correspondientes de matrices dimensionales de 2 1. Por ejemplo, puede que desee agregar `{1, 2, 3, 4, 5}` y `{6, 7, 8, 9, 10}` obtener. `{7, 9, 11, 13, 15}` Sin usar C++ AMP, puede escribir el código siguiente para agregar los números y mostrar los resultados.

```cpp
#include <iostream>

void StandardMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx < 5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx < 5; idx++)
    {
        std::cout << sumCPP[idx] << "\n";
    }
}
```

Las partes importantes del código son las siguientes:

- Datos: los datos se componen de tres matrices. Todos tienen el mismo rango (uno) y la longitud (cinco).

- Iteración: el `for` primer bucle proporciona un mecanismo para recorrer en iteración los elementos de las matrices. El código que desea ejecutar para calcular las sumas se encuentra en el primer `for` bloque.

- Index: la `idx` variable obtiene acceso a los elementos individuales de las matrices.

Con C++ AMP, puede escribir el código siguiente en su lugar.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

const int size = 5;

void CppAmpMethod() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[size];

    // Create C++ AMP objects.
    array_view<const int, 1> a(size, aCPP);
    array_view<const int, 1> b(size, bCPP);
    array_view<int, 1> sum(size, sumCPP);
    sum.discard_data();

    parallel_for_each(
        // Define the compute domain, which is the set of threads that are created.
        sum.extent,
        // Define the code to run on each thread on the accelerator.
        [=](index<1> idx) restrict(amp) {
            sum[idx] = a[idx] + b[idx];
        }
    );

    // Print the results. The expected output is "7, 9, 11, 13, 15".
    for (int i = 0; i < size; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

Los mismos elementos básicos están presentes, pero se usan C++ AMP construcciones:

- Datos: utilice matrices de C++ para construir tres objetos [array_view](../../parallel/amp/reference/array-view-class.md) de C++ amp. Se proporcionan cuatro valores para construir un `array_view` objeto: los valores de datos, el rango, el tipo de elemento y la longitud del `array_view` objeto en cada dimensión. El rango y el tipo se pasan como parámetros de tipo. Los datos y la longitud se pasan como parámetros de constructor. En este ejemplo, la matriz de C++ que se pasa al constructor es unidimensional. El rango y la longitud se usan para construir la forma rectangular de los datos en `array_view` el objeto y los valores de datos se utilizan para rellenar la matriz. La biblioteca en tiempo de ejecución también incluye la [clase de matriz](../../parallel/amp/reference/array-class.md), que tiene una interfaz `array_view` similar a la clase y se describe más adelante en este artículo.

- Iteración: la [función parallel_for_each (C++ amp)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) proporciona un mecanismo para recorrer en iteración los elementos de datos o el *dominio de cálculo*. En este ejemplo, el dominio de cálculo se especifica mediante `sum.extent`. El código que desea ejecutar está contenido en una expresión lambda o en una *función de kernel*. `restrict(amp)` Indica que solo se utiliza el subconjunto del lenguaje C++ que C++ amp puede acelerar.

- Índice: la variable de [clase](../../parallel/amp/reference/index-class.md) de `idx`índice,, se declara con un rango de uno para que coincida con `array_view` el rango del objeto. Con el índice, puede tener acceso a los elementos individuales de los `array_view` objetos.

## <a name="shaping-and-indexing-data-index-and-extent"></a>Modelar e indexar datos: índice y extensión

Debe definir los valores de datos y declarar la forma de los datos antes de poder ejecutar el código del kernel. Todos los datos se definen como una matriz (rectangular) y puede definir la matriz para que tenga cualquier rango (número de dimensiones). Los datos pueden tener cualquier tamaño en cualquiera de las dimensiones.

### <a name="index-class"></a>index (Clase)

La [clase index](../../parallel/amp/reference/index-class.md) especifica una ubicación en el `array` objeto `array_view` o encapsulando el desplazamiento desde el origen de cada dimensión en un objeto. Cuando se obtiene acceso a una ubicación de la matriz, se `index` pasa un objeto al operador de indización, `[]`, en lugar de una lista de índices de enteros. Puede tener acceso a los elementos de cada dimensión mediante el [operador Array:: Operator ()](reference/array-class.md#operator_call) o [array_view:: Operator ()](reference/array-view-class.md#operator_call).

En el ejemplo siguiente se crea un índice unidimensional que especifica el tercer elemento de un objeto unidimensional `array_view` . El índice se utiliza para imprimir el tercer elemento en el `array_view` objeto. El resultado es 3.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

En el ejemplo siguiente se crea un índice bidimensional que especifica el elemento en el que la fila = 1 y la columna = 2 en un `array_view` objeto bidimensional. El primer parámetro del `index` constructor es el componente de fila y el segundo parámetro es el componente de columna. El resultado es 6.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

En el ejemplo siguiente se crea un índice tridimensional que especifica el elemento donde Depth = 0, Row = 1 y Column = 3 en un `array_view` objeto tridimensional. Observe que el primer parámetro es el componente de profundidad, el segundo parámetro es el componente de fila y el tercer parámetro es el componente de columna. El resultado es 8.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};

array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";
// Output: 8
```

### <a name="extent-class"></a>extent (Clase)

La [clase extent](../../parallel/amp/reference/extent-class.md) especifica la longitud de los datos en cada dimensión del `array` objeto `array_view` o. Puede crear una extensión y utilizarla para crear un `array` objeto o `array_view` . También puede recuperar la extensión de un objeto o `array` `array_view` existente. En el ejemplo siguiente se imprime la longitud de la extensión en cada dimensión `array_view` de un objeto.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
// There are 3 rows and 4 columns, and the depth is two.
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";
```

En el ejemplo siguiente se `array_view` crea un objeto que tiene las mismas dimensiones que el objeto en el ejemplo anterior, pero en este `extent` ejemplo se usa un objeto en lugar de usar `array_view` parámetros explícitos en el constructor.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-array_view"></a>Mover datos al acelerador: matriz y array_view

En la biblioteca en tiempo de ejecución se definen dos contenedores de datos que se usan para trasladar datos al acelerador. Son la [clase de matriz](../../parallel/amp/reference/array-class.md) y la [clase array_view](../../parallel/amp/reference/array-view-class.md). La `array` clase es una clase contenedora que crea una copia en profundidad de los datos cuando se construye el objeto. La `array_view` clase es una clase contenedora que copia los datos cuando la función de kernel tiene acceso a los datos. Cuando los datos son necesarios en el dispositivo de origen, los datos se copian de nuevo.

### <a name="array-class"></a>array (Clase)

Cuando se `array` construye un objeto, se crea una copia en profundidad de los datos en el acelerador si se usa un constructor que incluya un puntero al conjunto de datos. La función kernel modifica la copia en el acelerador. Una vez finalizada la ejecución de la función kernel, debe volver a copiar los datos en la estructura de datos de origen. En el ejemplo siguiente se multiplica cada elemento de un vector por 10. Una vez finalizada la función de kernel `vector conversion operator` , se utiliza para volver a copiar los datos en el objeto de vector.

```cpp
std::vector<int> data(5);

for (int count = 0; count <5; count++)
{
    data[count] = count;
}

array<int, 1> a(5, data.begin(), data.end());

parallel_for_each(
    a.extent,
    [=, &a](index<1> idx) restrict(amp) {
        a[idx] = a[idx]* 10;
    });

data = a;
for (int i = 0; i < 5; i++)
{
    std::cout << data[i] << "\n";
}
```

### <a name="array_view-class"></a>array_view (Clase)

`array_view` Tiene casi los mismos miembros que la `array` clase, pero el comportamiento subyacente no es el mismo. Los datos pasados al `array_view` constructor no se replican en la GPU como si se tratase `array` de un constructor. En su lugar, los datos se copian en el acelerador cuando se ejecuta la función de kernel. Por lo tanto, si crea `array_view` dos objetos que utilizan los mismos datos, `array_view` ambos objetos hacen referencia al mismo espacio de memoria. Al hacerlo, tendrá que sincronizar cualquier acceso multiproceso. La principal ventaja de utilizar la `array_view` clase es que solo se mueven los datos si es necesario.

### <a name="comparison-of-array-and-array_view"></a>Comparación de Array y array_view

En la tabla siguiente se resumen las similitudes y diferencias entre `array` las `array_view` clases y.

|Descripción|array (clase)|array_view (clase)|
|-----------------|-----------------|-----------------------|
|Cuando se determina el rango|En tiempo de compilación.|En tiempo de compilación.|
|Cuando se determina la extensión|En tiempo de ejecución.|En tiempo de ejecución.|
|Forma|Rectangular.|Rectangular.|
|Almacenamiento de datos|Es un contenedor de datos.|Es un contenedor de datos.|
|Copiar|Copia explícita y en profundidad en la definición.|Copia implícita cuando se tiene acceso a ella mediante la función kernel.|
|Recuperación de datos|Copiando los datos de la matriz en un objeto en el subproceso de la CPU.|Mediante el acceso directo del `array_view` objeto o llamando al [método array_view:: Synchronize](reference/array-view-class.md#synchronize) para seguir accediendo a los datos en el contenedor original.|

### <a name="shared-memory-with-array-and-array_view"></a>Memoria compartida con matrices y array_view

La memoria compartida es la memoria a la que puede tener acceso la CPU y el acelerador. El uso de memoria compartida elimina o reduce significativamente la sobrecarga de copiar datos entre la CPU y el acelerador. Aunque la memoria está compartida, no se puede tener acceso a ella simultáneamente por la CPU y el acelerador, y esto provoca un comportamiento indefinido.

`array`los objetos se pueden usar para especificar un control específico sobre el uso de memoria compartida si el acelerador asociado lo admite. La propiedad [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) del acelerador determina si un acelerador admite la memoria compartida, que devuelve **true** cuando se admite la memoria compartida. Si se admite la memoria compartida, la `default_cpu_access_type` propiedad determina la [enumeración access_type](reference/concurrency-namespace-enums-amp.md#access_type) predeterminada para las asignaciones de memoria en el acelerador. De forma predeterminada `array` , `array_view` los objetos y toman el `access_type` mismo que el principal `accelerator`asociado.

Al establecer la propiedad de [miembro de datos Array:: cpu_access_type](reference/array-class.md#cpu_access_type) de un explícitamente, puede ejercer un `array` control exhaustivo sobre cómo se usa la memoria compartida, de modo que pueda optimizar la aplicación para las características de rendimiento del hardware, en función de los patrones de acceso a la memoria de los kernels de cálculo. Un `array_view` objeto refleja el `cpu_access_type` mismo que `array` el objeto al que está asociado; o bien, si la array_view se construye sin un origen de datos `access_type` , su refleja el entorno que primero hace que asigne almacenamiento. Es decir, si el host (CPU) tiene acceso por primera vez, se comporta como si se hubiera creado en un origen de datos de CPU y comparte el `access_type` de la asociada mediante `accelerator_view` la captura; sin embargo, si se obtiene acceso por primera vez `accelerator_view`a `array` , se comporta como si se hubiera creado sobre un creado en `accelerator_view` y comparte la `array`de. `access_type`

En el ejemplo de código siguiente se muestra cómo determinar si el acelerador predeterminado admite la memoria compartida y, a continuación, crea varias matrices que tienen configuraciones de cpu_access_type diferentes.

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.default_cpu_access_type = access_type_read_write

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view inherits its default_cpu_access_type from acc.
    accelerator_view acc_v = acc.default_view;

    // Create an extent object to size the arrays.
    extent<1> ex(10);

    // Input array that can be written on the CPU.
    array<int, 1> arr_w(ex, acc_v, access_type_write);

    // Output array that can be read on the CPU.
    array<int, 1> arr_r(ex, acc_v, access_type_read);

    // Read-write array that can be both written to and read from on the CPU.
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);
}
```

## <a name="executing-code-over-data-parallel_for_each"></a>Ejecutar código sobre datos: parallel_for_each

La función [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) define el código que se desea ejecutar en el acelerador con respecto a los datos `array` del `array_view` objeto o. Considere el siguiente código de la introducción de este tema.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddArrays() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            sum[idx] = a[idx] + b[idx];
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

El `parallel_for_each` método toma dos argumentos, un dominio de cálculo y una expresión lambda.

El *dominio de cálculo* es un `extent` objeto o un `tiled_extent` objeto que define el conjunto de subprocesos que se va a crear para la ejecución en paralelo. Se genera un subproceso para cada elemento del dominio de proceso. En este caso, el `extent` objeto es unidimensional y tiene cinco elementos. Por lo tanto, se inician cinco subprocesos.

La *expresión lambda* define el código que se va a ejecutar en cada subproceso. La cláusula Capture, `[=]`, especifica que el cuerpo de la expresión lambda tiene acceso a todas las variables capturadas por valor, que en `a`este `b`caso son `sum`, y. En este ejemplo, la lista de parámetros crea una variable unidimensional `index` denominada `idx`. El valor de `idx[0]` es 0 en el primer subproceso y se incrementa en uno en cada subproceso subsiguiente. `restrict(amp)` Indica que solo se utiliza el subconjunto del lenguaje C++ que C++ amp puede acelerar.  Las limitaciones de las funciones que tienen el modificador Restrict se describen en [Restrict (C++ amp)](../../cpp/restrict-cpp-amp.md). Para obtener más información, vea [Sintaxis de expresiones lambda](../../cpp/lambda-expression-syntax.md).

La expresión lambda puede incluir el código que se va a ejecutar o puede llamar a una función de kernel independiente. La función kernel debe incluir el `restrict(amp)` modificador. El ejemplo siguiente es equivalente al ejemplo anterior, pero llama a una función de kernel independiente.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddElements(
    index<1> idx,
    array_view<int, 1> sum,
    array_view<int, 1> a,
    array_view<int, 1> b) restrict(amp) {
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp) {
            AddElements(idx, sum, a, b);
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

## <a name="accelerating-code-tiles-and-barriers"></a>Aceleración del código: mosaicos y barreras

Puede obtener una aceleración adicional mediante el uso de mosaicos. El mosaico divide los subprocesos en subconjuntos o *mosaicos*rectangulares iguales. Puede determinar el tamaño de mosaico adecuado en función del conjunto de datos y del algoritmo que va a codificar. Para cada subproceso, tiene acceso a la ubicación *global* de un elemento de datos en relación con `array` el `array_view` total o y el acceso a la ubicación *local* en relación con el mosaico. El uso del valor de índice local simplifica el código porque no es necesario escribir el código para convertir los valores de índice de global a local. Para usar el mosaico, llame al [método extent:: Tile](reference/extent-class.md#tile) en el dominio de cálculo `parallel_for_each` en el método y use un objeto [tiled_index](../../parallel/amp/reference/tiled-index-class.md) en la expresión lambda.

En las aplicaciones típicas, los elementos de un mosaico se relacionan de alguna manera, y el código tiene que tener acceso y realizar un seguimiento de los valores en el mosaico. Use la palabra clave [palabra clave tile_static](../../cpp/tile-static-keyword.md) y el [método tile_barrier:: wait](reference/tile-barrier-class.md#wait) para lograrlo. Una variable que tiene la palabra clave **tile_static** tiene un ámbito en todo el icono y se crea una instancia de la variable para cada mosaico. Debe controlar la sincronización del acceso de subprocesos de mosaicos a la variable. El [método tile_barrier:: wait](reference/tile-barrier-class.md#wait) detiene la ejecución del subproceso actual hasta que todos los subprocesos del mosaico hayan alcanzado `tile_barrier::wait`la llamada a. Por lo tanto, puede acumular valores en el icono mediante variables de **tile_static** . Después, puede finalizar los cálculos que requieran acceso a todos los valores.

El siguiente diagrama representa una matriz bidimensional de datos de muestreo que está organizada en mosaicos.

![Valores de índice en una extensión en mosaico](../../parallel/amp/media/camptiledgridexample.png "Valores de índice en una extensión en mosaico")

En el ejemplo de código siguiente se usan los datos de muestreo del diagrama anterior. El código reemplaza cada valor del mosaico por el promedio de los valores del mosaico.

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
        [=](tiled_index<2,2> idx) restrict(amp) {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];

        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];

        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
    });

for (int i = 0; i <4; i++) {
    for (int j = 0; j <6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="math-libraries"></a>Bibliotecas matemáticas

C++ AMP incluye dos bibliotecas matemáticas. La biblioteca de precisión doble en el [espacio de nombres Concurrency::p recise_math](../../parallel/amp/reference/concurrency-precise-math-namespace.md) proporciona compatibilidad con las funciones de precisión doble. También proporciona compatibilidad con las funciones de precisión sencilla, aunque todavía se requiere compatibilidad de doble precisión en el hardware. Cumple con la [especificación C99 (ISO/IEC 9899)](https://go.microsoft.com/fwlink/p/?linkid=225887). El acelerador debe admitir una precisión doble completa. Puede determinar si comprueba el valor del [miembro de datos Accelerator:: supports_double_precision](reference/accelerator-class.md#supports_double_precision). La biblioteca matemática rápida, en el [espacio de nombres Concurrency:: fast_math](../../parallel/amp/reference/concurrency-fast-math-namespace.md), contiene otro conjunto de funciones matemáticas. Estas funciones, que solo `float` admiten operandos, se ejecutan más rápidamente, pero no son tan precisas como las de la biblioteca matemática de doble precisión. Las funciones están contenidas \<en el archivo de encabezado amp_math. h> y todas `restrict(amp)`se declaran con. Las funciones del archivo \<de encabezado CMATH> se importan en los `fast_math` espacios `precise_math` de nombres y. La palabra clave **Restrict** se usa para distinguir \<la versión> cmath y la versión C++ amp. El código siguiente calcula el logaritmo en base 10, con el método rápido, de cada valor que se encuentra en el dominio de proceso.

```cpp
#include <amp.h>
#include <amp_math.h>
#include <iostream>
using namespace concurrency;

void MathExample() {

    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };
    array_view<double, 1> logs(6, numbers);

    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp) {
            logs[idx] = concurrency::fast_math::log10(numbers[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>Biblioteca de gráficos

C++ AMP incluye una biblioteca de gráficos diseñada para la programación de gráficos acelerada. Esta biblioteca se utiliza solo en dispositivos que admiten la funcionalidad de gráficos nativos. Los métodos se encuentran en el [espacio de nombres Concurrency:: Graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) y \<están contenidos en el archivo de encabezado amp_graphics. h>. Los componentes clave de la biblioteca de gráficos son:

- [clase Texture](../../parallel/amp/reference/texture-class.md): puede utilizar la clase Texture para crear texturas a partir de la memoria o de un archivo. Las texturas se parecen a las matrices porque contienen datos y se parecen a los contenedores de la biblioteca estándar de C++ con respecto a la asignación y la construcción de la copia. Para más información, vea [Contenedores de la biblioteca estándar de C++](../../standard-library/stl-containers.md). Los parámetros de plantilla de `texture` la clase son el tipo de elemento y el rango. El rango puede ser 1, 2 o 3. El tipo de elemento puede ser uno de los tipos de vector cortos que se describen más adelante en este artículo.

- [Writeonly_texture_view clase](../../parallel/amp/reference/writeonly-texture-view-class.md): proporciona acceso de solo escritura a cualquier textura.

- Biblioteca de vectores cortos: define un conjunto de tipos de vector corto de longitud 2, 3 y 4 que se **int**basan en `uint`int,, **float**, **Double**, [Norm](../../parallel/amp/reference/norm-class.md)o [unorm](../../parallel/amp/reference/unorm-class.md).

## <a name="universal-windows-platform-uwp-apps"></a>Aplicaciones de Plataforma universal de Windows (UWP)

Al igual que otras bibliotecas de C++, puede usar C++ AMP en las aplicaciones de UWP. En estos artículos se describe cómo incluir código de C++ AMP en aplicaciones que se crean mediante C++, C#, Visual Basic o JavaScript:

- [Uso de C++ AMP en aplicaciones para UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [Tutorial: crear un componente de Windows Runtime básico en C++ y llamarlo desde JavaScript](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [Optimizador de recorridos de mapas de Bing, una aplicación de la tienda Windows en JavaScript y C++](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [Cómo usar C++ AMP de C# mediante el Windows Runtime](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c-using-winrt/)

- [Cómo usar C++ AMP de C #](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c/)

- [Llamar a funciones nativas desde código administrado](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP y visualizador de simultaneidad

El visualizador de simultaneidad incluye compatibilidad para analizar el rendimiento de C++ AMP código. En estos artículos se describen estas características:

- [Gráfico de actividad de GPU](/visualstudio/profiling/gpu-activity-graph)

- [Actividad de GPU (Paginación)](/visualstudio/profiling/gpu-activity-paging)

- [Actividad GPU (Este proceso)](/visualstudio/profiling/gpu-activity-this-process)

- [Actividad GPU (Otros procesos)](/visualstudio/profiling/gpu-activity-other-processes)

- [Canales (Vista de subprocesos)](/visualstudio/profiling/channels-threads-view)

- [Analizar código de C++ AMP con el visualizador de simultaneidad](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)

## <a name="performance-recommendations"></a>Recomendaciones de rendimiento

El módulo y la división de enteros sin signo tienen un rendimiento significativamente mejor que el módulo y la división de enteros con signo. Se recomienda utilizar enteros sin signo cuando sea posible.

## <a name="see-also"></a>Consulte también

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Sintaxis de la expresión lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Referencia (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Blog de programación en paralelo en código nativo](https://go.microsoft.com/fwlink/p/?linkid=238472)
