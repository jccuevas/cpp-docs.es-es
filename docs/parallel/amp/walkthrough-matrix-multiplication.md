---
title: 'Tutorial: Multiplicación de matrices | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0c61bff6251d5ae833611161ef7b1bb06e6f39a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693200"
---
# <a name="walkthrough-matrix-multiplication"></a>Tutorial: Multiplicación de matrices
Este tutorial muestra, paso a paso, cómo utilizar C++ AMP para acelerar la ejecución de la multiplicación de matrices. Se presentan dos algoritmos, uno sin mosaico y otro con mosaico.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Antes de empezar:  
  
-   Lectura [Introducción a C++ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
-   Lectura [mediante iconos](../../parallel/amp/using-tiles.md).  
  
-   Asegúrese de que [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/reference/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)] o [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] está instalado en el equipo.  
  
### <a name="to-create-the-project"></a>Para crear el proyecto  
  
1.  En la barra de menús de Visual Studio, elija **archivo**, **New**, **proyecto**.  
  
2.  En **instalado** en el panel Plantillas, seleccione **Visual C++**.  
  
3.  Seleccione **proyecto vacío**, escriba `MatrixMultiply` en el **nombre** cuadro y, a continuación, elija la **Aceptar** botón.  
  
4.  Elija el botón **Siguiente**.  
  
5.  En **el Explorador de soluciones**, abra el menú contextual para **archivos de código fuente**y, a continuación, elija **agregar**, **nuevo elemento**.  
  
6.  En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **archivo C++ (.cpp)**, escriba `MatrixMultiply.cpp` en el **nombre** cuadro y, a continuación, elija la **agregar** botón.  
  
