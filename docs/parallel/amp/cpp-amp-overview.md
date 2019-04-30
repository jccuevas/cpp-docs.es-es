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
ms.openlocfilehash: 258266768d3f456fb761a9d5a403a92c502dbe32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349908"
---
# <a name="c-amp-overview"></a>Información general sobre C++ AMP

C++ Accelerated Massive Parallelism (C++ AMP) acelera la ejecución del código de C++ aprovechando las ventajas de hardware de los datos en paralelo, como una unidad de procesamiento de gráficos (GPU) en una tarjeta gráfica discreta. Al utilizar C++ AMP, puede codificar algoritmos de datos multidimensionales para que se acelere la ejecución mediante el uso de paralelismo en hardware heterogéneo. El modelo de programación de C++ AMP incluye matrices multidimensionales, indexación, transferencia de memoria, disposición en mosaico y una biblioteca de funciones matemáticas. Puede usar las extensiones del lenguaje C++ AMP para controlar cómo se mueven los datos de la CPU a la GPU y viceversa, para que se puede mejorar el rendimiento.

## <a name="system-requirements"></a>Requisitos del sistema

- Windows 7 o posterior

- Windows Server 2008 R2 o posterior

- Característica de nivel 11.0 de DirectX 11 o hardware posterior

- Para depurar en el emulador de software, se requiere Windows 8 o Windows Server 2012. Para depurar en el hardware, debe instalar los controladores de su tarjeta gráfica. Para obtener más información, consulte [depurar código de GPU](/visualstudio/debugger/debugging-gpu-code).

- Nota: AMP no se admite actualmente en ARM64.

## <a name="introduction"></a>Introducción

Los dos ejemplos siguientes muestran los principales componentes de C++ AMP. Suponga que desea agregar los elementos correspondientes de dos matrices unidimensionales. Por ejemplo, desea agregar `{1, 2, 3, 4, 5}` y `{6, 7, 8, 9, 10}` obtener `{7, 9, 11, 13, 15}`. Sin utilizar C++ AMP, podría escribir el código siguiente para agregar los números y mostrar los resultados.

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

Las partes importantes del código son los siguientes:

- Datos: Los datos constan de tres matrices. Todos tienen el mismo rango (uno) y longitud (cinco).

- Iteración: La primera `for` bucle proporciona un mecanismo para recorrer en iteración los elementos de las matrices. El código que desea ejecutar para calcular las sumas se encuentra en la primera `for` bloque.

- Índice: El `idx` variable tiene acceso a los elementos individuales de las matrices.

Mediante C++ AMP, podría escribir el código siguiente en su lugar.

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

Los mismos elementos básicos están presentes, pero se utilizan construcciones de C++ AMP:

- Datos: Usa C++ matrices para construir tres C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) objetos. Se proporcionan cuatro valores para construir un `array_view` objeto: los valores de datos, el rango, el tipo de elemento y la longitud de la `array_view` objeto en cada dimensión. El rango y tipo se pasan como parámetros de tipo. Los datos y la longitud se pasan como parámetros del constructor. En este ejemplo, la matriz de C++ que se pasa al constructor es unidimensional. El rango y longitud que se usan para construir la forma rectangular de los datos en el `array_view` objeto y los valores se usan para rellenar la matriz de datos. La biblioteca en tiempo de ejecución también incluye el [array (clase)](../../parallel/amp/reference/array-class.md), que tiene una interfaz similar a la `array_view` clase y se explica más adelante en este artículo.

