---
title: "Usar mosaicos | Microsoft Docs"
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
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
caps.latest.revision: 18
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar mosaicos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede utilizar la disposición en mosaico para maximizar la aceleración de la aplicación.  La disposición en mosaicos divide los subprocesos en subconjuntos o *mosaicos* rectangulares iguales.  Si se utiliza un tamaño apropiado de mosaico y un algoritmo de teselado apropiado, se puede obtener mayor aceleración del código C\+\+ AMP.  Los componentes básicos de la disposición en mosaico son:  
  
-   Variables de `tile_static`.  La ventaja principal de la disposición en mosaico es el aumento del rendimiento desde el acceso `tile_static`.  El acceso a los datos en memoria de `tile_static` puede ser mucho más rápido que el acceso a los datos en el espacio global \(`array` u objetos de `array_view`\).  Se crea una instancia de la variable `tile_static` para cada mosaico y todos los subprocesos del mosaico tienen acceso a la variable.  En un típico algoritmo de disposición en mosaico, los datos se copian en la memoria `tile_static` una vez que están en la memoria global, y después se puede obtener acceso a ellos desde la memoria `tile_static`.  
  
-   [tile\_barrier::wait \(Método\)](../Topic/tile_barrier::wait%20Method.md).  Una llamada a `tile_barrier::wait` suspende la ejecución del subproceso actual hasta que todos los subprocesos en el mismo mosaico llaman a `tile_barrier::wait`.  No se puede garantizar el orden en el que los subprocesos se van a ejecutar. Solo puede garantizar que ningún subproceso del mosaico se ejecutará después de la llamada a `tile_barrier::wait` hasta que todos los subprocesos hayan alcanzado la llamada.  Esto significa que utilizando el método de `tile_barrier::wait`, se pueden realizar tareas mosaico a mosaico en lugar de subproceso a subproceso.  Un algoritmo de disposición en mosaico típico tiene código para inicializar la memoria `tile_static` para todo el mosaico después de una llamada a `tile_barrer::wait`.  El código que sigue `tile_barrier::wait` contiene los cálculos que requieren acceso a todos los valores de `tile_static`.  
  
-   Indización local y global.  Tiene acceso al índice del subproceso que concierne a la totalidad del objeto `array_view` o `array` y al índice que concierne al mosaico.  Si utiliza el índice local puede hacer que su código sea más fácil de leer y de depurar.  Normalmente, se utiliza la indización local para tener acceso a las variables de `tile_static`, y la indización global para tener acceso a las variables `array` y `array_view`.  
  
-   [tiled\_extent \(Clase\)](../../parallel/amp/reference/tiled-extent-class.md) y [tiled\_index \(Clase\)](../../parallel/amp/reference/tiled-index-class.md).  Use un objeto `tiled_extent` en lugar de un objeto `extent` en la llamada a `parallel_for_each`.  Use un objeto `tiled_index` en lugar de un objeto `index` en la llamada a `parallel_for_each`.  
  
 Para aprovechar el teselado, el algoritmo debe dividir el dominio del cálculo en mosaicos y copiar a continuación los datos del mosaico en variables de `tile_static` para así tener un acceso más rápido.  
  
## Ejemplo de índices globales, de mosaico y locales  
 El siguiente diagrama representa una matriz de datos de 8x9 que está organizada en mosaicos de 2x3.  
  
 ![Matriz de 8 por 9 dividido en mosaicos de 2 por 3](../../parallel/amp/media/usingtilesmatrix.png "UsingTilesMatrix")  
  
 El siguiente ejemplo muestra los índices globales, los índices de disposición en mosaicos y los índices locales de esta matriz de disposición en mosaicos.  Un objeto `array_view` se crea utilizando elementos de tipo `Description`.  La `Description` contiene los índices globales, los índices del mosaico y los índices locales del elemento en la matriz.  El código de llamada a `parallel_for_each` establece los valores de los índices globales, los índices del mosaico y los índices locales de cada elemento.  La salida muestra los valores en las estructuras de `Description`.  
  
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
    int colorValue = (color == 0) ? 4 : 2;  
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);  
}  
  