## <a name="multiplication-without-tiling"></a>Multiplicación sin mosaico  
 En esta sección, considere la multiplicación de dos matrices, A y B, que se definen a continuación:  
  
 ![3&#45;por&#45;matriz 2](../../parallel/amp/media/campmatrixanontiled.png "campmatrixanontiled")  
  
 ![2&#45;por&#45;matriz 3](../../parallel/amp/media/campmatrixbnontiled.png "campmatrixbnontiled")  
  
 A es una matriz de 3 por 2 y B es una matriz de 2 por 3. El producto de multiplicar A por B es la siguiente matriz de 3 por 3. El producto se calcula multiplicando las filas de A por las columnas de B elemento por elemento.  
  
 ![3&#45;por&#45;matriz 3](../../parallel/amp/media/campmatrixproductnontiled.png "campmatrixproductnontiled")  
  
### <a name="to-multiply-without-using-c-amp"></a>Para multiplicar sin usar C++ AMP  
  
1.  Abra el archivo MatrixMultiply.cpp y use el código siguiente para reemplazar el código existente.  
  
```cpp  
#include <iostream>  
  
void MultiplyWithOutAMP() {  
  
    int aMatrix[3][2] = {{1, 4}, {2, 5}, {3, 6}};  
    int bMatrix[2][3] = {{7, 8, 9}, {10, 11, 12}};  
    int product[3][3] = {{0, 0, 0}, {0, 0, 0}, {0, 0, 0}};  
  
    for (int row = 0; row < 3; row++) {  
        for (int col = 0; col < 3; col++) {  
            // Multiply the row of A by the column of B to get the row, column of product.  
            for (int inner = 0; inner < 2; inner++) {  
                product[row][col] += aMatrix[row][inner] * bMatrix[inner][col];  
            }  
            std::cout << product[row][col] << "  ";  
        }  
        std::cout << "\n";  
    }  
}  
  
void main() {  
    MultiplyWithOutAMP();  
    getchar();  
}  
```  
  
    The algorithm is a straightforward implementation of the definition of matrix multiplication. It does not use any parallel or threaded algorithms to reduce the computation time.  
  
2.  En la barra de menús, pulse **Archivo**, **Guardar todo**.  
  
3.  Elija el método abreviado de teclado F5 para iniciar la depuración y compruebe que el resultado es correcto.  
  
4.  Elija Entrar para salir de la aplicación.  
  
### <a name="to-multiply-by-using-c-amp"></a>Para multiplicar mediante C++ AMP  
  
1.  En MatrixMultiply.cpp, agregue el siguiente código antes del método `main`.  
  
```cpp  
void MultiplyWithAMP() {  
    int aMatrix[] = { 1, 4, 2, 5, 3, 6 };  
    int bMatrix[] = { 7, 8, 9, 10, 11, 12 };  
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0 };  
 
    array_view<int, 2> a(3, 2, aMatrix);

    array_view<int, 2> b(2, 3, bMatrix);

    array_view<int, 2> product(3, 3, productMatrix);

 
    parallel_for_each(product.extent,  
        [=] (index<2> idx) restrict(amp) {  
            int row = idx[0];  
            int col = idx[1];  
            for (int inner = 0; inner <2; inner++) {  
                product[idx] += a(row, inner)* b(inner, col);  
            }  
        });  
 
    product.synchronize();
 
    for (int row = 0; row <3; row++) {  
        for (int col = 0; col <3; col++) { 
            //std::cout << productMatrix[row*3 + col] << "  ";  
            std::cout << product(row, col) << "  ";  
        }    
        std::cout << "\n";  
    }  
}  
```  
  
    The AMP code resembles the non-AMP code. The call to `parallel_for_each` starts one thread for each element in `product.extent`, and replaces the `for` loops for row and column. The value of the cell at the row and column is available in `idx`. You can access the elements of an `array_view` object by using either the `[]` operator and an index variable, or the `()` operator and the row and column variables. The example demonstrates both methods. The `array_view::synchronize` method copies the values of the `product` variable back to the `productMatrix` variable.  
  
2.  Agregue las siguientes instrucciones `include` y `using` en la parte superior de MatrixMultiply.cpp.  
  
```cpp  
#include <amp.h>  
using namespace concurrency;  
```  
  
3.  Modifique el método `main` para llamar al método `MultiplyWithAMP`.  
  
```cpp  
void main() {  
    MultiplyWithOutAMP();  
    MultiplyWithAMP();  
    getchar();  
}  
```  
  
4.  Elija el método abreviado de teclado Ctrl+F5 para iniciar la depuración y comprobar que el resultado es correcto.  
  
5.  Elija la barra espaciadora para salir de la aplicación.  
  
## <a name="multiplication-with-tiling"></a>Multiplicación con mosaico  
 Mosaico es una técnica de partición de datos en subconjuntos de igual tamaño, que se conocen como iconos. Tres cosas cambian cuando se usa el mosaico.  
  
-   Puede crear variables `tile_static`. El acceso a los datos en el espacio `tile_static` puede ser mucho más rápido que el acceso a los datos en el espacio global. Se crea una instancia de la variable `tile_static` para cada mosaico y todos los subprocesos del mosaico tienen acceso a la variable. La ventaja fundamental del mosaico es que mejora el rendimiento debido al acceso `tile_static`.  
  
-   Puede llamar a la [tile_barrier:: wait](reference/tile-barrier-class.md#wait) método para detener todos los subprocesos en un mosaico dentro una línea de código especificada. No se puede garantizar el orden en el que se van a ejecutar los subprocesos, solo se garantiza que todos los subprocesos de un mosaico se ​​detendrán al llamar a `tile_barrier::wait` antes de continuar la ejecución.  

  
-   Tiene acceso al índice del subproceso que concierne a la totalidad del objeto `array_view` y al índice que concierne al mosaico. Al usar el índice local, se facilita la lectura y la depuración del código.  
  
 Para aprovechar las ventajas del mosaico en la multiplicación de matrices, el algoritmo debe dividir la matriz en mosaicos y luego copiar los datos de los mosaicos en variables `tile_static` para un acceso más rápido. En este ejemplo, la matriz se divide en submatrices de igual tamaño. El producto se obtiene multiplicando las submatrices. En este ejemplo, las dos matrices y su producto son:  
  
 ![4&#45;por&#45;matriz 4](../../parallel/amp/media/campmatrixatiled.png "campmatrixatiled")  
  
 ![4&#45;por&#45;matriz 4](../../parallel/amp/media/campmatrixbtiled.png "campmatrixbtiled")  
  
 ![4&#45;por&#45;matriz 4](../../parallel/amp/media/campmatrixproducttiled.png "campmatrixproducttiled")  
  
 Las matrices se dividen en cuatro matrices de 2 por 2, que se definen a continuación:  
  
 ![4&#45;por&#45;matriz 4 dividida en 2&#45;por&#45;sub 2&#45;matrices](../../parallel/amp/media/campmatrixapartitioned.png "campmatrixapartitioned")  
  
 ![4&#45;por&#45;matriz 4 dividida en 2&#45;por&#45;sub 2&#45;matrices](../../parallel/amp/media/campmatrixbpartitioned.png "campmatrixbpartitioned")  
  
 El producto de A y B ahora se puede escribir y calcular tal y como se muestra a continuación:  
  
 ![4&#45;por&#45;matriz 4 dividida en 2&#45;por&#45;sub 2&#45;matrices](../../parallel/amp/media/campmatrixproductpartitioned.png "campmatrixproductpartitioned")  
  
 Dado que las matrices de `a` a `h` son matrices de 2x2, todos sus productos y sumas también son matrices de 2x2. También se deduce que A*B es una matriz de 4x4, tal y como se esperaba. Para comprobar rápidamente el algoritmo, calcule el valor del elemento de la primera fila y la primera columna en el producto. En el ejemplo, este sería el valor del elemento de la primera fila y la primera columna de `ae + bg`. Solo tiene que calcular la primera columna y la primera fila de `ae` y `bg` para cada término. El valor para `ae` es `1*1 + 2*5 = 11`. El valor de `bg` es `3*1 + 4*5 = 23`. El valor total es `11 + 23 = 34`, que es correcto.  
  
 Para implementar este algoritmo, el código:  
  
-   Usa un objeto `tiled_extent` en lugar de un objeto `extent` en la llamada a `parallel_for_each`.  
  
-   Usa un objeto `tiled_index` en lugar de un objeto `index` en la llamada a `parallel_for_each`.  
  
-   Crea variables `tile_static` para contener las submatrices.  
  
-   Usa el método `tile_barrier::wait` para detener los subprocesos de cálculo de los productos de las submatrices.  
  
### <a name="to-multiply-by-using-amp-and-tiling"></a>Para multiplicar usando AMP y el mosaico  
  
1.  En MatrixMultiply.cpp, agregue el siguiente código antes del método `main`.  
  
```cpp  
void MultiplyWithTiling() {  
    // The tile size is 2.  
    static const int TS = 2;  

    // The raw data.  
    int aMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };  
    int bMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };  
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };  

    // Create the array_view objects.  
    array_view<int, 2> a(4, 4, aMatrix);  
    array_view<int, 2> b(4, 4, bMatrix);  
    array_view<int, 2> product(4, 4, productMatrix);  
  
    // Call parallel_for_each by using 2x2 tiles.  
    parallel_for_each(product.extent.tile<TS, TS>(),  
        [=] (tiled_index<TS, TS> t_idx) restrict(amp)   
        { 
            // Get the location of the thread relative to the tile (row, col) 
            // and the entire array_view (rowGlobal, colGlobal).  
            int row = t_idx.local[0];   
            int col = t_idx.local[1];  
            int rowGlobal = t_idx.global[0];  
            int colGlobal = t_idx.global[1];  
            int sum = 0;  
  
            // Given a 4x4 matrix and a 2x2 tile size, this loop executes twice for each thread.  
            // For the first tile and the first loop, it copies a into locA and e into locB.  
            // For the first tile and the second loop, it copies b into locA and g into locB.  
            for (int i = 0; i < 4; i += TS) {  
                tile_static int locA[TS][TS];  
                tile_static int locB[TS][TS];  
                locA[row][col] = a(rowGlobal, col + i);  
                locB[row][col] = b(row + i, colGlobal);  
                // The threads in the tile all wait here until locA and locB are filled.  
                t_idx.barrier.wait();  

                // Return the product for the thread. The sum is retained across 
                // both iterations of the loop, in effect adding the two products 
                // together, for example, a*e.  
                for (int k = 0; k < TS; k++) {  
                    sum += locA[row][k] * locB[k][col];  
                }  

                // All threads must wait until the sums are calculated. If any threads  
                // moved ahead, the values in locA and locB would change.        
                t_idx.barrier.wait();
                // Now go on to the next iteration of the loop.            
            }  
            
            // After both iterations of the loop, copy the sum to the product variable by using the global location.  
            product[t_idx.global] = sum;  
        });

    // Copy the contents of product back to the productMatrix variable.  
    product.synchronize();
 
    for (int row = 0; row <4; row++) {  
        for (int col = 0; col <4; col++) { 
            // The results are available from both the product and productMatrix variables. 
            //std::cout << productMatrix[row*3 + col] << "  ";  
            std::cout << product(row, col) << "  ";  
        }  
        std::cout << "\n";  
    }  
}  
```  
  
    This example is significantly different than the example without tiling. The code uses these conceptual steps:  
  
    1.  Copia los elementos del mosaico [0,0] de `a` en `locA`. Copia los elementos del mosaico [0,0] de `b` en `locB`. Observe que `product` se dispone en mosaico, pero no así `a` y `b`. Por lo tanto, debe usar índices globales para tener acceso a `a, b` y `product`. La llamada a `tile_barrier::wait` es fundamental. Detiene todos los subprocesos del mosaico hasta que se rellenen `locA` y `locB`.  
  
    2.  Multiplica `locA` y `locB` y coloca los resultados en `product`.  
  
    3.  Copiar los elementos del mosaico [0,1] de `a` en `locA`. Copiar los elementos del mosaico [1,0] de `b` en `locB`.  
  
    4.  Multiplica `locA` y `locB` y los añade a los resultados que ya están en `product`.  
  
    5.  La multiplicación del mosaico [0,0] se ha completado.  
  
    6.  Repita los pasos para los otros cuatro mosaicos. No existe indexación específica para los mosaicos, por lo que los subprocesos se pueden ejecutar en cualquier orden. A medida que cada subproceso se ejecuta, se crean las variables `tile_static` para cada mosaico y la llamada a `tile_barrier::wait` controla el flujo del programa.  
  
    7.  Al examinar el algoritmo detenidamente, se observa que cada submatriz se carga en una memoria `tile_static` dos veces. Esa transferencia de datos lleva bastante tiempo. Sin embargo, una vez que los datos están en la memoria `tile_static`, el acceso a los datos es mucho más rápido. Debido a que el cálculo de los productos requiere el acceso repetido a los valores de las submatrices, hay un aumento global del rendimiento. Para cada algoritmo, se requiere práctica para encontrar el tamaño óptimo del algoritmo y del mosaico.  
  
         En los ejemplos que no son de AMP ni de mosaico, se tiene acceso a cada elemento de A y B cuatro veces desde la memoria global para calcular el producto. En el ejemplo del mosaico, se tiene acceso a cada elemento dos veces desde la memoria global y cuatro veces desde la memoria `tile_static`. Eso no supone una mejora significativa del rendimiento. Sin embargo, si A y B fueran matrices de 1024x1024 y el tamaño del mosaico fuese 16, sí habría una mejora de rendimiento significativa. En ese caso, cada elemento solo se copiaría en la memoria `tile_static` 16 veces y se tendría acceso a él 1024 veces desde la memoria `tile_static`.  
  
2.  Modifique el método principal para llamar a la `MultiplyWithTiling` método, tal como se muestra.  
  
```cpp  
void main() {  
    MultiplyWithOutAMP();  
    MultiplyWithAMP();  
    MultiplyWithTiling();  
    getchar();  
}  
```  
  
3.  Elija el método abreviado de teclado Ctrl+F5 para iniciar la depuración y comprobar que el resultado es correcto.  
  
4.  Elija la barra espaciadora para salir de la aplicación.  
  
## <a name="see-also"></a>Vea también  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Tutorial: Depurar una aplicación de C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)

