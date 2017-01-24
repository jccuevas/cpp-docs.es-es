---
title: "Tutorial: Depurar una aplicaci&#243;n de C++ AMP | Microsoft Docs"
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
helpviewer_keywords: 
  - "depurar, C++ Accelerated Massive Parallelism"
  - "C++ AMP, depurar"
  - "C++ Accelerated Massive Parallelism, depurar"
  - "depurar, C++ AMP"
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
caps.latest.revision: 35
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Depurar una aplicaci&#243;n de C++ AMP
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema muestra cómo depurar una aplicación que utiliza C\+\+ Accelerated Massive Parallelism \(C\+\+ AMP\) para aprovechar la unidad de procesamiento gráfico \(GPU\).  Utiliza un programa de reducción en paralelo que sintetiza una gran matriz de enteros.  En este tutorial se muestran las tareas siguientes:  
  
-   Iniciar el depurador de GPU.  
  
-   Inspeccionar los subprocesos de GPU en la ventana de subprocesos de GPU.  
  
-   Usar la ventana de Parallel Stacks para observar simultáneamente las pilas de las llamadas de varios subprocesos GPU.  
  
-   Usar la ventana de Inspección Paralela para inspeccionar valores de una única expresión a través de varios subprocesos al mismo tiempo.  
  
-   Señalar,congelar, descongelar y agrupar los subprocesos de GPU.  
  
-   Ejecutar todos los subprocesos de un mosaico en una ubicación especifica en el código.  
  
## Requisitos previos  
 Antes de iniciar el tutorial:  
  
-   Lea [Información general sobre C\+\+ AMP](../../parallel/amp/cpp-amp-overview.md).  
  
-   Asegúrese de que los números de línea aparecen en el editor de texto.  Para obtener más información, vea [Cómo: Mostrar los números de línea en el editor](../Topic/How%20to:%20Display%20Line%20Numbers%20in%20the%20Editor.md).  
  
-   Asegúrese de que está ejecutando [!INCLUDE[win8](../../build/includes/win8_md.md)] o [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] para admitir la depuración en el emulador del software.  
  
 [!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]  
  
### Para crear el proyecto de ejemplo  
  
1.  Inicie Visual Studio.  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el panel de plantillas **Instaladas,** elija **Visual C\+\+**.  
  
4.  Elija **Aplicación de consola Win32**, escriba `AMPMapReduce` en la casilla **Nombre** y elija el botón **Aceptar** .  
  
5.  Elija el botón **Siguiente**.  
  
6.  Desactive la casilla de verificación **Encabezado precompilado** y elija el botón **Finalizar** .  
  
7.  En el **Explorador de soluciones**, elimine stdafx.h, targetver.h y stdafx.cpp del proyecto.  
  