// A helper function for formatting the output.  
void SetConsoleSize(int height, int width) {  
    COORD coord; coord.X = width; coord.Y = height;  
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);  
    SMALL_RECT* rect = new SMALL_RECT();  
    rect->Left = 0; rect->Top = 0; rect->Right = width; rect->Bottom = height;  
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);  
}  
  
// This method creates an 8x9 matrix of Description structures. In the call to parallel_for_each, the structure is updated   
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
  
void main() {  
    TilingDescription();  
    char wait;  
    std::cin >> wait;  
}  
  
```  
  
 El objetivo principal del ejemplo se centra en la definición del objeto `array_view` y en la llamada a `parallel_for_each`.  
  
1.  El vector de estructuras de `Description` se copia en un objeto 8x9 `array_view`.  
  
2.  Al método `parallel_for_each` se le llama con un objeto `tiled_extent` como al dominio de cálculo.  El objeto `tiled_extent` se crea llamando al método `extent::tile()` de la variable `descriptions`.  Los parámetros tipo de la llamada a `extent::tile()`, `<2,3>`, especifican que se crean mosaicos de 2x3.  Así, la matriz de 8x9 está dispuesta en 12 mosaicos, cuatro filas y tres columnas.  
  
3.  Al método de `parallel_for_each` se le llama mediante un objeto `tiled_index<2,3>` \(`t_idx`\) como el índice.  Los parámetros tipo del índice \(`t_idx`\) deben coincidir con los parámetros tipo del dominio de cálculo \(`descriptions.extent.tile< 2, 3>()`\).  
  
4.  Cuando se ejecuta cada subproceso, el índice `t_idx` devuelve información acerca de en qué mosaico está el subproceso \(propiedad`tiled_index::tile`\) así como la ubicación del subproceso dentro del mosaico \(propiedad`tiled_index::local`\).  
  
## Sincronización del mosaico: tile\_static y tile\_barrier::wait  
 El ejemplo anterior muestra el diseño y los índices del mosaico, pero el ejemplo por si solo no es muy útil.  El mosaico resulta útil cuando los mosaicos son enteros para el algoritmo y explotan las variables de `tile_static`.  Dado que todos los subprocesos de un mosaico tienen acceso a las variables de `tile_static`, las llamadas a `tile_barrier::wait` se utilizan para sincronizar el acceso a las variables de `tile_static`.  Aunque todos los subprocesos de un mosaico tengan acceso a las variables de `tile_static` , no se garantiza ningún orden en la ejecución de subprocesos del mosaico.  El siguiente ejemplo muestra cómo utilizar las variables `tile_static` y el método `tile_barrier::wait` para calcular el valor medio de cada mosaico.  Estas son las claves para entender el ejemplo:  
  
1.  Los datos sin formato se almacenan en una matriz de 8x8.  
  
2.  El tamaño del mosaico es de 2x2.  Esto crea una cuadrícula de mosaicos de 4x4 y los promedios se pueden almacenar en una matriz de 4x4, utilizando un objeto `array`.  Solo hay un número limitado de tipos que se pueden capturar por referencia en una función restringida por AMP.  La clase `array` es una de ellos.  
  
3.  El tamaño de la matriz y el tamaño de la muestra se definen mediante instrucciones `#define`, porque los parámetros tipo de `array`, `array_view`, `extent` y `tiled_index` deben ser valores constantes.  También se pueden utilizar las declaraciones de `const int static`.  Como ventaja adicional, es trivial cambiar el tamaño de la muestra para calcular el promedio de los mosaicos 4x4.  
  
4.  Se declara una matriz `tile_static` de 2x2 con valores flotantes para cada mosaico.  Aunque la declaración está en la ruta de acceso al código para cada subproceso, en la matriz solo se crea un vector para cada mosaico.  
  
5.  Hay una línea de código para copiar los valores de cada mosaico a la matriz `tile_static`.  Para cada subproceso, después de que el valor se copia en la matriz, la ejecución en el subproceso se detiene debido a la llamada a `tile_barrier::wait`.  
  
6.  Cuando todos los subprocesos de un mosaico han alcanzado la barrera, se puede calcular el promedio.  Dado que el código se ejecuta para cada subproceso, existe una instrucción `if` que calcula solo el promedio en un subproceso.  El promedio se almacena en la variable de promedios.  La barrera es esencialmente el concepto que controla los cálculos por mosaico, es como si se utilizara un bucle `for`.  
  
