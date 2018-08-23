---
title: 'Tutorial: Depurar una aplicación C++ AMP | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6bec76b407221fb9029662ba982a10edc4ca9c77
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604925"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Tutorial: Depurar una aplicación de C++ AMP
En este tema se muestra cómo depurar una aplicación que usa C++ Accelerated Massive Parallelism (C++ AMP) para aprovechar las ventajas de la unidad de procesamiento de gráficos (GPU). Usa un programa de reducción de paralelo que realiza la suma de una matriz de enteros grande. En este tutorial se muestran las tareas siguientes:  
  
- Iniciando al depurador de GPU.  
  
- Inspeccionar subprocesos de GPU en la ventana subprocesos de GPU.  
  
- Mediante el **pilas paralelas** ventana simultáneamente observar las pilas de llamadas de varios subprocesos GPU.  
  
- Mediante el **inspección paralela** ventana para inspeccionar los valores de una sola expresión en varios subprocesos al mismo tiempo.  
  
- Al marcar, congelación, reanudación y agrupación de subprocesos de GPU.  
  
- Ejecutar todos los subprocesos de un icono en una ubicación específica en el código.  
  
## <a name="prerequisites"></a>Requisitos previos  
 
Antes de empezar este tutorial:  
  
- Lectura [Introducción a C++ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
- Asegúrese de que esa línea números se muestran en el editor de texto. Para obtener más información, consulte [Cómo: mostrar los números de línea en el Editor de](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).  
  
- Asegúrese de que está ejecutando Windows 8 o Windows Server 2012 para admitir la depuración en el emulador de software.  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### <a name="to-create-the-sample-project"></a>Para crear el proyecto de ejemplo  
  
1. Inicie Visual Studio.  
  
2. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.  
  
3. En **instalado** en el panel Plantillas, elija **Visual C++**.  
  
4. Elija **aplicación de consola Win32**, tipo `AMPMapReduce` en el **nombre** cuadro y, a continuación, elija el **Aceptar** botón.  
  
5. Elija el botón **Siguiente**.  
  
6. Desactive el **encabezado precompilado** casilla de verificación y, a continuación, elija el **finalizar** botón.  
  
7. En **el Explorador de soluciones**, elimine stdafx.h, targetver.h y stdafx.cpp del proyecto.  
  
8. Abra AMPMapReduce.cpp y reemplace su contenido con el código siguiente.  
  
 ```cpp  
    // AMPMapReduce.cpp defines the entry point for the program.  
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.   
  
    #include <stdio.h>  
    #include <tchar.h>  
    #include <amp.h>  
  
    const int BLOCK_DIM = 32;  
  
    using namespace concurrency;  
  
    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)  
    {  
        tile_static int localA[BLOCK_DIM];  
  
        index<1> globalIdx = t_idx.global * stride_size;  
        index<1> localIdx = t_idx.local;  
  
        localA[localIdx[0]] =  A[globalIdx];  
  
        t_idx.barrier.wait();  
  
        // Aggregate all elements in one tile into the first element.  
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)   
        {  
            if (localIdx[0] < i)   
            {  
  
                localA[localIdx[0]] += localA[localIdx[0] + i];  
            }  
  
            t_idx.barrier.wait();  
        }  
  
        if (localIdx[0] == 0)  
        {  
            A[globalIdx] = localA[0];  
        }  
    }  
  
    int size_after_padding(int n)  
    {  
        // The extent might have to be slightly bigger than num_stride to   
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.  
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)  
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;  
    }  
  
    int reduction_sum_gpu_kernel(array<int, 1> input)   
    {  
        int len = input.extent[0];  
  
        //Tree-based reduction control that uses the CPU.  
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)   
        {  
            // Number of useful values in the array, given the current  
            // stride size.  
            int num_strides = len / stride_size;    
  
            extent<1> e(size_after_padding(num_strides));  
  
            // The sum kernel that uses the GPU.  
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)  
            {  
                sum_kernel_tiled(idx, input, stride_size);  
            });  
        }  
  
        array_view<int, 1> output = input.section(extent<1>(1));  
        return output[0];  
    }  
  
    int cpu_sum(const std::vector<int> &arr) {  
        int sum = 0;  
        for (size_t i = 0; i < arr.size(); i++) {  
            sum += arr[i];  
        }  
        return sum;  
    }  
  
    std::vector<int> rand_vector(unsigned int size) {  
        srand(2011);  
  
        std::vector<int> vec(size);  
        for (size_t i = 0; i < size; i++) {  
            vec[i] = rand();  
        }  
        return vec;  
    }  
  
    array<int, 1> vector_to_array(const std::vector<int> &vec) {  
        array<int, 1> arr(vec.size());  
        copy(vec.begin(), vec.end(), arr);  
        return arr;  
    }  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
        std::vector<int> vec = rand_vector(10000);  
        array<int, 1> arr = vector_to_array(vec);  
  
        int expected = cpu_sum(vec);  
        int actual = reduction_sum_gpu_kernel(arr);  
  
        bool passed = (expected == actual);  
        if (!passed) {  
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);  
        }  
        printf("sum: %s\n", passed  "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
 ```  
  
9. En la barra de menús, pulse **Archivo** > **Guardar todo**.  
  
10. En **el Explorador de soluciones**, abra el menú contextual para **AMPMapReduce**y, a continuación, elija **propiedades**.  
  
11. En el **páginas de propiedades** cuadro de diálogo **propiedades de configuración**, elija **C o C++** > **encabezados precompilados**.  
  
12. Para el **encabezado precompilado** propiedad, seleccione **no utilizar encabezados precompilados**y, a continuación, elija el **Aceptar** botón.  
  
13. En la barra de menús, elija **Compilar** > **Compilar solución**.  
  
## <a name="debugging-the-cpu-code"></a>Depurar el código de la CPU  
 
En este procedimiento, usará al depurador de Windows Local para asegurarse de que el código de la CPU en esta aplicación es correcto. El segmento de un código de la CPU en la aplicación es especialmente interesante es la `for` bucle en el `reduction_sum_gpu_kernel` función. Controla la reducción paralela basados en árbol que se ejecuta en la GPU.  
  
### <a name="to-debug-the-cpu-code"></a>Para depurar el código de la CPU  
  
1. En **el Explorador de soluciones**, abra el menú contextual para **AMPMapReduce**y, a continuación, elija **propiedades**.  
  
2. En el **páginas de propiedades** cuadro de diálogo **propiedades de configuración**, elija **depuración**. Compruebe que **depurador Local de Windows** está seleccionado en el **depurador para iniciar** lista.  
  
3. Vuelva a la **Editor de código**.  
  
4. Establecer puntos de interrupción en las líneas de código que se muestra en la siguiente ilustración (aproximadamente líneas 67 en línea 70).  
  
     ![Los puntos de interrupción de CPU](../../parallel/amp/media/campcpubreakpoints.png "campcpubreakpoints")  
Puntos de interrupción de CPU  
  
5. En la barra de menús, seleccione **Depurar** > **Iniciar depuración**.  
  
6. En el **variables locales** ventana, observe el valor para `stride_size` hasta que se alcanza el punto de interrupción en la línea 70.  
  
7. En la barra de menús, seleccione **Depurar** > **Detener depuración**.  
  
## <a name="debugging-the-gpu-code"></a>Depurar el código de GPU  
 
En esta sección se muestra cómo depurar el código GPU, que es el código contenido en el `sum_kernel_tiled` función. El código GPU calcula la suma de enteros para cada "bloque" en paralelo.  
  
### <a name="to-debug-the-gpu-code"></a>Para depurar el código GPU  
  
1. En **el Explorador de soluciones**, abra el menú contextual para **AMPMapReduce**y, a continuación, elija **propiedades**.  
  
2. En el **páginas de propiedades** cuadro de diálogo **propiedades de configuración**, elija **depuración**.  
  
3. En el **depurador para iniciar** lista, seleccione **depurador Local de Windows**.  
  
4. En el **tipo de depurador** lista, compruebe que **automática** está seleccionada.

    **Auto** es el valor predeterminado. Antes de Windows 10, **solo GPU** es el valor necesario en lugar de **automática**.
  
5. Elija el botón **Aceptar** .  
  
6. Establecer un punto de interrupción en la línea 30, tal como se muestra en la siguiente ilustración.  
  
     ![Los puntos de interrupción GPU](../../parallel/amp/media/campgpubreakpoints.png "campgpubreakpoints")  
Punto de interrupción GPU  
  
7. En la barra de menús, seleccione **Depurar** > **Iniciar depuración**. Los puntos de interrupción en el código de la CPU en las líneas 67 y 70 no se ejecutan durante la depuración porque esas líneas de código se ejecutan en la CPU de GPU.  
  
### <a name="to-use-the-gpu-threads-window"></a>Para utilizar la ventana subprocesos de GPU  
  
1. Para abrir el **subprocesos de GPU** ventana, en la barra de menús, elija **depurar** > **Windows** > **subprocesos de GPU**.  
  
     Puede inspeccionar el estado de la GPU de subprocesos en el **subprocesos de GPU** ventana que aparece.  
  
2. Acoplar el **subprocesos de GPU** ventana en la parte inferior de Visual Studio. Elija la **expanda subproceso conmutador** botón para mostrar los cuadros de texto de mosaico y subproceso. El **subprocesos de GPU** ventana muestra el número total de subprocesos de GPU activos y bloqueados, tal como se muestra en la siguiente ilustración.  
  
     ![Ventana subprocesos de GPU con 4 subprocesos activos](../../parallel/amp/media/campc.png "campc")  
Ventana Subprocesos de GPU  
  
     Hay 313 iconos asignados para este cálculo. Cada mosaico contiene 32 subprocesos. Dado que la depuración de GPU local se produce en un emulador de software, hay cuatro subprocesos GPU activos. Los cuatro subprocesos ejecutan al mismo tiempo las instrucciones y, a continuación, pase juntos a la siguiente instrucción.  
  
     En el **subprocesos de GPU** ventana, hay cuatro subprocesos de GPU activa y bloquean el 28 subprocesos de GPU en el [tile_barrier:: wait](reference/tile-barrier-class.md#wait) instrucción definida en acerca de la línea 21 (`t_idx.barrier.wait();`). Todos los subprocesos GPU 32 pertenecen al primer icono, `tile[0]`. Una flecha apunta a la fila que incluye el subproceso actual. Para cambiar a un subproceso diferente, use uno de los métodos siguientes:  

    - En la fila para el subproceso cambiar a la **subprocesos de GPU** ventana, abra el menú contextual y elija **cambiar a subproceso**. Si la fila representa más de un subproceso, cambiará al primer subproceso según las coordenadas de subproceso.  
  
    - Escriba los valores de mosaico y el subproceso del subproceso en los cuadros de texto correspondiente y, a continuación, elija el **conmutador subproceso** botón.  
  
     El **pila de llamadas** ventana muestra la pila de llamadas del subproceso actual de la GPU.  
  
### <a name="to-use-the-parallel-stacks-window"></a>Para usar la ventana Pilas paralelas  
  
1. Para abrir el **pilas paralelas** ventana, en la barra de menús, elija **depurar** > **Windows** > **pilas paralelas**.  
  
     Puede usar el **pilas paralelas** ventana simultáneamente inspeccionar los marcos de pila de varios subprocesos GPU.  
  
2. Acoplar el **pilas paralelas** ventana en la parte inferior de Visual Studio.  
  
3. Asegúrese de que **subprocesos** está seleccionado en la lista en la esquina superior izquierda. En la siguiente ilustración, el **pilas paralelas** ventana muestra una vista centrada de la pila de llamadas de los subprocesos GPU que vio en el **subprocesos de GPU** ventana.  
  
     ![Ventana Pilas paralelas con 4 subprocesos activos](../../parallel/amp/media/campd.png "campd")  
Ventana Pilas paralelas  
  
     32 subprocesos pasaron de `_kernel_stub` la expresión lambda en el `parallel_for_each` llamada de función y, a continuación, en el `sum_kernel_tiled` función, donde se produce la reducción en paralelo. 28 fuera de los 32 subprocesos han progresado en los [tile_barrier:: wait](reference/tile-barrier-class.md#wait) instrucción y permanecerá bloqueado en la línea 22, mientras que los 4 subprocesos permanecen activas en el `sum_kernel_tiled` función en la línea 30.  

     Puede inspeccionar las propiedades de un subproceso GPU que están disponibles en el **subprocesos de GPU** ventana en la información sobre datos enriquecido de los **pilas paralelas** ventana. Para ello, coloque el puntero del mouse sobre el marco de pila de **sum_kernel_tiled**. La siguiente ilustración muestra la información sobre datos.  
  
     ![Información sobre datos de la ventana Pilas paralelas](../../parallel/amp/media/campe.png "campe")  
Información sobre datos de subproceso de GPU  
  
     Para obtener más información sobre la **pilas paralelas** ventana, consulte [mediante la ventana Pilas paralelas](/visualstudio/debugger/using-the-parallel-stacks-window).  
  
### <a name="to-use-the-parallel-watch-window"></a>Para usar la ventana Inspección paralela  
  
1. Para abrir el **inspección paralela** ventana, en la barra de menús, elija **depurar** > **Windows** > **inspección paralela**  >  **Inspección 1 paralela**.  
  
     Puede usar el **inspección paralela** ventana para inspeccionar los valores de una expresión entre varios subprocesos.  
  
2. Acoplar el **inspección paralela 1** ventana a la parte inferior de Visual Studio. Hay 32 filas en la tabla de la **inspección paralela** ventana. Cada uno corresponde a un subproceso GPU que apareció en la ventana subprocesos de GPU y la **pilas paralelas** ventana. Ahora, puede escribir expresiones cuyos valores desea inspeccionar en todos los 32 subprocesos GPU.  
  
3. Seleccione el **Agregar inspección** encabezado de columna, escriba `localIdx`y, a continuación, elija el **ENTRAR** clave.  
  
4. Seleccione el **Agregar inspección** nuevo encabezado de columna, escriba `globalIdx`y, a continuación, elija el **ENTRAR** clave.  
  
5. Seleccione el **Agregar inspección** nuevo encabezado de columna, escriba `localA[localIdx[0]]`y, a continuación, elija el **ENTRAR** clave.  
  
     Puede ordenar por una expresión especificada, seleccione el encabezado de columna correspondiente.  
  
     Seleccione el **localA [localIdx [0]]** encabezado de columna para ordenar la columna. La siguiente ilustración muestra los resultados de ordenación por **localA [localIdx [0]]**.  
  
     ![Ventana Inspección paralela con resultados ordenados](../../parallel/amp/media/campf.png "campf")  
 Resultados de la ordenación  
  
     Puede exportar el contenido de la **inspección paralela** ventana de Excel eligiendo el **Excel** botón y, a continuación, elija **abrir en Excel**. Si tiene Excel instalado en el equipo de desarrollo, se abrirá una hoja de cálculo de Excel que contiene el contenido.  
  
6. En la esquina superior derecha de la **inspección paralela** ventana, hay un control de filtro que puede usar para filtrar el contenido mediante el uso de expresiones booleanas. ENTRAR `localA[localIdx[0]] > 20000` en el texto del control de filtro y, a continuación, elija el **ENTRAR** clave.  
  
     La ventana ahora contiene sólo los subprocesos en los que el `localA[localIdx[0]]` valor es mayor de 20 000. El contenido todavía está ordenado por la `localA[localIdx[0]]` columna, que es la acción de ordenación que realizó anteriormente.  
  
## <a name="flagging-gpu-threads"></a>Marcar los subprocesos de GPU  
 
Puede marcar los subprocesos GPU específicos marcando en el **subprocesos de GPU** ventana, el **inspección paralela** ventana o la información sobre datos en el **pilas paralelas** ventana. Si una fila en la ventana subprocesos de GPU contiene más de un subproceso, al marcar esa fila marcas de todos los subprocesos que se encuentran en la fila.  
  
### <a name="to-flag-gpu-threads"></a>Para marcar subprocesos GPU  
  
1. Seleccione el **[subproceso]** encabezado de columna en la **inspección paralela 1** ventana para ordenar por índice de icono y el índice de subproceso.  
  
2. En la barra de menús, elija **depurar** > **continuar**, que hace que los cuatro subprocesos que estaban activas al progreso a la barrera siguiente (definida en la línea 32 de AMPMapReduce.cpp).  
  
3. Elija el símbolo de marca en el lado izquierdo de la fila que contiene los cuatro subprocesos que ahora están activos.  
  
     La siguiente ilustración muestra los cuatro subprocesos marcados activos en el **subprocesos de GPU** ventana.  
  
     ![Ventana subprocesos de GPU con subprocesos marcados](../../parallel/amp/media/campg.png "campg")  
Subprocesos activos en la ventana Subprocesos de GPU  
  
     El **inspección paralela** ventana y la información sobre datos de la **pilas paralelas** ventana ambos indicar los subprocesos marcados.  
  
4. Si desea centrarse en los cuatro subprocesos que indican, puede elegir mostrar, en el **subprocesos de GPU**, **inspección paralela**, y **pilas paralelas** windows, solo los marcados subprocesos.  
  
     Elija la **mostrar solo marcados** botón en cualquiera de las ventanas o en el **ubicación de depuración** barra de herramientas. La siguiente ilustración muestra el **mostrar solo marcados** situado en la **ubicación de depuración** barra de herramientas.  
  
     ![Barra de herramientas de ubicación con el icono Mostrar marcadas únicamente depuración](../../parallel/amp/media/camph.png "camph")  
**Mostrar solo subprocesos marcados** botón  
  
     Ahora el **subprocesos de GPU**, **inspección paralela**, y **pilas paralelas** ventanas muestran solo los subprocesos marcados.  
  
## <a name="freezing-and-thawing-gpu-threads"></a>Inmovilizar y reanudar subprocesos de GPU  
 
Puede inmovilizar (suspender) y retomar (Reanudar) GPU subprocesos desde la **subprocesos de GPU** ventana o el **inspección paralela** ventana. Puede inmovilizar y descongelar subprocesos de CPU de la misma manera; Para obtener información, consulte [Cómo: utilizar la ventana subprocesos](/visualstudio/debugger/how-to-use-the-threads-window).  
  
### <a name="to-freeze-and-thaw-gpu-threads"></a>Para inmovilizar y descongelar subprocesos de GPU  
  
1. Elija la **mostrar solo marcados** botón para mostrar todos los subprocesos.  
  
2. En la barra de menús, elija **depurar** > **continuar**.  
  
3. Abra el menú contextual de la fila activa y, a continuación, elija **inmovilizar**.  
  
     La siguiente ilustración de la **subprocesos de GPU** ventana muestra que todos los cuatro subprocesos están inmovilizados.  
  
     ![Windows de subprocesos de GPU que muestra los subprocesos inmovilizados](../../parallel/amp/media/campk.png "campk")  
Inmovilizar subprocesos la **subprocesos de GPU** ventana  
  
     De forma similar, el **inspección paralela** ventana muestra que todos los cuatro subprocesos están inmovilizados.  
  
4. En la barra de menús, elija **depurar** > **continuar** para permitir que los siguientes cuatro subprocesos de GPU para avanza más allá de la barrera en la línea 22 y alcanzar el punto de interrupción en la línea 30. El **subprocesos de GPU** ventana muestra que los cuatro subprocesos inmovilizados previamente permanecen inmovilizado y en el estado activo.  
  
5. En la barra de menús, elija **depurar**, **continuar**.  
  
6. Desde el **inspección paralela** ventana, también puede reanudar individuales o varios subprocesos GPU.  
  
### <a name="to-group-gpu-threads"></a>Para agrupar los subprocesos GPU  
  
1. En el menú contextual para uno de los subprocesos en la **subprocesos de GPU** ventana, elija **Group By**, **dirección**.  
  
     Los subprocesos en la **subprocesos de GPU** ventana se agrupan por dirección. La dirección corresponde a la instrucción en el desensamblado donde se encuentra cada grupo de subprocesos. 24 subprocesos que están en la línea 22 donde el [tile_barrier:: Wait (método)](reference/tile-barrier-class.md#wait) se ejecuta. 12 subprocesos están en la instrucción de la barrera en la línea 32. Cuatro de estos subprocesos están marcado. Ocho subprocesos están en el punto de interrupción en la línea 30. Cuatro de estos subprocesos están congelado. La siguiente ilustración muestra los subprocesos agrupados en el **subprocesos de GPU** ventana.  

     ![Ventana subprocesos de GPU con subprocesos agrupados por dirección](../../parallel/amp/media/campl.png "campl")  
Agrupar subprocesos en la **subprocesos de GPU** ventana  
  
2. También puede realizar la **Group By** operación abriendo el menú contextual de la cuadrícula de datos de la **inspección paralela** ventana, elija **Group By**y, a continuación, elija el menú elemento que corresponde a cómo desea agrupar los subprocesos.  
  
## <a name="running-all-threads-to-a-specific-location-in-code"></a>Todos los subprocesos en ejecución en una ubicación específica en el código  
 
Ejecute todos los subprocesos en un icono determinado para la línea que contiene el cursor mediante **ejecutar actual icono hasta el Cursor**.  
  
### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Para ejecutar todos los subprocesos en la ubicación marcada por el cursor  
  
1. En el menú contextual para los subprocesos inmovilizados, elija **reanudar**.  
  
2. En el **Editor de código**, coloque el cursor en la línea 30.  
  
3. En el menú contextual para el **Editor de código**, elija **ejecutar Tile actual a Cursor**.  
  
     Los 24 subprocesos que se bloquearon anteriormente en la barrera en la línea 21 han progresado en línea 32. Esto se muestra en el **subprocesos de GPU** ventana.  
  
## <a name="see-also"></a>Vea también  
 
[Introducción a C++ AMP](../../parallel/amp/cpp-amp-overview.md)   
[Depurar código de GPU](/visualstudio/debugger/debugging-gpu-code)   
[Cómo: utilizar la ventana de subprocesos GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)   
[Cómo: utilizar la ventana Inspección paralela](/visualstudio/debugger/how-to-use-the-parallel-watch-window)   
[Análisis de código de AMP de C++ con el visualizador de simultaneidad](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)