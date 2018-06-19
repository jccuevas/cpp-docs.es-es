---
title: 'Tutorial: Quitar trabajo de un subproceso de interfaz de usuario | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0502ce728c35b08d927cea48ee5b82756980aec5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694292"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario
Este documento muestra cómo usar el Runtime de simultaneidad para mover el trabajo que se realiza mediante el subproceso de interfaz de usuario (UI) en una aplicación de Microsoft Foundation Classes (MFC) para un subproceso de trabajo. Este documento también muestra cómo mejorar el rendimiento de una operación de dibujo prolongada.  
  
 Quitar trabajo desde el subproceso de interfaz de usuario mediante la descarga de operaciones de bloqueo, por ejemplo, dibujo, a subprocesos de trabajo puede mejorar la capacidad de respuesta de la aplicación. Este tutorial utiliza una rutina de dibujo que genera el fractal de Mandelbrot para demostrar una operación larga de bloqueo. La generación del fractal de Mandelbrot también es un buen candidato para la ejecución en paralelo porque el cálculo de cada píxel es independiente de todos los demás cálculos.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Lea los siguientes temas antes de iniciar este tutorial:  
  
-   [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)  
  
-   [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)  
  
-   [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)  
  
 También se recomienda que entienda los fundamentos de desarrollo de aplicaciones de MFC y [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] antes de iniciar este tutorial. Para obtener más información acerca de MFC, vea [aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md). Para obtener más información acerca de [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)], consulte [GDI +](https://msdn.microsoft.com/en-us/library/windows/desktop/ms533798).  
  
##  <a name="top"></a> Secciones  
 Este tutorial contiene las siguientes secciones:  
  
-   [Crear la aplicación MFC](#application)  
  
-   [Implementación de la versión en serie de la aplicación Mandelbrot](#serial)  
  
-   [Quitar trabajo desde el subproceso de interfaz de usuario](#removing-work)  
  
-   [Mejorar el rendimiento de dibujo](#performance)  
  
-   [Agregar compatibilidad para cancelación](#cancellation)  
  
##  <a name="application"></a> Crear la aplicación MFC  
 En esta sección se describe cómo crear la aplicación MFC básica.  
  
### <a name="to-create-a-visual-c-mfc-application"></a>Para crear una aplicación MFC de Visual C++  
  
1.  En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, en la **plantillas instaladas** panel, seleccione **Visual C++** y, a continuación, en la **plantillas** panel, seleccione **Aplicación MFC**. Escriba un nombre para el proyecto, por ejemplo, `Mandelbrot`y, a continuación, haga clic en **Aceptar** para mostrar la **Asistente para aplicaciones MFC**.  
  
3.  En el **tipo de aplicación** panel, seleccione **único documento**. Asegúrese de que el **compatibilidad con la arquitectura documento/vista** casilla de verificación está desactivada.  
  
4.  Haga clic en **finalizar** para crear el proyecto y cierre el **Asistente para aplicaciones MFC**.  
  
     Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en la **generar** menú, haga clic en **generar solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo clic en **Iniciar depuración** en el **depurar** menú.  
  
##  <a name="serial"></a> Implementación de la versión en serie de la aplicación Mandelbrot  
 Esta sección describe cómo dibujar el fractal de Mandelbrot. Esta versión dibuja el fractal de Mandelbrot para un [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [mapa de bits](https://msdn.microsoft.com/library/ms534420.aspx) de objeto y, a continuación, copia el contenido del mapa de bits en la ventana del cliente.  
  
#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Para implementar la versión en serie de la aplicación Mandelbrot  
  
1.  En stdafx.h, agregue las siguientes `#include` directiva:  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  En ChildView.h, después de la `pragma` directiva, definir la `BitmapPtr` tipo. El `BitmapPtr` tipo permite un puntero a un `Bitmap` objeto debe ser compartida por varios componentes. La `Bitmap` objeto se elimina cuando ya no se hace referencia por alguno de los componentes.  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  En ChildView.h, agregue el código siguiente a la `protected` sección de la `CChildView` clase:  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  En ChildView.cpp, marque como comentario o quite las siguientes líneas.  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     En las compilaciones de depuración, este paso impide que la aplicación utilizando la `DEBUG_NEW` asignador, que no es compatible con [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
5.  En ChildView.cpp, agregue un `using` la directiva a la `Gdiplus` espacio de nombres.  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  Agregue el código siguiente al constructor y destructor de la `CChildView` clase para inicializar y cerrar [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  Implemente el método `CChildView::DrawMandelbrot`. Este método dibuja el fractal de Mandelbrot para especificado `Bitmap` objeto.  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  Implemente el método `CChildView::OnPaint`. Este método llama a `CChildView::DrawMandelbrot` y, a continuación, copia el contenido de la `Bitmap` objeto en la ventana.  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. Compruebe que la aplicación se ha actualizado correctamente.  
  
 La ilustración siguiente muestra los resultados de la aplicación Mandelbrot.  
  
 ![La aplicación Mandelbrot](../../parallel/concrt/media/mandelbrot.png "mandelbrot")  
  
 Dado que el cálculo de cada píxel es caro, el subproceso de interfaz de usuario no puede procesar mensajes adicionales hasta que finaliza el cálculo general. Esto puede reducir la capacidad de respuesta en la aplicación. Sin embargo, puede aliviar este problema quitando el trabajo desde el subproceso de interfaz de usuario.  
  
 [[Arriba](#top)]  
  
##  <a name="removing-work"></a> Quitar trabajo desde el subproceso de interfaz de usuario  
 En esta sección se muestra cómo quitar el trabajo de dibujo del subproceso de interfaz de usuario en la aplicación Mandelbrot. Al mover el trabajo de dibujo desde el subproceso de interfaz de usuario a un subproceso de trabajo, el subproceso de interfaz de usuario puede procesar mensajes como el subproceso de trabajo genera la imagen en segundo plano.  
  
 El Runtime de simultaneidad proporciona tres maneras de ejecutar tareas: [grupos de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md), y [tareas ligeras](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Aunque puede usar cualquiera de estos mecanismos para quitar el trabajo desde el subproceso de interfaz de usuario, este ejemplo se utiliza un [Concurrency:: task_group](reference/task-group-class.md) objeto porque los grupos de tareas admiten la cancelación. Más adelante en este tutorial usa la cancelación para reducir la cantidad de trabajo que se realiza cuando se cambia el tamaño de la ventana de cliente y debe realizar una limpieza cuando se destruye la ventana.  
  
 Este ejemplo también utiliza un [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) objeto para permitir que el subproceso de interfaz de usuario y el subproceso de trabajo para comunicarse entre sí. Una vez que el subproceso de trabajo genera la imagen, envía un puntero a la `Bitmap` el objeto a la `unbounded_buffer` del objeto y, a continuación, envía un mensaje de dibujo al subproceso de interfaz de usuario. El subproceso de interfaz de usuario, a continuación, se recibe desde el `unbounded_buffer` objeto el `Bitmap` objeto y lo muestra en la ventana del cliente.  
  
#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Para quitar el trabajo de dibujo del subproceso de interfaz de usuario  
  
1.  En stdafx.h, agregue las siguientes `#include` directivas:  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  En ChildView.h, agregue `task_group` y `unbounded_buffer` variables de miembro a la `protected` sección de la `CChildView` clase. El `task_group` objeto contiene las tareas que realizan un dibujo; la `unbounded_buffer` objeto contiene la imagen de Mandelbrot completada.  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  En ChildView.cpp, agregue un `using` la directiva a la `concurrency` espacio de nombres.  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  

4.  En el `CChildView::DrawMandelbrot` método después de llamar a `Bitmap::UnlockBits`, llame a la [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) función para pasar el `Bitmap` objeto al subproceso de interfaz de usuario. A continuación, registrar un mensaje de dibujo al subproceso de interfaz de usuario e invalidar el área de cliente.  

  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  Actualización de la `CChildView::OnPaint` método para recibir la actualización `Bitmap` de objetos y dibujar la imagen a la ventana de cliente.  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     El `CChildView::OnPaint` método crea una tarea para generar la imagen de Mandelbrot si no existe en el búfer de mensajes. El búfer de mensajes no contendrá un `Bitmap` objeto en casos como el mensaje de dibujo inicial y cuando se mueve otra ventana delante de la ventana de cliente.  
  
6.  Compruebe que la aplicación se ha actualizado correctamente.  
  
 La interfaz de usuario ahora es más sensible, ya que el trabajo de dibujo se realiza en segundo plano.  
  
 [[Arriba](#top)]  
  
##  <a name="performance"></a> Mejorar el rendimiento de dibujo  

 La generación del fractal de Mandelbrot es un buen candidato para la ejecución en paralelo porque el cálculo de cada píxel es independiente de todos los demás cálculos. Para paralelizar el procedimiento de dibujo, convertir el exterior `for` un bucle en el `CChildView::DrawMandelbrot` método a una llamada a la [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo, como se indica a continuación.  

  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 Dado que el cálculo de cada elemento de mapa de bits es independiente, no tienes que volver a sincronizar las operaciones de dibujo que tienen acceso a la memoria de mapa de bits. Así, puede escalar como el número de procesadores disponibles aumenta el rendimiento.  
  
 [[Arriba](#top)]  
  
##  <a name="cancellation"></a> Agregar compatibilidad para cancelación  
 Esta sección describe cómo controlar el cambio de tamaño de ventana y cómo cancelar las tareas de dibujo activas cuando se destruye la ventana.  
  
 El documento [cancelación en la biblioteca PPL](cancellation-in-the-ppl.md) explica cómo funciona la cancelación en el tiempo de ejecución. La cancelación es cooperativa; por lo tanto, esto no sucede inmediatamente. Para detener una tarea cancelada, el runtime produce una excepción interna durante una llamada posterior de la tarea en el tiempo de ejecución. La sección anterior muestra cómo utilizar el `parallel_for` algoritmo para mejorar el rendimiento de la tarea de dibujo. La llamada a `parallel_for` permite que el tiempo de ejecución detener la tarea y, por tanto, que la cancelación para trabajar.  
  
### <a name="cancelling-active-tasks"></a>Cancelar tareas activas  
 Crea la aplicación Mandelbrot `Bitmap` objetos cuyas dimensiones coinciden con el tamaño de la ventana del cliente. Cada vez que se cambia el tamaño de la ventana de cliente, la aplicación crea una tarea de obtener información general adicional para generar una imagen para el nuevo tamaño de ventana. La aplicación no necesita estas imágenes intermedias; requiere solo la imagen para el tamaño de la ventana final. Para evitar que la aplicación realice este trabajo adicional, puede cancelar las tareas de dibujo activas en los controladores de mensajes para la `WM_SIZE` y `WM_SIZING` mensajes y, a continuación, dibujos de reprogramar funcionan después de cambiar el tamaño de la ventana.  
  
 Para cancelar las tareas de dibujo activas cuando se cambia el tamaño de la ventana, la aplicación llama a la [concurrency::task_group::cancel](reference/task-group-class.md#cancel) método en los controladores para la `WM_SIZING` y `WM_SIZE` mensajes. El controlador para el `WM_SIZE` mensaje también llamadas el [concurrency::task_group::wait](reference/task-group-class.md#wait) método esperar active todas las tareas para completar y, a continuación, reprograma la tarea de dibujo para el tamaño de ventana actualizado.  
  
 Cuando se destruye la ventana de cliente, es recomendable para cancelar las tareas de dibujo activas. Cancelar las tareas de dibujo activas, se asegura de que los subprocesos de trabajo no envían mensajes al subproceso de interfaz de usuario después de que se destruya la ventana del cliente. La aplicación cancela las tareas de dibujo activas en el controlador para el `WM_DESTROY` mensaje.  
  
### <a name="responding-to-cancellation"></a>Responder a la cancelación  
 El `CChildView::DrawMandelbrot` método, que realiza la tarea de dibujo, debe responder a la cancelación. Dado que el runtime usa el control de excepciones para cancelar las tareas, la `CChildView::DrawMandelbrot` método debe utilizar un mecanismo seguro ante excepciones para garantizar que todos los recursos se limpian correctamente. Este ejemplo se utiliza la *Resource Acquisition Is Initialization* patrón (RAII) para garantizar que los bits del mapa de bits se desbloquean cuando se cancela la tarea.  
  
##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Para agregar compatibilidad para cancelación en la aplicación Mandelbrot  
  
1.  En ChildView.h, en la `protected` sección de la `CChildView` clase, agregue las declaraciones para la `OnSize`, `OnSizing`, y `OnDestroy` funciones de mapa de mensajes.  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  En ChildView.cpp, modifique el mapa de mensajes para que contenga los controladores para la `WM_SIZE`, `WM_SIZING`, y `WM_DESTROY` mensajes.  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  Implemente el método `CChildView::OnSizing`. Este método cancela las tareas de dibujo existentes.  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  Implemente el método `CChildView::OnSize`. Este método cancela las tareas de dibujo existentes y crea una nueva tarea de dibujo para el tamaño de la ventana de cliente actualizado.  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  Implemente el método `CChildView::OnDestroy`. Este método cancela las tareas de dibujo existentes.  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  En ChildView.cpp, defina el `scope_guard` (clase), que implementa el modelo RAII.  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  Agregue el código siguiente a la `CChildView::DrawMandelbrot` método después de llamar a `Bitmap::LockBits`:  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     Este código controla la cancelación mediante la creación de un `scope_guard` objeto. Cuando el objeto sale del ámbito, desbloquea el mapa de bits.  
  
8.  Modifique el final de la `CChildView::DrawMandelbrot` método para descartar la `scope_guard` objeto después de que se desbloquean los bits del mapa de bits, pero antes de que los mensajes se envían al subproceso de interfaz de usuario. Esto garantiza que el subproceso de interfaz de usuario no se actualiza antes de que se desbloquean los bits del mapa de bits.  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. Compruebe que la aplicación se ha actualizado correctamente.  
  
 Cuando cambia el tamaño de la ventana, trabajo de dibujo solo se realiza para el tamaño de la ventana final. También se cancelan las tareas de dibujo activas cuando se destruye la ventana.  
  
 [[Arriba](#top)]  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)   
 [Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md)