7.  Los datos en la variable `averages`, porque es un objeto `array`, se deben copiar de nuevo al host.  Este ejemplo utiliza el operador de conversión de vectores.  
  
8.  En el ejemplo completo, se puede cambiar SAMPLESIZE a 4 y el código se ejecuta correctamente sin hacer ningún otro cambio.  
  
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
    // Output for SAMPLESSIZE = 2 is:  
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
  
## Condiciones de carrera  
 Podría ser tentador crear una variable de `tile_static` denominada `total` y aumentar dicha variable para cada subproceso, como se indica a continuación:  
  
```cpp  
  
// Do not do this.  
tile_static float total;  
total += matrix[t_idx];  
t_idx.barrier.wait();  
averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);  
  
```  
  
 El primer problema de este enfoque es que las variables de `tile_static` no pueden tener inicializadores.  El segundo problema es que hay una condición de carrera en la asignación a `total`, porque todos los subprocesos del mosaico tienen acceso a la variable sin un orden determinado.  Es posible programar un algoritmo para que solo permita el acceso de un subproceso al total en cada barrera, tal como se muestra a continuación.  Esta solución, sin embargo, no puede ampliarse.  
  
```cpp  
  
// Do not do this.  
tile_static float total;  
if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {  
    total = matrix[t_idx];  
}  
t_idx.barrier.wait();  
  
if (t_idx.local[0] == 0 && t_idx.local[1] == 1) {  
    total += matrix[t_idx];  
}  
t_idx.barrier.wait();  
  
// etc.  
  
```  
  
## Obstáculos de memoria  
 Hay dos tipos de accesos a la memoria que deben estar sincronizados: el acceso a la memoria global memoria y el acceso a la memoria de `tile_static`.  Un objeto `concurrency::array` asigna solo memoria global.  Un `concurrency::array_view` puede hacer referencia a la memoria global, a la memoria de `tile_static`, o a ambas, en función de cómo se construyó.  Hay dos tipos de memoria que deben estar sincronizadas:  
  
-   memoria global  
  
-   `tile_static`  
  
 Una *barrera de memoria* garantiza que los accesos a la memoria estén disponibles para los otros subprocesos en el mosaico del subproceso, y que los accesos a la memoria se ejecuten según el orden programado.  Para asegurar esto, los compiladores y los procesadores no reordenan la lectura y escritura a través de la barrera.  En el AMP de C\+\+, se crea una barrera de memoria mediante una llamada a uno de estos métodos:  
  
-   [tile\_barrier::wait \(Método\)](../Topic/tile_barrier::wait%20Method.md): crea una barrera alrededor tanto de la memoria global como de la memoria `tile_static`.  
  
-   [tile\_barrier::wait\_with\_all\_memory\_fence \(Método\)](../Topic/tile_barrier::wait_with_all_memory_fence%20Method.md): crea una barrera alrededor tanto de la memoria global como de la memoria `tile_static`.  
  
-   [tile\_barrier::wait\_with\_global\_memory\_fence \(Método\)](../Topic/tile_barrier::wait_with_global_memory_fence%20Method.md): crea una barrera alrededor únicamente de la memoria global.  
  
-   [tile\_barrier::wait\_with\_tile\_static\_memory\_fence \(Método\)](../Topic/tile_barrier::wait_with_tile_static_memory_fence%20Method.md): crea una barrera alrededor únicamente de la memoria de `tile_static`.  
  
 Llamar a la barrera específica que se necesita puede mejorar el rendimiento de la aplicación.  El tipo de barrera influye en el modo en que el compilador y el hardware reordenan las instrucciones.  Por ejemplo, si utiliza una barrera de memoria global, esta solo se aplica a los accesos de memoria globales y por consiguiente, el compilador y el hardware podrían cambiar el orden de lectura y escritura de las variables de `tile_static` en los dos lados de la barrera.  
  
 En el ejemplo siguiente, la barrera sincroniza la escritura con `tileValues`, una variable de `tile_static`.  En este ejemplo, se llama a `tile_barrier::wait_with_tile_static_memory_fence` en lugar de a `tile_barrier::wait`.  
  
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
  
```  
  
## Vea también  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [tile\_static \(Palabra clave\)](../../cpp/tile-static-keyword.md)