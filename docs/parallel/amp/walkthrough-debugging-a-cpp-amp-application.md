---
title: 'Tutorial: Depuración C++ de una aplicación amp'
ms.date: 04/23/2019
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 0c9fb5588cfd44c83d8fe72c7c4aede0fedab672
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "69631596"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Tutorial: Depuración C++ de una aplicación amp

En este tema se muestra cómo depurar una C++ aplicación que usa el paralelismoC++ masivo acelerado (amp) para aprovechar las ventajas de la unidad de procesamiento de gráficos (GPU). Utiliza un programa de reducción paralela que suma una gran matriz de enteros. En este tutorial se muestran las tareas siguientes:

- Inicio del depurador de GPU.

- Inspeccionando los subprocesos de GPU en la ventana subprocesos de GPU.

- Usar la ventana **pilas paralelas** para observar simultáneamente las pilas de llamadas de varios subprocesos de GPU.

- Usar la ventana **inspección paralela** para inspeccionar los valores de una única expresión en varios subprocesos al mismo tiempo.

- Marcado, congelación, reanudación y agrupación de subprocesos de GPU.

- Ejecutar todos los subprocesos de un icono en una ubicación específica en el código.

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar este tutorial:

- Lea [ C++ la información general de amp](../../parallel/amp/cpp-amp-overview.md).

- Asegúrese de que los números de línea se muestran en el editor de texto. Para obtener más información, vea [Cómo: Muestra los números de línea en](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor)el editor.

- Asegúrese de que está ejecutando como mínimo Windows 8 o Windows Server 2012 para admitir la depuración en el emulador de software. 

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>Para crear el proyecto de ejemplo

Las instrucciones para crear un proyecto varían en función de la versión de Visual Studio que se use. Asegúrese de que tiene la versión correcta seleccionada en la parte superior izquierda de esta página.

::: moniker range="vs-2019"

### <a name="to-create-the-sample-project-in-visual-studio-2019"></a>Para crear el proyecto de ejemplo en Visual Studio 2019

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++** , establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Consola**. 

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**. En la siguiente página, escriba `AMPMapReduce` en el cuadro **Nombre** con el fin de especificar un nombre para el proyecto y, si lo desea, especifique la ubicación del proyecto.

   ![Asignar un nombre al proyecto](../../build/media/mathclient-project-name-2019.png "Asignar un nombre al proyecto")

1. Haga clic en el botón **Crear** para crear el proyecto de cliente.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-the-sample-project-in-visual-studio-2017-or-visual-studio-2015"></a>Para crear el proyecto de ejemplo en Visual Studio 2017 o Visual Studio 2015

1. Inicie Visual Studio.

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

1. En **instalado** en el panel plantillas, elija **Visual C++** .

1. Elija **aplicación de consola Win32**, `AMPMapReduce` escriba en el cuadro **nombre** y, a continuación, elija el botón **Aceptar** .

1. Elija el botón **Siguiente**.

1. Desactive la casilla **encabezado precompilado** y, a continuación, elija el botón **Finalizar** .

1. En **Explorador de soluciones**, elimine *stdafx. h*, *targetver. h*y *stdafx. cpp* del proyecto.

::: moniker-end

Siguiente:

8. Abra AMPMapReduce. cpp y reemplace su contenido por el código siguiente.

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

10. En **Explorador de soluciones**, abra el menú contextual de **AMPMapReduce**y, a continuación, elija **propiedades**.

11. En el cuadro de diálogo **páginas de propiedades** , en **propiedades de configuración**, elija encabezados de **C/C++**  > precompilados.

12. En la propiedad **encabezado precompilado** , seleccione **no usar encabezados precompilados**y, a continuación, elija el botón **Aceptar** .

13. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="debugging-the-cpu-code"></a>Depurar el código de CPU

En este procedimiento, usará el depurador local de Windows para asegurarse de que el código de CPU de esta aplicación es correcto. El segmento del código de CPU en esta aplicación que es especialmente interesante es el `for` bucle de la `reduction_sum_gpu_kernel` función. Controla la reducción paralela basada en el árbol que se ejecuta en la GPU.