- Iteración: El [parallel_for_each (función) (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) proporciona un mecanismo para recorrer en iteración los elementos de datos, o *dominio del cálculo*. En este ejemplo, el dominio del cálculo especificado por `sum.extent`. El código que desea ejecutar se encuentra en una expresión lambda, o *función kernel*. El `restrict(amp)` indica que se usa solo el subconjunto del lenguaje C++ que C++ AMP pueda acelerar.

- Índice: El [index (clase)](../../parallel/amp/reference/index-class.md) variable, `idx`, se declara con un rango de uno para que coincida con el rango de la `array_view` objeto. Con el índice, puede tener acceso a los elementos individuales de la `array_view` objetos.

## <a name="shaping-and-indexing-data-index-and-extent"></a>Dando formas e indexando datos: índice y extensión

Debe definir los valores de datos y declarar la forma de los datos antes de poder ejecutar el código de kernel. Todos los datos se define como una matriz (rectangular), y puede definir la matriz para que tenga cualquier rango (número de dimensiones). Los datos pueden ser de cualquier tamaño en cualquiera de las dimensiones.

### <a name="index-class"></a>index (Clase)

El [index (clase)](../../parallel/amp/reference/index-class.md) especifica una ubicación en la `array` o `array_view` objeto encapsulando el desplazamiento desde el origen de cada dimensión en un solo objeto. Cuando tenga acceso a una ubicación de la matriz, se pasa un `index` objeto para el operador de indización, `[]`, en lugar de una lista de índices de entero. Puede acceder a los elementos de cada dimensión mediante el [array::operator() (operador)](reference/array-class.md#operator_call) o [array_view::operator() operador](reference/array-view-class.md#operator_call).

En el ejemplo siguiente se crea un índice unidimensional que especifica el tercer elemento unidimensional `array_view` objeto. El índice se utiliza para imprimir el tercer elemento de la `array_view` objeto. El resultado es 3.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

En el ejemplo siguiente se crea un índice bidimensional que especifica el elemento donde la fila = 1 y la columna = 2 de una matriz bidimensional `array_view` objeto. El primer parámetro de la `index` constructor es el componente de fila y el segundo parámetro es el componente de columna. El resultado es 6.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

En el ejemplo siguiente se crea un índice tridimensional que especifica el elemento donde la profundidad = 0, la fila = 1 y la columna = 3 en tridimensional `array_view` objeto. Tenga en cuenta que el primer parámetro es el componente de profundidad, el segundo parámetro es el componente de fila y el tercer parámetro es el componente de columna. El resultado es 8.

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

El [extent (clase)](../../parallel/amp/reference/extent-class.md) especifica la longitud de los datos en cada dimensión de la `array` o `array_view` objeto. Puede crear una medida y usarla para crear un `array` o `array_view` objeto. También puede recuperar la extensión de un miembro de `array` o `array_view` objeto. El ejemplo siguiente imprime la longitud de la extensión de cada dimensión de una `array_view` objeto.

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

En el ejemplo siguiente se crea un `array_view` objeto que tiene las mismas dimensiones que el objeto en el ejemplo anterior, pero en este ejemplo usa un `extent` objeto en lugar de utilizar parámetros explícitos en el `array_view` constructor.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>Mover datos al acelerador: array y array_view

Se definen dos contenedores de datos que se usa para mover datos al Acelerador de la biblioteca en tiempo de ejecución. Son el [array (clase)](../../parallel/amp/reference/array-class.md) y [array_view (clase)](../../parallel/amp/reference/array-view-class.md). La `array` clase es una clase contenedora que crea una copia en profundidad de los datos cuando se construye el objeto. La `array_view` clase es una clase contenedora que copia los datos cuando la función kernel tiene acceso a los datos. Cuando se necesitan los datos en el dispositivo de origen los datos se copian de nuevo.

### <a name="array-class"></a>array (Clase)

Cuando un `array` se construye el objeto, se crea una copia en profundidad de los datos en el acelerador si utilizas un constructor que incluya un puntero al conjunto de datos. La función kernel modifica la copia en el acelerador. Cuando finalice la ejecución de la función de kernel, debe copiar los datos a la estructura de datos de origen. El ejemplo siguiente multiplica cada elemento de un vector por 10. Una vez finalizada la función de kernel, el `vector conversion operator` se usa para copiar los datos en el objeto de vector.

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

### <a name="arrayview-class"></a>array_view (Clase)

El `array_view` tiene casi los mismos miembros que el `array` clase, pero el comportamiento subyacente no es el mismo. Los datos pasan a la `array_view` constructor no se replica en la GPU como lo es con un `array` constructor. En su lugar, los datos se copian al acelerador cuando se ejecuta la función de kernel. Por lo tanto, si se crean dos `array_view` objetos que usan los mismos datos, ambos `array_view` objetos hacen referencia al mismo espacio de memoria. Al hacerlo, tendrá que sincronizar cualquier acceso multiproceso. La principal ventaja de usar la `array_view` clase es que los datos se mueven solo si es necesario.

### <a name="comparison-of-array-and-arrayview"></a>Comparación de array y array_view

En la tabla siguiente se resumen las similitudes y diferencias entre la `array` y `array_view` clases.

|Descripción|array (clase)|array_view (clase)|
|-----------------|-----------------|-----------------------|
|Cuando se determina el rango|En tiempo de compilación.|En tiempo de compilación.|
|Cuando se determina la extensión|En tiempo de ejecución.|En tiempo de ejecución.|
|Forma|Rectangular.|Rectangular.|
|Almacenamiento de datos|Es un contenedor de datos.|Es un contenedor de datos.|
|Copiar|Copia explícita y profunda en la definición.|Copia implícita cuando se tiene acceso a la función kernel.|
|Recuperación de datos|Copiando los datos de matriz a un objeto en el subproceso de CPU.|Mediante el acceso directo el `array_view` o llamando el [array_view:: Synchronize método](reference/array-view-class.md#synchronize) para seguir accediendo a los datos en el contenedor original.|

### <a name="shared-memory-with-array-and-arrayview"></a>Memoria compartida con matriz y array_view

Memoria compartida es memoria que se puede acceder por la CPU y el acelerador. El uso de memoria compartida elimina o reduce la sobrecarga de copiar datos entre la CPU y el acelerador. Aunque la memoria se comparte, no se puede acceder a él al mismo tiempo la CPU y el acelerador y, si lo hace un comportamiento indefinido.

`array` objetos pueden utilizarse para especificar un mayor control sobre el uso de memoria compartida si el Acelerador asociado lo admite. Si un acelerador admite memoria compartida viene determinada por el Acelerador [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) propiedad, que devuelve **true** cuando se admite memoria compartida. Si se admite memoria compartida, el valor predeterminado [access_type (enumeración)](reference/concurrency-namespace-enums-amp.md#access_type) memoria asignaciones en el Acelerador viene determinada por la `default_cpu_access_type` propiedad. De forma predeterminada, `array` y `array_view` objetos adoptan el mismo `access_type` como principal asociado `accelerator`.

Estableciendo el [array::cpu_access_type miembro de datos](reference/array-class.md#cpu_access_type) propiedad de un `array` explícitamente, puede ejercicio específica controlar a través de la memoria compartida de cómo se usa, por lo que puede optimizar la aplicación para el rendimiento del hardware características, según los patrones de acceso de memoria de los núcleos de cálculo. Un `array_view` refleja el mismo `cpu_access_type` como el `array` que está asociado; o bien, si la array_view se construye sin un origen de datos, su `access_type` refleja el entorno que provoca por primera vez asignar el almacenamiento. Es decir, si primero se obtiene acceso por el host (CPU), a continuación, se comporta como si se crearon a través de un origen de datos de la CPU y recursos compartidos de la `access_type` de la `accelerator_view` asociado por captura; sin embargo, si es primera accediendo a una `accelerator_view`, a continuación, se comporta como si fuese creado a través de un `array` creado en ese `accelerator_view` y comparte el `array`del `access_type`.

El ejemplo de código siguiente muestra cómo determinar si el Acelerador predeterminado admite memoria compartida y, a continuación, crea varias matrices con distintas configuraciones de cpu_access_type.

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

## <a name="executing-code-over-data-parallelforeach"></a>Ejecutando código sobre los datos: parallel_for_each

El [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) función define el código que desea ejecutar en el Acelerador contra los datos en el `array` o `array_view` objeto. Considere el siguiente código de la introducción de este tema.

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

El *dominio del cálculo* es un `extent` objeto o un `tiled_extent` objeto que define el conjunto de subprocesos se pueden crear para la ejecución en paralelo. Se genera un subproceso para cada elemento en el dominio del cálculo. En este caso, el `extent` objeto es unidimensional y tiene cinco elementos. Por lo tanto, se inician cinco subprocesos.

El *expresión lambda* define el código que se ejecutará en cada subproceso. La cláusula de captura `[=]`, especifica que el cuerpo de la expresión lambda tiene acceso a todas las variables capturadas por valor, que en este caso son `a`, `b`, y `sum`. En este ejemplo, la lista de parámetros crea unidimensional `index` variable denominada `idx`. El valor de la `idx[0]` es 0 en el primer subproceso y aumenta en uno en cada subproceso siguiente. El `restrict(amp)` indica que se usa solo el subconjunto del lenguaje C++ que C++ AMP pueda acelerar.  Las limitaciones de las funciones con el modificador limitado se describen en [restrict (AMP de C++)](../../cpp/restrict-cpp-amp.md). Para obtener más información, vea, [sintaxis de expresión Lambda](../../cpp/lambda-expression-syntax.md).

La expresión lambda puede incluir el código para ejecutar o puede llamar a una función kernel independiente. La función kernel debe incluir el `restrict(amp)` modificador. El ejemplo siguiente es equivalente al ejemplo anterior, pero llama a una función kernel independiente.

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

## <a name="accelerating-code-tiles-and-barriers"></a>Acelerar código: Teselas y barreras

Puede obtener la aceleración adicional utilizando mosaicos. Mosaico divide los subprocesos en subconjuntos rectangulares iguales o *iconos*. Determinar el tamaño apropiado del mosaico según el conjunto de datos y el algoritmo que se está escribiendo. Para cada subproceso, tiene acceso a la *global* ubicación de un elemento de datos en relación con toda la `array` o `array_view` y el acceso a la *local* ubicación concierne al mosaico. Con el valor de índice local simplifica el código porque no tiene que escribir el código para convertir los valores de índice de global a local. Para utilizar el teselado, llame a la [extent::tile método](reference/extent-class.md#tile) en el dominio del cálculo en el `parallel_for_each` método y el uso un [tiled_index](../../parallel/amp/reference/tiled-index-class.md) objeto en la expresión lambda.

En las aplicaciones típicas, están relacionados con los elementos de un icono de alguna manera y el código tiene acceso y realizar un seguimiento de los valores a través del mosaico. Use la [tile_static (palabra clave)](../../cpp/tile-static-keyword.md) palabra clave y el [tile_barrier:: Wait (método)](reference/tile-barrier-class.md#wait) para realizar esta acción. Una variable que tiene el **tile_static** palabra clave tiene un ámbito a través de una tesela completa, y se crea una instancia de la variable para cada mosaico. Debe controlar la sincronización de subproceso de icono tenga acceso a la variable. El [tile_barrier:: Wait (método)](reference/tile-barrier-class.md#wait) detiene la ejecución del subproceso actual hasta que todos los subprocesos del mosaico hayan alcanzado la llamada a `tile_barrier::wait`. Por lo que se puedan acumular los valores a través del mosaico mediante el uso de **tile_static** variables. A continuación, puede finalizar cualquier cálculo que requiere acceso a todos los valores.

El siguiente diagrama representa una matriz bidimensional de muestreo de datos que se organizan en teselas.

![Indexar valores en una extensión del mosaico](../../parallel/amp/media/camptiledgridexample.png "indexar valores en una extensión del mosaico")

El siguiente ejemplo de código usa los datos de muestreo del diagrama anterior. El código reemplaza cada valor en el icono de la media de los valores en el icono.

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

C++ AMP incluye dos bibliotecas matemáticas. La biblioteca de precisión doble en la [precise_math Namespace](../../parallel/amp/reference/concurrency-precise-math-namespace.md) proporciona compatibilidad para las funciones de precisión doble. También proporciona compatibilidad para las funciones de precisión sencilla, aunque sigue siendo necesaria la compatibilidad de doble precisión en el hardware. Cumple con el [especificación C99 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/p/?linkid=225887). El acelerador debe admitir doble precisión completa. Puede determinar si lo hace comprobando el valor de la [accelerator::supports_double_precision miembro de datos](reference/accelerator-class.md#supports_double_precision). La librería matemática rápida, en el [fast_math Namespace](../../parallel/amp/reference/concurrency-fast-math-namespace.md), contiene otro conjunto de funciones matemáticas. Estas funciones, que solo admiten `float` operandos, ejecutar más rápidamente, pero no son tan exactas como las de la biblioteca matemática de precisión doble. Las funciones contenidas en el \<amp_math.h > archivo de encabezado y todas se declaran con `restrict(amp)`. Las funciones de la \<cmath > archivo de encabezado se importan en ambos el `fast_math` y `precise_math` espacios de nombres. El **restringir** palabra clave se usa para distinguir el \<cmath > versión y la versión C++ AMP. El código siguiente calcula el logaritmo en base 10, mediante el método rápido de cada valor que se encuentra en el dominio del cálculo.

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

C++ AMP incluye una biblioteca de gráficos que se ha diseñado para la programación de gráficos acelerados. Esta biblioteca se usa únicamente en dispositivos que admiten la funcionalidad de gráficos nativos. Los métodos están en el [Concurrency:: Graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md) y están incluidos en el \<amp_graphics.h > archivo de encabezado. Los componentes clave de la biblioteca de gráficos son:

- [Texture (clase)](../../parallel/amp/reference/texture-class.md): Puede usar la clase textura para crear texturas desde la memoria o desde un archivo. Las texturas se parecen a las matrices porque contienen datos, y se parecen a los contenedores en la biblioteca estándar de C++ con respecto a la asignación y construcción de copia. Para obtener más información, vea [Contenedores de la biblioteca estándar de C++](../../standard-library/stl-containers.md). Los parámetros de plantilla para el `texture` clase son el tipo de elemento y el rango. El rango puede ser 1, 2 o 3. El tipo de elemento puede ser uno de los tipos de vector corto que se describen más adelante en este artículo.

- [writeonly_texture_view (clase)](../../parallel/amp/reference/writeonly-texture-view-class.md): Proporciona acceso de solo escritura a cualquier textura.

- Biblioteca de vectores cortos: Define un conjunto de tipos de vector corto de longitud 2, 3 y 4 que se basan en **int**, `uint`, **float**, **doble**, [norma](../../parallel/amp/reference/norm-class.md), o [unorm](../../parallel/amp/reference/unorm-class.md).

## <a name="universal-windows-platform-uwp-apps"></a>Aplicaciones de Plataforma universal de Windows (UWP)

Al igual que otras bibliotecas de C++, puede utilizar C++ AMP en sus aplicaciones para UWP. Estos artículos describe cómo incluir código de C++ AMP en aplicaciones que se crea mediante el uso de C++, C#, Visual Basic o JavaScript:

- [Uso de C++ AMP en aplicaciones de UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [Tutorial: Crear un componente básico de Windows Runtime en C++ y llamarlo desde JavaScript](http://go.microsoft.com/fwlink/p/?linkid=249077)

- [Optimizador de recorridos de una aplicación de la ventana Store en JavaScript y C++ de mapas de Bing](http://go.microsoft.com/fwlink/p/?linkid=249078)

- [Cómo usar C++ AMP de C# con el tiempo de ejecución de Windows](http://go.microsoft.com/fwlink/p/?linkid=249080)

- [Cómo usar C++ AMP desde C#](http://go.microsoft.com/fwlink/p/?linkid=249081)

- [Llamar a funciones nativas desde código administrado](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP y visualizador de simultaneidad

El visualizador de simultaneidad incluye compatibilidad para analizar el rendimiento del código C++ AMP. Estos artículos describen estas características:

- [Gráfico de actividad de GPU](/visualstudio/profiling/gpu-activity-graph)

- [Actividad de GPU (Paginación)](/visualstudio/profiling/gpu-activity-paging)

- [Actividad GPU (este proceso)](/visualstudio/profiling/gpu-activity-this-process)

- [Actividad GPU (otros procesos)](/visualstudio/profiling/gpu-activity-other-processes)

- [Canales (vista de subprocesos)](/visualstudio/profiling/channels-threads-view)

- [Análisis de código de AMP de C++ con el visualizador de simultaneidad](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)

## <a name="performance-recommendations"></a>Recomendaciones de rendimiento

Módulo y la división de enteros sin signo tienen un rendimiento significativamente mejor que el módulo y la división de enteros con signo. Se recomienda usar enteros sin signo cuando sea posible.

## <a name="see-also"></a>Vea también

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Sintaxis de la expresión lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Referencia (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Programación en paralelo en código nativo](http://go.microsoft.com/fwlink/p/?linkid=238472)
