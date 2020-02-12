---
title: Usar mosaicos
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: e5cedde255846f61ed0aaadacbd9966c00a03c9d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126271"
---
# <a name="using-tiles"></a>Usar mosaicos

Puede usar la disposición en mosaico para maximizar la aceleración de la aplicación. El mosaico divide los subprocesos en subconjuntos o *mosaicos*rectangulares iguales. Si usa un tamaño de icono y un algoritmo en mosaico adecuados, puede obtener aún más aceleración del código C++ del amp. Los componentes básicos de la disposición en mosaico son:

- `tile_static` variables. La principal ventaja de la disposición en mosaico es la ganancia de rendimiento de `tile_static` acceso. El acceso a los datos de `tile_static` memoria puede ser mucho más rápido que el acceso a los datos en el espacio global (objetos`array` o `array_view`). Se crea una instancia de la variable `tile_static` para cada mosaico y todos los subprocesos del mosaico tienen acceso a la variable. En un algoritmo en mosaico típico, los datos se copian en `tile_static` memoria una vez desde la memoria global y, a continuación, se tiene acceso a ellas muchas veces desde la memoria de `tile_static`.

- [tile_barrier:: Wait (método](reference/tile-barrier-class.md#wait)). Una llamada a `tile_barrier::wait` suspende la ejecución del subproceso actual hasta que todos los subprocesos del mismo mosaico lleguen a la llamada a `tile_barrier::wait`. No se puede garantizar el orden en el que se ejecutarán los subprocesos, solo que no se ejecutarán los subprocesos del mosaico más allá de la llamada a `tile_barrier::wait` hasta que todos los subprocesos hayan alcanzado la llamada. Esto significa que, al usar el método `tile_barrier::wait`, puede realizar tareas en mosaico a mosaico en lugar de subproceso por subproceso. Un algoritmo de mosaico típico tiene código para inicializar el `tile_static` memoria para todo el mosaico seguido de una llamada a `tile_barrier::wait`. El código siguiente `tile_barrier::wait` contiene cálculos que requieren acceso a todos los valores de `tile_static`.

- Indexación local y global. Tiene acceso al índice del subproceso en relación con todo el `array_view` o `array` objeto y con el Índice relativo al mosaico. El uso del índice local puede hacer que el código sea más fácil de leer y depurar. Normalmente, se usa la indexación local para tener acceso a las variables `tile_static` e indexación global para tener acceso a las variables `array` y `array_view`.

- [Tiled_extent clase](../../parallel/amp/reference/tiled-extent-class.md) y [tiled_index clase](../../parallel/amp/reference/tiled-index-class.md). Se usa un objeto de `tiled_extent` en lugar de un objeto `extent` en la llamada a `parallel_for_each`. Se usa un objeto de `tiled_index` en lugar de un objeto `index` en la llamada a `parallel_for_each`.

Para aprovechar las ventajas de la disposición en mosaico, el algoritmo debe particionar el dominio de cálculo en mosaicos y, a continuación, copiar los datos del icono en variables de `tile_static` para obtener un acceso más rápido.

## <a name="example-of-global-tile-and-local-indices"></a>Ejemplo de índices globales, de mosaico y locales

El siguiente diagrama representa una matriz de datos 8x9 que se organiza en mosaicos de 2x3.

![una&#45;matriz&#45;de 8 por 9 dividida en 2&#45;por&#45;3 mosaicos](../../parallel/amp/media/usingtilesmatrix.png "una&#45;matriz&#45;de 8 por 9 dividida en 2&#45;por&#45;3 mosaicos")

En el ejemplo siguiente se muestran los índices globales, de mosaico y locales de esta matriz en mosaico. Se crea un objeto de `array_view` mediante el uso de elementos de tipo `Description`. El `Description` contiene los índices globales, de mosaico y locales del elemento de la matriz. El código de la llamada a `parallel_for_each` establece los valores de los índices globales, de mosaico y locales de cada elemento. La salida muestra los valores de las estructuras `Description`.

```cpp
#include <iostream>
#include <iomanip>
#include <Windows.h>
#include <amp.h>
using namespace concurrency;

const int ROWS = 8;
const int COLS = 9;

// tileRow and tileColumn specify the tile that each thread is in.
// globalRow and globalColumn specify the location of the thread in the array_view.
// localRow and localColumn specify the location of the thread relative to the tile.
struct Description {
    int value;
    int tileRow;
    int tileColumn;
    int globalRow;
    int globalColumn;
    int localRow;
    int localColumn;
};

// A helper function for formatting the output.
void SetConsoleColor(int color) {
    int colorValue = (color == 0)  4 : 2;
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);
}

// A helper function for formatting the output.
void SetConsoleSize(int height, int width) {
    COORD coord;

    coord.X = width;
    coord.Y = height;
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);

    SMALL_RECT* rect = new SMALL_RECT();
    rect->Left = 0;
    rect->Top = 0;
    rect->Right = width;
    rect->Bottom = height;
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);
}

// This method creates an 8x9 matrix of Description structures.
// In the call to parallel_for_each, the structure is updated
// with tile, global, and local indices.
void TilingDescription() {
    // Create 72 (8x9) Description structures.
    std::vector<Description> descs;
    for (int i = 0; i < ROWS * COLS; i++) {
        Description d = {i, 0, 0, 0, 0, 0, 0};
        descs.push_back(d);
    }

    // Create an array_view from the Description structures.
    extent<2> matrix(ROWS, COLS);
    array_view<Description, 2> descriptions(matrix, descs);

    // Update each Description with the tile, global, and local indices.
    parallel_for_each(descriptions.extent.tile< 2, 3>(),
        [=] (tiled_index< 2, 3> t_idx) restrict(amp)
    {
        descriptions[t_idx].globalRow = t_idx.global[0];
        descriptions[t_idx].globalColumn = t_idx.global[1];
        descriptions[t_idx].tileRow = t_idx.tile[0];
        descriptions[t_idx].tileColumn = t_idx.tile[1];
        descriptions[t_idx].localRow = t_idx.local[0];
        descriptions[t_idx].localColumn= t_idx.local[1];
    });

    // Print out the Description structure for each element in the matrix.
    // Tiles are displayed in red and green to distinguish them from each other.
    SetConsoleSize(100, 150);
    for (int row = 0; row < ROWS; row++) {
        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Value: " << std::setw(2) << descriptions(row, column).value << "      ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Tile:   " << "(" << descriptions(row, column).tileRow << "," << descriptions(row, column).tileColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Global: " << "(" << descriptions(row, column).globalRow << "," << descriptions(row, column).globalColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Local:  " << "(" << descriptions(row, column).localRow << "," << descriptions(row, column).localColumn << ")  ";
        }
        std::cout << "\n";
        std::cout << "\n";
    }
}

int main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

El trabajo principal del ejemplo está en la definición del objeto `array_view` y la llamada a `parallel_for_each`.

1. El vector de las estructuras de `Description` se copia en un objeto de `array_view` 8x9.

2. Se llama al método `parallel_for_each` con un objeto `tiled_extent` como el dominio de cálculo. El objeto `tiled_extent` se crea llamando al método `extent::tile()` de la variable `descriptions`. Los parámetros de tipo de la llamada a `extent::tile()`, `<2,3>`, especifican que se crean mosaicos de 2x3. Por lo tanto, la matriz 8x9 se coloca en mosaico en 12 mosaicos, cuatro filas y tres columnas.

3. Se llama al método `parallel_for_each` mediante un objeto `tiled_index<2,3>` (`t_idx`) como índice. Los parámetros de tipo del índice (`t_idx`) deben coincidir con los parámetros de tipo del dominio de proceso (`descriptions.extent.tile< 2, 3>()`).

4. Cuando se ejecuta cada subproceso, el índice `t_idx` devuelve información sobre el mosaico en el que se encuentra el subproceso (`tiled_index::tile` propiedad) y la ubicación del subproceso en el mosaico (propiedad`tiled_index::local`).

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>Sincronización de iconos: tile_static y tile_barrier:: wait

En el ejemplo anterior se muestran los índices y el diseño del icono, pero no es muy útil.  El mosaico resulta útil cuando los mosaicos son integrales para el algoritmo y aprovechan las variables de `tile_static`. Dado que todos los subprocesos de un mosaico tienen acceso a las variables de `tile_static`, las llamadas a `tile_barrier::wait` se utilizan para sincronizar el acceso a las variables `tile_static`. Aunque todos los subprocesos de un mosaico tienen acceso a las variables `tile_static`, no hay ningún orden garantizado de ejecución de subprocesos en el icono. En el ejemplo siguiente se muestra cómo usar las variables `tile_static` y el método `tile_barrier::wait` para calcular el valor medio de cada mosaico. Estas son las claves para comprender el ejemplo:

1. RawData se almacena en una matriz de 8 x 8.

2. El tamaño del mosaico es 2x2. Esto crea una cuadrícula 4x4 de mosaicos y los promedios se pueden almacenar en una matriz 4x4 mediante un objeto `array`. Solo hay un número limitado de tipos que puede capturar por referencia en una función con restricción de AMP. La clase `array` es uno de ellos.

3. El tamaño de la matriz y el tamaño de la muestra se definen mediante instrucciones de `#define`, porque los parámetros de tipo para `array`, `array_view`, `extent`y `tiled_index` deben ser valores constantes. También puede usar declaraciones `const int static`. Como ventaja adicional, es trivial cambiar el tamaño de la muestra para calcular el promedio de los mosaicos de 4x4.

4. Se declara una matriz de 2x2 `tile_static` de valores Float para cada mosaico. Aunque la declaración está en la ruta de acceso del código para cada subproceso, solo se crea una matriz para cada mosaico de la matriz.

5. Hay una línea de código para copiar los valores de cada mosaico en la `tile_static` matriz. Para cada subproceso, una vez que el valor se copia en la matriz, la ejecución en el subproceso se detiene debido a la llamada a `tile_barrier::wait`.

6. Cuando todos los subprocesos de un mosaico han alcanzado la barrera, se puede calcular el promedio. Dado que el código se ejecuta para cada subproceso, hay una instrucción `if` para calcular únicamente el promedio en un subproceso. El promedio se almacena en la variable promedios. La barrera es esencialmente la construcción que controla los cálculos por mosaico, de forma muy similar a como podría usar un bucle `for`.

7. Los datos de la variable `averages`, porque es un objeto `array`, se deben copiar de nuevo al host. En este ejemplo se usa el operador de conversión de vectores.

8. En el ejemplo completo, puede cambiar MUESTREAdor a 4 y el código se ejecuta correctamente sin realizar ningún otro cambio.

```cpp
#include <iostream>
#include <amp.h>
using namespace concurrency;

#define SAMPLESIZE 2
#define MATRIXSIZE 8
void SamplingExample() {

    // Create data and array_view for the matrix.
    std::vector<float> rawData;
    for (int i = 0; i < MATRIXSIZE * MATRIXSIZE; i++) {
        rawData.push_back((float)i);
    }
    extent<2> dataExtent(MATRIXSIZE, MATRIXSIZE);
    array_view<float, 2> matrix(dataExtent, rawData);

    // Create the array for the averages.
    // There is one element in the output for each tile in the data.
    std::vector<float> outputData;
    int outputSize = MATRIXSIZE / SAMPLESIZE;
    for (int j = 0; j < outputSize * outputSize; j++) {
        outputData.push_back((float)0);
    }
    extent<2> outputExtent(MATRIXSIZE / SAMPLESIZE, MATRIXSIZE / SAMPLESIZE);
    array<float, 2> averages(outputExtent, outputData.begin(), outputData.end());

    // Use tiles that are SAMPLESIZE x SAMPLESIZE.
    // Find the average of the values in each tile.
    // The only reference-type variable you can pass into the parallel_for_each call
    // is a concurrency::array.
    parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
        [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
    {
        // Copy the values of the tile into a tile-sized array.
        tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
        tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

        // Wait for the tile-sized array to load before you calculate the average.
        t_idx.barrier.wait();

        // If you remove the if statement, then the calculation executes for every
        // thread in the tile, and makes the same assignment to averages each time.
        if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {
            for (int trow = 0; trow < SAMPLESIZE; trow++) {
                for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {
                    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
                }
            }
            averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);
        }
    });

    // Print out the results.
    // You cannot access the values in averages directly. You must copy them
    // back to a CPU variable.
    outputData = averages;
    for (int row = 0; row < outputSize; row++) {
        for (int col = 0; col < outputSize; col++) {
            std::cout << outputData[row*outputSize + col] << " ";
        }
        std::cout << "\n";
    }
    // Output for SAMPLESIZE = 2 is:
    //  4.5  6.5  8.5 10.5
    // 20.5 22.5 24.5 26.5
    // 36.5 38.5 40.5 42.5
    // 52.5 54.5 56.5 58.5

    // Output for SAMPLESIZE = 4 is:
    // 13.5 17.5
    // 45.5 49.5
}

int main() {
    SamplingExample();
}
```

## <a name="race-conditions"></a>Condiciones de carrera

Podría ser tentador crear una variable de `tile_static` denominada `total` y aumentar esa variable para cada subproceso, como se indica a continuación:

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

El primer problema de este enfoque es que `tile_static` variables no pueden tener inicializadores. El segundo problema es que hay una condición de carrera en la asignación a `total`, porque todos los subprocesos del mosaico tienen acceso a la variable en ningún orden determinado. Puede programar un algoritmo para permitir solo que un subproceso tenga acceso al total en cada barrera, como se muestra a continuación. Sin embargo, esta solución no es extensible.

```cpp
// Do not do this.
tile_static float total;
if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
    total = matrix[t_idx];
}
t_idx.barrier.wait();

if (t_idx.local[0] == 0&& t_idx.local[1] == 1) {
    total += matrix[t_idx];
}
t_idx.barrier.wait();

// etc.
```

## <a name="memory-fences"></a>Límites de memoria

Hay dos tipos de accesos de memoria que se deben sincronizar: acceso a memoria global y `tile_static` acceso a memoria. Un objeto `concurrency::array` asigna solo memoria global. Un `concurrency::array_view` puede hacer referencia a la memoria global, `tile_static` memoria o ambos, en función de cómo se haya construido.  Hay dos tipos de memoria que se deben sincronizar:

- memoria global

- `tile_static`

Una *barrera de memoria* garantiza que los accesos de memoria estén disponibles para otros subprocesos en el mosaico de subprocesos y que los accesos a memoria se ejecuten según el orden del programa. Para garantizar esto, los compiladores y los procesadores no reordenan las lecturas y escrituras en la barrera. En C++ amp, una barrera de memoria se crea mediante una llamada a uno de estos métodos:

- [tile_barrier:: wait Method](reference/tile-barrier-class.md#wait): crea una barrera alrededor de la memoria global y de `tile_static`.

- [método tile_barrier:: wait_with_all_memory_fence](reference/tile-barrier-class.md#wait_with_all_memory_fence): crea una barrera alrededor de la memoria global y `tile_static`.

- [método tile_barrier:: wait_with_global_memory_fence](reference/tile-barrier-class.md#wait_with_global_memory_fence): crea una barrera alrededor únicamente de la memoria global.

- [método tile_barrier:: wait_with_tile_static_memory_fence](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): crea una barrera alrededor únicamente de la memoria `tile_static`.

Llamar a la barrera específica que necesita puede mejorar el rendimiento de la aplicación. El tipo de barrera afecta al modo en que el compilador y las instrucciones de reordenación de hardware. Por ejemplo, si usa una barrera de memoria global, solo se aplica a los accesos de memoria globales y, por tanto, el compilador y el hardware pueden reordenar las lecturas y escrituras en `tile_static` variables en los dos lados de la barrera.

En el ejemplo siguiente, la barrera sincroniza las escrituras en `tileValues`, una variable de `tile_static`. En este ejemplo, se llama a `tile_barrier::wait_with_tile_static_memory_fence` en lugar de `tile_barrier::wait`.

```cpp
// Using a tile_static memory fence.
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
    [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
{
    // Copy the values of the tile into a tile-sized array.
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

    // Wait for the tile-sized array to load before calculating the average.
    t_idx.barrier.wait_with_tile_static_memory_fence();

    // If you remove the if statement, then the calculation executes
    // for every thread in the tile, and makes the same assignment to
    // averages each time.
    if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
        for (int trow = 0; trow <SAMPLESIZE; trow++) {
            for (int tcol = 0; tcol <SAMPLESIZE; tcol++) {
                averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
            }
        }
    averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
    }
});
```

## <a name="see-also"></a>Consulte también

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[tile_static (Palabra clave)](../../cpp/tile-static-keyword.md)