### <a name="to-debug-the-cpu-code"></a>Para depurar el código de CPU

1. En **Explorador de soluciones**, abra el menú contextual de **AMPMapReduce**y, a continuación, elija **propiedades**.

2. En el cuadro de diálogo **páginas de propiedades** , en **propiedades de configuración**, elija **depuración**. Compruebe que el **depurador local de Windows** está seleccionado en la lista **depurador para iniciar** .

3. Vuelva al **Editor de código**.

4. Establezca puntos de interrupción en las líneas de código que se muestran en la siguiente ilustración (aproximadamente 67 línea 70).

   ![Puntos de interrupción de CPU](../../parallel/amp/media/campcpubreakpoints.png "Puntos de interrupción de CPU") <br/>
   Puntos de interrupción de CPU

5. En la barra de menús, seleccione **Depurar** > **Iniciar depuración**.

6. En la ventana **variables locales** , observe el valor `stride_size` de hasta que se alcance el punto de interrupción de la línea 70.

7. En la barra de menús, seleccione **Depurar** > **Detener depuración**.

## <a name="debugging-the-gpu-code"></a>Depuración del código de GPU

En esta sección se muestra cómo depurar el código de GPU, que es el `sum_kernel_tiled` código contenido en la función. El código de GPU calcula la suma de enteros para cada "bloque" en paralelo.

### <a name="to-debug-the-gpu-code"></a>Para depurar el código de GPU

1. En **Explorador de soluciones**, abra el menú contextual de **AMPMapReduce**y, a continuación, elija **propiedades**.

2. En el cuadro de diálogo **páginas de propiedades** , en **propiedades de configuración**, elija **depuración**.

3. En la lista **Depurador para iniciar**, seleccione **Depurador local de Windows**.

4. En la lista **tipo de depurador** , compruebe que está seleccionado **automático** .

    **Auto** es el valor predeterminado. Antes de Windows 10, la **GPU solo** es el valor necesario en lugar de **auto**.

5. Elija el botón **Aceptar** .

6. Establezca un punto de interrupción en la línea 30, tal como se muestra en la siguiente ilustración.

   ![Puntos de interrupción de GPU](../../parallel/amp/media/campgpubreakpoints.png "Puntos de interrupción de GPU") <br/>
   Punto de interrupción de GPU

7. En la barra de menús, seleccione **Depurar** > **Iniciar depuración**. Los puntos de interrupción en el código de CPU de las líneas 67 y 70 no se ejecutan durante la depuración de la GPU porque esas líneas de código se ejecutan en la CPU.

### <a name="to-use-the-gpu-threads-window"></a>Para usar la ventana subprocesos de GPU

1. Para abrir la ventana **subprocesos de GPU** , en la barra de menús, elija **depurar** > **subprocesos de GPU**de**Windows** > .

   Puede inspeccionar el estado de los subprocesos de GPU en la ventana **subprocesos de GPU** que aparece.

