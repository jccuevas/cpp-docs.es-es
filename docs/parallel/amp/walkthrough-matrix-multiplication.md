---
title: "Tutorial: Multiplicaci&#243;n de matrices | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
caps.latest.revision: 16
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Multiplicaci&#243;n de matrices
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tutorial muestra, paso a paso, cómo utilizar C\+\+ AMP para acelerar la ejecución de la multiplicación de matrices.  Se presentan dos algoritmos, uno sin mosaico y otro con mosaico.  
  
## Requisitos previos  
 Antes de empezar:  
  
-   Lea [Información general sobre C\+\+ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
-   Lea [Usar mosaicos](../../parallel/amp/using-tiles.md).  
  
-   Asegúrese de que [!INCLUDE[win7](../../build/includes/win7_md.md)], [!INCLUDE[win8](../../build/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)] o [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] está instalado en el equipo.  
  
### Para crear el proyecto  
  
1.  En la barra de menús de Visual Studio, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  Debajo de **Instalado** en el panel de plantillas, seleccione **Visual C\+\+**.  
  
3.  Seleccione **Proyecto vacío**, escriba `MatrixMultiply` en el cuadro **Nombre** y después elija el botón **Aceptar**.  
  
4.  Elija el botón **Siguiente**.  
  
5.  En el **Explorador de soluciones**, abra el menú contextual para **Archivos de origen**y, a continuación, elija **Agregar**, **Nuevo elemento**.  
  
6.  En el cuadro de diálogo **Agregar nuevo elemento**, elija **Archivo C\+\+ \(.cpp\)**, escriba `MatrixMultiply.cpp` en el cuadro **Nombre** y después elija el botón **Agregar**.  
  
## Multiplicación sin mosaico  
 En esta sección, considere la multiplicación de dos matrices, A y B, que se definen a continuación:  
  
 ![Matriz de 3 por 2](../../parallel/amp/media/campmatrixanontiled.png "CampMatrixANonTiled")  
  
 ![Matriz de 2 por 3](../../parallel/amp/media/campmatrixbnontiled.png "CampMatrixBNonTiled")  
  
 A es una matriz de 3 por 2 y B es una matriz de 2 por 3.  El producto de multiplicar A por B es la siguiente matriz de 3 por 3.  El producto se calcula multiplicando las filas de A por las columnas de B elemento por elemento.  
  
 ![Matriz de 3 por 3](../../parallel/amp/media/campmatrixproductnontiled.PNG "CampMatrixProductNonTiled")  
  
### Para multiplicar sin usar C\+\+ AMP  
  
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
  
     El algoritmo es una implementación directa de la definición de multiplicación de matrices.  No usa ningún algoritmo paralelo o de subproceso para reducir los tiempos de cálculo.  
  
2.  En la barra de menús, elija **Archivo**, **Guardar todo**.  
  
3.  Elija el método abreviado de teclado F5 para iniciar la depuración y compruebe que el resultado es correcto.  
  
4.  Elija Entrar para salir de la aplicación.  
  
### Para multiplicar mediante C\+\+ AMP  
  
1.  En MatrixMultiply.cpp, agregue el siguiente código antes del método `main`.  
  
    ```cpp  
  
    void MultiplyWithAMP() {  
        int aMatrix[] = { 1, 4, 2, 5, 3, 6 };  
        int bMatrix[] = { 7, 8, 9, 10, 11, 12 };  
        int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0 };  
  
        array_view<int, 2> a(3, 2, aMatrix);  
        array_view<int, 2> b(2, 3, bMatrix);  
        array_view<int, 2> product(3, 3, productMatrix);  
  
        parallel_for_each(  
            product.extent,   
             [=](index<2> idx) restrict(amp) {  
                int row = idx[0];  
                int col = idx[1];  
                for (int inner = 0; inner < 2; inner++) {  
                    product[idx] += a(row, inner) * b(inner, col);  
                }  
            }  
        );  
  
        product.synchronize();  
  
        for (int row = 0; row < 3; row++) {  
            for (int col = 0; col < 3; col++) {  
                //std::cout << productMatrix[row*3 + col] << "  ";  
                std::cout << product(row, col) << "  ";  
            }  
            std::cout << "\n";  
        }  
    }  
  
    ```  
  
     El código de AMP es similar al código que no es de AMP.  La llamada a `parallel_for_each` inicia un subproceso para cada elemento de `product.extent` y reemplaza los bucles `for` por fila y columna.  El valor de la celda en la fila y la columna se encuentra disponible en `idx`.  Puede tener acceso a los elementos de un objeto `array_view` bien usando el operador `[]` y una variable de índice, o el operador `()` y las variables de fila y columna.  En este ejemplo se muestran ambos métodos.  El método `array_view::synchronize` copia los valores de la variable `product` en la variable `productMatrix`.  
  
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
  
4.  Elija el método abreviado de teclado Ctrl\+F5 para iniciar la depuración y comprobar que el resultado es correcto.  
  
5.  Elija la barra espaciadora para salir de la aplicación.  
  
## Multiplicación con mosaico  
 El mosaico es una técnica en la que se crean particiones de datos en subconjuntos de igual tamaño, denominados tiles.  Tres cosas cambian cuando se usa el mosaico.  
  
-   Puede crear variables `tile_static`.  El acceso a los datos en el espacio `tile_static` puede ser mucho más rápido que el acceso a los datos en el espacio global.  Se crea una instancia de la variable `tile_static` para cada mosaico y todos los subprocesos del mosaico tienen acceso a la variable.  La ventaja fundamental del mosaico es que mejora el rendimiento debido al acceso `tile_static`.  
  
-   Puede llamar al método [tile\_barrier::wait](../Topic/tile_barrier::wait%20Method.md) para detener todos los subprocesos en un mosaico dentro una línea de código específica.  No se puede garantizar el orden en el que se van a ejecutar los subprocesos, solo se garantiza que todos los subprocesos de un mosaico se ​​detendrán al llamar a `tile_barrier::wait` antes de continuar la ejecución.  
  
-   Tiene acceso al índice del subproceso que concierne a la totalidad del objeto `array_view` y al índice que concierne al mosaico.  Al usar el índice local, se facilita la lectura y la depuración del código.  
  
 Para aprovechar las ventajas del mosaico en la multiplicación de matrices, el algoritmo debe dividir la matriz en mosaicos y luego copiar los datos de los mosaicos en variables `tile_static` para un acceso más rápido.  En este ejemplo, la matriz se divide en submatrices de igual tamaño.  El producto se obtiene multiplicando las submatrices.  En este ejemplo, las dos matrices y su producto son:  
  
 ![Matriz de 4 por 4](../../parallel/amp/media/campmatrixatiled.png "CampMatrixATiled")  
  
 ![Matriz de 4 por 4](../../parallel/amp/media/campmatrixbtiled.png "CampMatrixBTiled")  
  
 ![Matriz de 4 por 4](../../parallel/amp/media/campmatrixproducttiled.PNG "CampMatrixProductTiled")  
  
 Las matrices se dividen en cuatro matrices de 2 por 2, que se definen a continuación:  
  
 ![Matriz de 4 por 4 dividida en submatrices de 2 por 2](../../parallel/amp/media/campmatrixapartitioned.png "CampMatrixAPartitioned")  
  
 ![Matriz de 4 por 4 dividida en submatrices de 2 por 2](../../parallel/amp/media/campmatrixbpartitioned.png "CampMatrixBPartitioned")  
  
 El producto de A y B ahora se puede escribir y calcular tal y como se muestra a continuación:  
  
 ![Matriz de 4 por 4 dividida en submatrices de 2 por 2](../../parallel/amp/media/campmatrixproductpartitioned.png "CampMatrixProductPartitioned")  
  
 Dado que las matrices de `a` a `h` son matrices de 2x2, todos sus productos y sumas también son matrices de 2x2.  También se deduce que A\*B es una matriz de 4x4, tal y como se esperaba.  Para comprobar rápidamente el algoritmo, calcule el valor del elemento de la primera fila y la primera columna en el producto.  En el ejemplo, este sería el valor del elemento de la primera fila y la primera columna de `ae + bg`.  Solo tiene que calcular la primera columna y la primera fila de `ae` y `bg` para cada término.  El valor para `ae` es `1*1 + 2*5 = 11`.  El valor de `bg` es `3*1 + 4*5 = 23`.  El valor total es `11 + 23 = 34`, que es correcto.  
  
 Para implementar este algoritmo, el código:  
  
-   Usa un objeto `tiled_extent` en lugar de un objeto `extent` en la llamada a `parallel_for_each`.  
  
-   Usa un objeto `tiled_index` en lugar de un objeto `index` en la llamada a `parallel_for_each`.  
  
-   Crea variables `tile_static` para contener las submatrices.  
  
-   Usa el método `tile_barrier::wait` para detener los subprocesos de cálculo de los productos de las submatrices.  
  
### Para multiplicar usando AMP y el mosaico  
  
1.  En MatrixMultiply.cpp, agregue el siguiente código antes del método `main`.  
  
    ```cpp  
  
    void MultiplyWithTiling()  
    {  
        // The tile size is 2.  
        static const int TS = 2;  
  
        // The raw data.  
        int aMatrix[] =       { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };  
        int bMatrix[] =       { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };  
        int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };  
  
        // Create the array_view objects.  
        array_view<int, 2> a(4, 4, aMatrix);  
        array_view<int, 2> b(4, 4, bMatrix);  
        array_view<int, 2> product(4, 4, productMatrix);  
  
        // Call parallel_for_each by using  2x2 tiles.  
        parallel_for_each(product.extent.tile< TS, TS >(),  
            [=] (tiled_index< TS, TS> t_idx) restrict(amp)   
            {  
                // Get the location of the thread relative to the tile (row, col) and the entire array_view (rowGlobal, colGlobal).  
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
  
            for (int row = 0; row < 4; row++) {  
            for (int col = 0; col < 4; col++) {  
                // The results are available from both the product and productMatrix variables.  
                //std::cout << productMatrix[row*3 + col] << "  ";  
                std::cout << product(row, col) << "  ";  
            }  
            std::cout << "\n";  
        }  
  
    }  
  
    ```  
  
     Este ejemplo es significativamente diferente del ejemplo sin mosaico.  El código usa estos pasos conceptuales:  
  
    1.  Copia los elementos del mosaico \[0,0\] de `a` en `locA`.  Copia los elementos del mosaico \[0,0\] de `b` en `locB`.  Observe que `product` se dispone en mosaico, pero no así `a` y `b`.  Por lo tanto, debe usar índices globales para tener acceso a `a, b` y `product`.  La llamada a `tile_barrier::wait` es fundamental.  Detiene todos los subprocesos del mosaico hasta que se rellenen `locA` y `locB`.  
  
    2.  Multiplica `locA` y `locB` y coloca los resultados en `product`.  
  
    3.  Copia los elementos del mosaico \[0,1\] de `a` en `locA`.  Copia los elementos del mosaico \[1,0\] de `b` en `locB`.  
  
    4.  Multiplica `locA` y `locB` y los añade a los resultados que ya están en `product`.  
  
    5.  La multiplicación del mosaico \[0,0\] se ha completado.  
  
    6.  Repita los pasos para los otros cuatro mosaicos.  No existe indexación específica para los mosaicos, por lo que los subprocesos se pueden ejecutar en cualquier orden.  A medida que cada subproceso se ejecuta, se crean las variables `tile_static` para cada mosaico y la llamada a `tile_barrier::wait` controla el flujo del programa.  
  
    7.  Al examinar el algoritmo detenidamente, se observa que cada submatriz se carga en una memoria `tile_static` dos veces.  Esa transferencia de datos lleva bastante tiempo.  Sin embargo, una vez que los datos están en la memoria `tile_static`, el acceso a los datos es mucho más rápido.  Debido a que el cálculo de los productos requiere el acceso repetido a los valores de las submatrices, hay un aumento global del rendimiento.  Para cada algoritmo, se requiere práctica para encontrar el tamaño óptimo del algoritmo y del mosaico.  
  
         En los ejemplos que no son de AMP ni de mosaico, se tiene acceso a cada elemento de A y B cuatro veces desde la memoria global para calcular el producto.  En el ejemplo del mosaico, se tiene acceso a cada elemento dos veces desde la memoria global y cuatro veces desde la memoria `tile_static`.  Eso no supone una mejora significativa del rendimiento.  Sin embargo, si A y B fueran matrices de 1024x1024 y el tamaño del mosaico fuese 16, sí habría una mejora de rendimiento significativa.  En ese caso, cada elemento solo se copiaría en la memoria `tile_static` 16 veces y se tendría acceso a él 1024 veces desde la memoria `tile_static`.  
  
2.  Modifique el método principal para llamar al método `MultiplyWithTiling`, como se muestra a continuación.  
  
    ```cpp  
  
    void main() {  
        MultiplyWithOutAMP();  
        MultiplyWithAMP();  
        MultiplyWithTiling();  
        getchar();  
    }  
  
    ```  
  
3.  Elija el método abreviado de teclado Ctrl\+F5 para iniciar la depuración y comprobar que el resultado es correcto.  
  
4.  Elija la barra espaciadora para salir de la aplicación.  
  
## Vea también  
 [C\+\+ AMP \(C\+\+ Accelerated Massive Parallelism\)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [Tutorial: Depurar una aplicación de C\+\+ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)