8.  Abra AMPMapReduce.cpp y reemplace su contenido con el siguiente código.  
  
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
        printf("sum: %s\n", passed ? "Passed!" : "Failed!");   
  
        getchar();  
  
        return 0;  
    }  
  
    ```  
  
9. En la barra de menús, elija **Archivo**, **Guardar todo**.  
  
10. En el **Explorador de soluciones**, abra el menú contextual para **AMPMapReduce** y, a continuación, elija **Propiedades**.  
  
11. En el cuadro de diálogo **Páginas de propiedades** , en **Propiedades de configuración**, elija **C\/C\+\+**, **Encabezados precompilados**.  
  
12. Para la propiedad **Encabezado precompilado** ,seleccione **No utilizar encabezados precompilados** y elija el botón **Aceptar** .  
  
13. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
## Depurar código de CPU  
 En este procedimiento, se utilizará el depurador local de Windows para asegurar que el código de la CPU en la aplicación es correcto.  El segmento de código CPU en esta aplicación que es especialmente interesante es el bucle `for` en la función `reduction_sum_gpu_kernel` .  Se encarga de controlar la reducción paralela en forma de árbol que se ejecuta en el GPU.  
  
### Para depurar el código de CPU  
  
1.  En el **Explorador de soluciones**, abra el menú contextual para **AMPMapReduce** y, a continuación, elija **Propiedades**.  
  
2.  En el cuadro de diálogo **Páginas de propiedades** , en **Propiedades de configuración**, elija **Depuración**.  Compruebe que el **Depurador local de Windows** esté seleccionado en la lista **Depurador para iniciar**.  
  
3.  Regrese al editor de código.  
  
4.  Establezca puntos de interrupción en las líneas de código que se muestran en la siguiente ilustración \(aproximadamente entre las líneas 67 y 70\).  
  
     ![Puntos de interrupción de CPU](../../parallel/amp/media/campcpubreakpoints.png "CampCpuBreakpoints")  
Puntos de interrupción de la CPU  
  
5.  En la barra de menús, elija **Depurar**, **Iniciar depuración**.  
  
6.  En la ventana **Locales**, observe el valor para `stride_size` hasta que se alcance el punto de interrupción en la línea 70.  
  
7.  En la barra de menús, seleccione **Depurar**, **Detener depuración**.  
  
## Depurar el código de GPU  
 Esta sección muestra cómo depurar el código de GPU, que es el código contenido en la función `sum_kernel_tiled` .  El código de GPU calcula la suma de enteros para cada “bloque” en paralelo.  
  
### Para depurar el código de GPU  
  
1.  En el **Explorador de soluciones**, abra el menú contextual para **AMPMapReduce** y, a continuación, elija **Propiedades**.  
  
2.  En el cuadro de diálogo **Páginas de propiedades** , en **Propiedades de configuración**, elija **Depuración**.  
  
3.  En la lista **Depurador para iniciar**, seleccione **Depurador local de Windows**.  
  
4.  En la lista **Tipo de depurador**, seleccione **Solo GPU**.  
  
5.  Elija el botón **Aceptar**.  
  
6.  Establezca un punto de interrupción en la línea 30, como se muestra en la siguiente ilustración.  
  
     ![Puntos de interrupción de GPU](../../parallel/amp/media/campgpubreakpoints.png "CampGpuBreakpoints")  
Punto de interrupción de GPU  
  
7.  En la barra de menús, elija **Depurar**, **Iniciar depuración**.  Los puntos de interrupción en el códigode la CPU en las líneas 67 y 70 no se ejecutan durante la depuración de GPU porque las líneas de código se ejecutan en la CPU.  
  
### Para utilizar la ventana de subprocesos de la GPU  
  
1.  Para abrir la ventana de subprocesos de la GPU, en la barra de menú, elija **Depurar**, **Ventanas**, **Subprocesos GPU**.  
  
     Puede inspeccionar el estado de los subprocesos de la GPU en la ventana de subprocesos de GPU que aparece.  
  
2.  Acople la ventana de Subprocesos de GPU en la parte inferior de Visual Studio.  Elija el botón de **Expandir el cambio de subproceso** para mostrar los cuadros de texto para los mosaicos y los subprocesos.  La ventana de subprocesos de la GPU muestra el número total de subprocesos de GPU activos y bloqueados, como aparece en la siguiente ilustración.  
  
     ![Ventana Subprocesos de GPU con 4 subprocesos activos](../../parallel/amp/media/campc.png "CampC")  
Ventana de subprocesos de GPU  
  
     Hay 313 mosaicos asignadas para este cálculo.  Cada mosaico contiene 32 subprocesos.  Dado que la depuración local de GPU se lleva a cabo en un emulador de software, hay cuatro subprocesos GPU activos.  Los cuatro subprocesos ejecutan las instrucciones simultáneamente y después se desplazan juntos a la siguiente instrucción.  
  
     En la ventana subprocesos de GPU, hay cuatro subprocesos de GPU activo y 28 subprocesos de GPU bloqueados en la instrucción de [tile\_barrier::wait](../Topic/tile_barrier::wait%20Method.md) definida en sobre la línea 21 \(`t_idx.barrier.wait();`\).  Los 32 subprocesos GPU pertenecen al primer mosaico, `tile[0]`.  Una flecha señala la fila donde se encuentra el subproceso actual.  Para cambiar a un subproceso diferente, utilice uno de los siguientes métodos:  
  
    -   En la fila del subproceso al que se desea cambiar en la ventana del subprocesos de GPU, abra el menú contextual y elija **Cambiar a subproceso**.  Si la fila representa más de un subproceso, cambiará al primer subproceso según las coordenadas del subproceso.  
  
    -   Escriba los valores de mosaico y subproceso en los cuadros de texto correspondientes y luego elija el botón **Cambiar subproceso** .  
  
     La ventana de pila de llamadas muestra la pila de llamadas del subproceso de GPU actual.  
  
### Para utilizar la ventana de pilas paralelas  
  
1.  Para abrir la ventana de pilas paralelas, en la barra de menú, elija **Depurar**, **Ventanas**, **Pilas paralelas**.  
  
     Puede utilizar la ventana de pilas paralelas para inspeccionar simultáneamente los marcos de pila de varios subprocesos de GPU.  
  
2.  Acople la ventana de pilas paralelas en la parte inferior de Visual Studio.  
  
3.  Asegúrese de que **Subprocesos** esté seleccionado en la lista de la esquina superior izquierda.  En la siguiente ilustración, la ventana de pilas paralelas ofrece una vista detallada de la pila de llamadas de los subprocesos de GPU que ya vio en la ventana subprocesos GPU.  
  
     ![Ventana Pilas paralelas con 4 subprocesos activos](../../parallel/amp/media/campd.png "CampD")  
Ventana Pilas paralelas  
  
     32 subprocesos fueron desde el `_kernel_stub` a la instrucción de lambda en la llamada de la función `parallel_for_each` y a continuación a la función `sum_kernel_tiled`, donde aparece la reducción. De los 32 subprocesos, 28 han progresado en la instrucción de [tile\_barrier::wait](../Topic/tile_barrier::wait%20Method.md) y permanecerán bloqueados en la línea 22, mientras que los otros 4 subprocesos siguen estando activos en la función de `sum_kernel_tiled` en la línea 30.  
  
     Puede examinar las propiedades de un subproceso de GPU que están disponibles en la ventana de subprocesos de la GPU en la información sobre datos enriquecido dentro de la ventana de pilas paralelas.  Para ello, sitúe el puntero del mouse en el marco de la pila **sum\_kernel\_tiled**.  La siguiente ilustración muestra la información de DataTip,  
  
     ![Información sobre datos para la ventana Pilas paralelas](../../parallel/amp/media/campe.png "CampE")  
Descripción emergente del Subproceso GPU  
  
     Para más información sobre la ventana de pilas paralelas, vea [Uso de la ventana Tareas paralelas](../Topic/Using%20the%20Parallel%20Stacks%20Window.md).  
  
### Para usar la ventana de inspección paralela  
  
1.  Para abrir la ventana de inspección paralela, en la barra de menú, elija **Depurar**, **Ventanas**, **Inspección paralela**, **Inspección paralela 1**.  
  
     Puede utilizar la ventana de inspección paralela para inspeccionar los valores de una expresión en varios subprocesos.  
  
2.  Acople la ventana de inspección paralela 1 a la parte inferior de Visual Studio.  Hay 32 filas en la tabla de la ventana de inspección paralela.  Cada una corresponde a un subproceso de GPU que ya apareció en la ventana de subprocesos de la GPU y la ventana de pilas paralelas.  Ahora, puede escribir expresiones cuyos valores desee inspeccionar en los 32 subprocesos GPU.  
  
3.  Seleccione el encabezado de columna **Agregar inspección**, escriba `localIdx` y después teclee INTRO.  
  
4.  Seleccione de nuevo el encabezado de columna **Agregar inspección**, el tipo `globalIdx` y después teclee INTRO.  
  
5.  Seleccione de nuevo el encabezado de columna **Agregar inspección**, el tipo `localA [localIdx [0]]` y después teclee INTRO.  
  
     Puede ordenar mediante una expresión especificada si selecciona su correspondiente encabezado de columna.  
  
     Seleccione el encabezado de la columna **localA \[localIdx \[0\]\]** para ordenar la columna.  La siguiente ilustración muestra los resultados de ordenación por **localA \[localIdx \[0\]\]**.  
  
     ![Ventana Inspección paralela con resultados ordenados](../../parallel/amp/media/campf.png "CampF")  
 Resultados de la ordenación  
  
     Puede exportar el contenido de la ventana de la inspección paralela a Excel mediante el botón Excel y luego elegir **Abrir en Excel**.  Si tiene instalado Excel en el equipo de desarrollo, éste abre una hoja de cálculo de Excel que incluye el contenido.  
  
6.  En la esquina superior derecha de la ventana de la inspección paralela, hay un control de filtro que se puede utilizar para filtrar el contenido mediante expresiones booleanas.  Escriba en `localA [localIdx [0]] > 20000` en el cuadro de texto del control de filtro y elija la tecla ENTRAR.  
  
     La ventana ahora sólo contiene los subprocesos en los que el valor de `localA[localIdx[0]]` son mayor que 20000.  El contenido todavía se ordena por la columna `localA[localIdx[0]]` , que es la acción de ordenación que se realizó anteriormente.  
  
## Marcar los subprocesos GPU  
 Puede marcar los subprocesos específicos de la GPU si las marca en las ventana de los subprocesos de GPU, la ventana de inspección paralela, o en la descripción emergente de pilas paralelas.  Si una fila en la ventana de subprocesos de GPU contiene más de un subproceso, al marcar esa fila se marcan todos los subprocesos que se incluyen en la fila.  
  
### Marcar los subprocesos de GPU  
  
1.  En la ventana de Inspección paralela 1, seleccione el encabezado de la columna **\[Subproceso\]** para ordenar por índice de mosaico y por índice de subproceso.  
  
2.  En la barra de menú, elija **Depurar**, **Continuar**, lo cual hace que los cuatro subprocesos que estaban activos avancen hacia la siguiente barrera \(definida en la línea 32 de AMPMapReduce.cpp\).  
  
3.  Elija el símbolo de marcador en el lado izquierdo de la fila que contiene los cuatro subprocesos activos ahora.  
  
     La siguiente ilustración muestran los cuatro subprocesos activos marcados en la ventana Subprocesos GPU.  
  
     ![Ventana Subprocesos de GPU con subprocesos marcados](../../parallel/amp/media/campg.png "CampG")  
Subprocesos activos en la ventana Subprocesos de GPU  
  
     Las ventanas de inspección paralela y la información de la ventana de pilas paralelas indican los subprocesos marcados.  
  
4.  Si desea centrarse en los cuatro subprocesos marcados, puede elegir mostrar, en las ventanas de los subprocesos de GPU, inspección paralela y pilas paralelas, solo en los subprocesos marcados.  
  
     Elija el botón Mostrar solo marcados en cualquiera de las ventanas o en la barra de herramientas **Ubicación de depuración** .  La siguiente ilustración muestra el botón Mostrar único botón en la barra de herramientas **Ubicación de depuración** .  
  
     ![Barra de herramientas Ubicación de depuración con el icono Mostrar marcadas únicamente](../../parallel/amp/media/camph.png "CampH")  
Botón Mostrar solo subprocesos marcados  
  
     Ahora las ventanas de los subprocesos de GPU, inspección paralela y pilas paralelas sólo muestran los subprocesos marcados.  
  
## Congelar y descongelar los Subprocesos GPU  
 Puede congelar \(suspender\) y descongelar \(continuar\) los subprocesos de GPU desde la ventana de los subprocesos GPU o desde la ventana Inspección paralela.  Puede congelar y descongelar los subprocesos de CPU de la misma manera; para obtener información, consulte [Cómo: Utilizar la ventana Subprocesos](../Topic/How%20to:%20Use%20the%20Threads%20Window.md).  
  
### Para congelar y descongelar los subprocesos de GPU  
  
1.  Elija el botón **Mostrar solo marcados** para mostrar todos los subprocesos.  
  
2.  En la barra menú, elija **Depurar**, **Continuar**.  
  
3.  Abrir el menú contextual para la fila activa y después elija **Congelar**.  
  
     La siguiente ilustración de la ventana de los subprocesos de GPU muestra que los cuatro subprocesos están congelados.  
  
     ![Ventana Subprocesos de GPU que muestra los subprocesos inmovilizados](../../parallel/amp/media/campk.png "CampK")  
Subprocesos inmovilizados en la ventana Subprocesos de GPU  
  
     De igual forma, la ventana de inspección paralela muestra que los cuatro subprocesos están congelados  
  
4.  En la barra menú, elija **Depurar**, **Continuar** para permitir que los siguientes cuatro subprocesos de la GPU avancen pasada la barrera en la línea 22 y lleguen al punto de interrupción en la línea 30.  La ventana de los subprocesos de GPU muestra que los cuatro subprocesos previamente congelados siguen congelados y en estado activo.  
  
5.  En la barra menú, elija **Depurar**, **Continuar**.  
  
6.  Desde la ventana de inspección paralela, también puede descongelar los subprocesos de GPU individuales o múltiples.  
  
### Agrupar los subprocesos de GPU  
  
1.  En el menú contextual para uno de los subprocesos en la ventana **Subprocesos GPU**, elija **Agrupar por**, **Dirección**.  
  
     Los subprocesos en la ventana de subprocesos de GPU están agrupados por la dirección.  La dirección corresponde a la instrucción en el desensamblado donde cada grupo de subprocesos se encuentra. 24 subprocesos están en la línea 22 donde se ejecuta el [tile\_barrier::wait \(Método\)](../Topic/tile_barrier::wait%20Method.md) . 12 subprocesos están en la instrucción para la barrera en la línea 32.  Cuatro de estos subprocesos están marcados.  Ocho subprocesos están en el punto de interrupción en la línea 30.  Cuatro de estos subprocesos están congelados.  La siguiente ilustración muestra los subprocesos agrupados en la ventana de subprocesos de la GPU.  
  
     ![Ventana Subprocesos de GPU con los subprocesos agrupados por dirección](../../parallel/amp/media/campl.png "CampL")  
Subprocesos agrupados en la ventana de Subprocesos de la GPU.  
  
2.  También puede realizar la operación **Agrupar por** al abrir el menú contextual de la cuadrícula de datos en la ventana de Inspección paralela, elija **Agrupar por** y luego elija el elemento del menú que corresponde a cómo desea agrupar los subprocesos.  
  
## Ejecutar todos los subprocesos en una ubicación específica del código  
 Ejecute todos los subprocesos de un mosaico determinado hasta la línea que contiene el cursor mediante **Ejecutar mosaico actual hasta el cursor**.  
  
### Para ejecutar todos los subprocesos a la ubicación marcada por el cursor  
  
1.  En el menú contextual, para los subprocesos congelados, elija **Descongelar**.  
  
2.  En el editor de código, colocar el cursor en la línea 30.  
  
3.  En el menú contextual del editor de código, elija **Ejecutar el mosaico actual hasta el cursor**.  
  
     Los 24 subprocesos que se bloquean previamente en la barrera en la línea 21 han progresado para la linea 32.  Esto se muestra en la ventana de **Subprocesos de GPU** .  
  
## Vea también  
 [Información general sobre C\+\+ AMP](../../parallel/amp/cpp-amp-overview.md)   
 [Depurar código de GPU](../Topic/Debugging%20GPU%20Code.md)   
 [Cómo: Utilizar la ventana Subprocesos de GPU](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)   
 [Cómo: Utilizar la Ventana Inspección paralela](../Topic/How%20to:%20Use%20the%20Parallel%20Watch%20Window.md)   
 [Analizar el código de AMP de C\+\+ con el visualizador de simultaneidad](http://go.microsoft.com/fwlink/?LinkID=253987&clcid=0x409)