2. Acople la ventana **subprocesos de GPU** en la parte inferior de Visual Studio. Elija el botón **expandir el conmutador de subproceso** para mostrar los cuadros de texto de icono y de subproceso. La ventana **subprocesos de GPU** muestra el número total de subprocesos de GPU activos y bloqueados, tal como se muestra en la siguiente ilustración.

   ![Ventana subprocesos de GPU con 4 subprocesos activos](../../parallel/amp/media/campc.png "Ventana subprocesos de GPU con 4 subprocesos activos") <br/>
   Ventana Subprocesos de GPU

   Hay 313 mosaicos asignados para este cálculo. Cada mosaico contiene 32 subprocesos. Dado que la depuración de GPU local se produce en un emulador de software, hay cuatro subprocesos de GPU activos. Los cuatro subprocesos ejecutan las instrucciones simultáneamente y después se mueven juntos a la siguiente instrucción.

   En la ventana **subprocesos de GPU** , hay cuatro subprocesos de GPU activos y 28 subprocesos de GPU bloqueados en la instrucción [tile_barrier:: wait](reference/tile-barrier-class.md#wait) definida en la línea 21 (`t_idx.barrier.wait();`). Todos los subprocesos de GPU 32 pertenecen al `tile[0]`primer icono,. Una flecha apunta a la fila que incluye el subproceso actual. Para cambiar a otro subproceso, use uno de los métodos siguientes:

    - En la fila del subproceso al que se va a cambiar en la ventana **subprocesos de GPU** , abra el menú contextual y elija **cambiar a subproceso**. Si la fila representa más de un subproceso, cambiará al primer subproceso según las coordenadas del subproceso.

    - Escriba los valores de mosaico y de subproceso del subproceso en los cuadros de texto correspondientes y, a continuación, elija el botón **cambiar de subproceso** .

   La ventana **pila de llamadas** muestra la pila de llamadas del subproceso de GPU actual.

### <a name="to-use-the-parallel-stacks-window"></a>Para usar la ventana pilas paralelas

1. Para abrir la ventana **pilas paralelas** , en la barra de menús, elija **depurar** > **pilas paralelas**de**Windows** > .

   Puede usar la ventana **pilas paralelas** para inspeccionar simultáneamente los marcos de pila de varios subprocesos de GPU.

2. Acople la ventana **pilas paralelas** en la parte inferior de Visual Studio.

3. Asegúrese de que **subprocesos** está seleccionado en la lista de la esquina superior izquierda. En la siguiente ilustración, la ventana **pilas paralelas** muestra una vista centrada en la pila de llamadas de los subprocesos de GPU que vio en la ventana **subprocesos de GPU** .

   ![Ventana pilas paralelas con 4 subprocesos activos](../../parallel/amp/media/campd.png "Ventana pilas paralelas con 4 subprocesos activos") <br/>
   Ventana Pilas paralelas

   32 los subprocesos pasaron de `_kernel_stub` a la instrucción lambda en la `parallel_for_each` llamada de función `sum_kernel_tiled` y, a continuación, a la función, donde se produce la reducción paralela. 28 de los subprocesos 32 han progresado hasta la instrucción [tile_barrier:: wait](reference/tile-barrier-class.md#wait) y siguen bloqueados en la línea 22, mientras que los otros 4 subprocesos permanecen activos en la función de la `sum_kernel_tiled` línea 30.

   Puede inspeccionar las propiedades de un subproceso de GPU que están disponibles en la ventana **subprocesos de GPU** en la información sobre la información enriquecida de la ventana **pilas paralelas** . Para ello, coloque el puntero del mouse en el marco de pila de **sum_kernel_tiled**. En la ilustración siguiente se muestra la información sobre la información.

   ![Información sobre la ventana pilas paralelas](../../parallel/amp/media/campe.png "Información sobre la ventana pilas paralelas") <br/>
   Información sobre los subprocesos de GPU

   Para obtener más información acerca de la ventana **pilas paralelas** , vea [usar la ventana pilas paralelas](/visualstudio/debugger/using-the-parallel-stacks-window).

### <a name="to-use-the-parallel-watch-window"></a>Para usar la ventana Inspección paralela

1. Para abrir la ventana **inspección paralela** , en la barra de menús, elija **depurar** > **Windows** > **Parallel Watch** > en paralelo inspección**1**.

   Puede usar la ventana **inspección paralela** para inspeccionar los valores de una expresión entre varios subprocesos.

2. Acople la ventana **inspección paralela 1** a la parte inferior de Visual Studio. Hay 32 filas en la tabla de la ventana **inspección paralela** . Cada corresponde a un subproceso de GPU que aparecía en la ventana subprocesos de GPU y en la ventana **pilas paralelas** . Ahora, puede escribir expresiones cuyos valores desee inspeccionar en todos los subprocesos de GPU 32.

3. Seleccione el encabezado de columna **Agregar inspección** , `localIdx`escriba y, a continuación, elija la tecla **entrar** .

4. Seleccione de nuevo el encabezado **Agregar** columna de inspección `globalIdx`, escriba y, a continuación, elija la tecla **entrar** .

5. Seleccione de nuevo el encabezado **Agregar** columna de inspección `localA[localIdx[0]]`, escriba y, a continuación, elija la tecla **entrar** .

   Puede ordenar por una expresión especificada seleccionando su correspondiente encabezado de columna.

   Seleccione el encabezado de columna **locala [localIdx [0]]** para ordenar la columna. En la ilustración siguiente se muestran los resultados de la ordenación por **locala [localIdx [0]]** .

   ![Ventana Inspección paralelas con resultados ordenados](../../parallel/amp/media/campf.png "Ventana Inspección paralelas con resultados ordenados") <br/>
   Resultados de la ordenación

   Puede exportar el contenido de la ventana **inspección paralela** a Excel eligiendo el botón **Excel** y eligiendo **abrir en Excel**. Si tiene Excel instalado en el equipo de desarrollo, se abre una hoja de cálculo de Excel que incluye el contenido.

6. En la esquina superior derecha de la ventana **inspección paralela** , hay un control de filtro que puede usar para filtrar el contenido mediante Expresiones booleanas. Escriba `localA[localIdx[0]] > 20000` en el cuadro de texto control de filtro y elija la tecla **entrar** .

   La ventana contiene ahora solo los subprocesos `localA[localIdx[0]]` en los que el valor es mayor que 20000. El contenido todavía está ordenado por la `localA[localIdx[0]]` columna, que es la acción de ordenación que realizó anteriormente.

## <a name="flagging-gpu-threads"></a>Marcar subprocesos de GPU

Puede marcar subprocesos de GPU específicos marcándolos en la ventana **subprocesos de GPU** , la ventana **inspección paralela** o la información sobre información en la ventana **pilas paralelas** . Si una fila de la ventana subprocesos de GPU contiene más de un subproceso, al marcar esa fila se marcan todos los subprocesos incluidos en la fila.

### <a name="to-flag-gpu-threads"></a>Para marcar subprocesos de GPU

1. Seleccione el encabezado de columna **[subproceso]** en la ventana **inspección paralela 1** para ordenar por índice de icono y por índice de subproceso.

2. En la barra de menús, elija **depurar** > **continuar**, que hace que los cuatro subprocesos que estaban activos progresen a la siguiente barrera (definida en la línea 32 de AMPMapReduce. cpp).

3. Elija el símbolo de marca en el lado izquierdo de la fila que contiene los cuatro subprocesos que ahora están activos.

   En la ilustración siguiente se muestran los cuatro subprocesos marcados activos en la ventana **subprocesos de GPU** .

   ![Ventana subprocesos de GPU con subprocesos marcados](../../parallel/amp/media/campg.png "Ventana subprocesos de GPU con subprocesos marcados") <br/>
   Subprocesos activos en la ventana Subprocesos de GPU

   La ventana **inspección paralela** y la información sobre la información de la ventana **pilas paralelas** indican los subprocesos marcados.

4. Si desea centrarse en los cuatro subprocesos marcados, puede optar por mostrar, en las ventanas **subprocesos de GPU**, **inspección paralela**y **pilas paralelas** , solo los subprocesos marcados.

   Elija el botón **Mostrar solo marcado** en cualquiera de las ventanas o en la barra de herramientas **Ubicación de depuración** . En la ilustración siguiente se muestra el botón **Mostrar solo marcado** en la barra de herramientas **Ubicación de depuración** .

   ![Barra de herramientas ubicación de depuración con el icono Mostrar solo marcado](../../parallel/amp/media/camph.png "Barra de herramientas ubicación de depuración con el icono Mostrar solo marcado") <br/>
   Botón **Mostrar solo marcas**

   Ahora, las ventanas **subprocesos de GPU**, **inspección paralela**y **pilas paralelas** muestran solo los subprocesos marcados.

## <a name="freezing-and-thawing-gpu-threads"></a>Inmovilizar y reanudar subprocesos de GPU

Puede inmovilizar (suspender) e reanudar (reanudar) los subprocesos de GPU en la ventana **subprocesos de GPU** o en la ventana **inspección paralela** . Puede inmovilizar y reanudar los subprocesos de CPU de la misma manera; para obtener información, [consulte Cómo: Use la ventana](/visualstudio/debugger/how-to-use-the-threads-window)subprocesos.

### <a name="to-freeze-and-thaw-gpu-threads"></a>Para inmovilizar y reanudar subprocesos de GPU

1. Elija el botón **Mostrar solo marcado** para mostrar todos los subprocesos.

2. En la barra de menús, elija **depurar** > **continuar**.

3. Abra el menú contextual de la fila activa y, a continuación, elija **inmovilizar**.

   La siguiente ilustración de la ventana **subprocesos de GPU** muestra que los cuatro subprocesos están inmovilizados.

   ![Subprocesos de GPU ventanas con subprocesos inmovilizados](../../parallel/amp/media/campk.png "Subprocesos de GPU ventanas con subprocesos inmovilizados") <br/>
   Subprocesos inmovilizados en la ventana **subprocesos de GPU**

   Del mismo modo, la ventana **inspección paralela** muestra que los cuatro subprocesos están inmovilizados.

4. En la barra de menús, elija **depurar** > **continuar** para permitir que los siguientes cuatro subprocesos de GPU progresan más allá de la barrera de la línea 22 y alcanzar el punto de interrupción en la línea 30. La ventana **subprocesos de GPU** muestra que los cuatro subprocesos previamente inmovilizados permanecen inmovilizados y en estado activo.

5. En la barra de menús, elija **depurar**, **continuar**.

6. En la ventana **inspección paralela** , también se pueden reanudar los subprocesos individuales o varios de GPU.

### <a name="to-group-gpu-threads"></a>Para agrupar subprocesos de GPU

1. En el menú contextual de uno de los subprocesos de la ventana **subprocesos de GPU** , elija **Agrupar por**y **Dirección**.

   Los subprocesos de la ventana **subprocesos de GPU** se agrupan por dirección. La dirección corresponde a la instrucción del desensamblado donde se encuentra cada grupo de subprocesos. 24 subprocesos se encuentran en la línea 22, donde se ejecuta el [método tile_barrier:: wait](reference/tile-barrier-class.md#wait) . 12 subprocesos se encuentran en la instrucción de la barrera de la línea 32. Se marcan cuatro de estos subprocesos. Ocho subprocesos se encuentran en el punto de interrupción de la línea 30. Cuatro de estos subprocesos están inmovilizados. En la ilustración siguiente se muestran los subprocesos agrupados en la ventana **subprocesos de GPU** .

   ![Ventana subprocesos de GPU con subprocesos agrupados por dirección](../../parallel/amp/media/campl.png "Ventana subprocesos de GPU con subprocesos agrupados por dirección") <br/>
   Subprocesos agrupados en la ventana **subprocesos de GPU**

2. También puede realizar la operación **Agrupar por** abriendo el menú contextual de la cuadrícula de datos de la ventana **inspección paralela** , eligiendo **Agrupar por**y, a continuación, eligiendo el elemento de menú que corresponde a cómo desea agrupar los subprocesos.

## <a name="running-all-threads-to-a-specific-location-in-code"></a>Ejecutar todos los subprocesos en una ubicación específica en el código

Todos los subprocesos de un mosaico determinado se ejecutan en la línea que contiene el cursor mediante **ejecutar el icono actual hasta el cursor**.

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>Para ejecutar todos los subprocesos en la ubicación marcada por el cursor

1. En el menú contextual para los subprocesos inmovilizados, elija **reanudar**.

2. En el **Editor de código**, coloque el cursor en la línea 30.

3. En el menú contextual del **Editor de código**, elija **ejecutar el icono actual hasta el cursor**.

   Los 24 subprocesos previamente bloqueados en la barrera de la línea 21 han progresado a la línea 32. Esto se muestra en la ventana **subprocesos de GPU** .

## <a name="see-also"></a>Vea también

[Información general sobre C++ AMP](../../parallel/amp/cpp-amp-overview.md)<br/>
[Depurar código de GPU](/visualstudio/debugger/debugging-gpu-code)<br/>
[Cómo: usar la ventana Subprocesos de GPU](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[Cómo: Uso de la ventana Inspección paralela](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[Analizar C++ código de amp con el visualizador de simultaneidad](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
