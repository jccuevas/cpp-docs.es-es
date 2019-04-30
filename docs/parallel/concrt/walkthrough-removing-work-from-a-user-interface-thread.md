---
title: 'Tutorial: Quitar trabajo de un subproceso de interfaz de usuario'
ms.date: 11/19/2018
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 1838ad0d6adb146adacb8b3a395f44f76e2a8d3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407811"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Tutorial: Quitar trabajo de un subproceso de interfaz de usuario

Este documento muestra cómo usar el Runtime de simultaneidad para mover el trabajo realizado por el subproceso de interfaz de usuario (UI) en una aplicación de Microsoft Foundation Classes (MFC) para un subproceso de trabajo. Este documento también muestra cómo mejorar el rendimiento de una operación de dibujo prolongada.

Quitar trabajo desde el subproceso de interfaz de usuario mediante la descarga de operaciones de bloqueo, por ejemplo, dibujar, en subprocesos de trabajo puede mejorar la capacidad de respuesta de la aplicación. Este tutorial utiliza una rutina de dibujo que genera el fractal de Mandelbrot para demostrar una operación larga de bloquea. La generación del fractal de Mandelbrot también es un buen candidato para la paralelización, dado que el cálculo de cada píxel es independiente de todos los demás cálculos.

## <a name="prerequisites"></a>Requisitos previos

Lea los siguientes temas antes de iniciar este tutorial:

- [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)

- [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)

- [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)

También se recomienda comprender los aspectos básicos del desarrollo de aplicaciones de MFC y GDI + antes de empezar este tutorial. Para obtener más información acerca de MFC, vea [MFC Desktop Applications](../../mfc/mfc-desktop-applications.md). Para obtener más información acerca de GDI +, consulte [GDI +](https://msdn.microsoft.com/library/windows/desktop/ms533798).

##  <a name="top"></a> Secciones

Este tutorial contiene las siguientes secciones:

- [Crear la aplicación MFC](#application)

- [Implementación de la versión en serie de la aplicación Mandelbrot](#serial)

- [Quitar el trabajo desde el subproceso de interfaz de usuario](#removing-work)

- [Mejorar el rendimiento de dibujo](#performance)

- [Agregar compatibilidad con la cancelación](#cancellation)

##  <a name="application"></a> Crear la aplicación MFC

En esta sección se describe cómo crear la aplicación básica de MFC.

### <a name="to-create-a-visual-c-mfc-application"></a>Para crear una aplicación MFC de Visual C++

1. En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.

1. En el **nuevo proyecto** cuadro de diálogo el **plantillas instaladas** panel, seleccione **Visual C++** y, a continuación, en el **plantillas** panel, seleccione **Aplicación MFC**. Escriba un nombre para el proyecto, por ejemplo, `Mandelbrot`y, a continuación, haga clic en **Aceptar** para mostrar el **MFC Application Wizard**.

1. En el **tipo de aplicación** panel, seleccione **único documento**. Asegúrese de que el **compatibilidad con la arquitectura documento/vista** casilla está desactivada.

1. Haga clic en **finalizar** para crear el proyecto y cierre el **MFC Application Wizard**.

   Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el **compilar** menú, haga clic en **compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo **Iniciar depuración** en el **depurar** menú.

##  <a name="serial"></a> Implementación de la versión en serie de la aplicación Mandelbrot

En esta sección se describe cómo se va a dibujar el fractal de Mandelbrot. Esta versión dibuja el fractal de Mandelbrot en GDI + [mapa de bits](/windows/desktop/api/gdiplusheaders/nl-gdiplusheaders-bitmap) de objetos y, a continuación, copia el contenido del mapa de bits en la ventana del cliente.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Para implementar la versión en serie de la aplicación Mandelbrot

1. En stdafx.h, agregue la siguiente `#include` directiva:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. En ChildView.h, después de la `pragma` directiva, definir la `BitmapPtr` tipo. El `BitmapPtr` tipo permite un puntero a un `Bitmap` objeto para ser compartidos por varios componentes. El `Bitmap` se elimina el objeto cuando ya no se hace referencia ningún componente.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. En ChildView.h, agregue el código siguiente a la `protected` sección de la `CChildView` clase:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. En ChildView.cpp, marque como comentario o quite las líneas siguientes.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   En las compilaciones de depuración, este paso evita que la aplicación utilizando la `DEBUG_NEW` asignador, que es incompatible con GDI +.

1. En ChildView.cpp, agregue un `using` la directiva a la `Gdiplus` espacio de nombres.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Agregue el código siguiente al constructor y destructor de la `CChildView` clase para inicializar y cerrar GDI +.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implemente el método `CChildView::DrawMandelbrot`. Este método dibuja el fractal de Mandelbrot especificado `Bitmap` objeto.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implemente el método `CChildView::OnPaint`. Este método llama a `CChildView::DrawMandelbrot` y, a continuación, copia el contenido de la `Bitmap` objeto en la ventana.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Compruebe que la aplicación se ha actualizado correctamente.

La ilustración siguiente muestra los resultados de la aplicación Mandelbrot.

![La aplicación Mandelbrot](../../parallel/concrt/media/mandelbrot.png "la aplicación Mandelbrot")

Dado que el cálculo de cada píxel es consumen muchos recursos, el subproceso de interfaz de usuario no puede procesar los mensajes adicionales hasta que finalice el cálculo global. Esto podría disminuir la capacidad de respuesta de la aplicación. Sin embargo, puede aliviar este problema quitando el trabajo desde el subproceso de interfaz de usuario.

[[Arriba](#top)]

##  <a name="removing-work"></a> Quitar el trabajo desde el subproceso de interfaz de usuario

En esta sección se muestra cómo quitar el trabajo de dibujo del subproceso de interfaz de usuario en la aplicación Mandelbrot. Al mover el trabajo de dibujo desde el subproceso de interfaz de usuario a un subproceso de trabajo, el subproceso de interfaz de usuario puede procesar mensajes, como el subproceso de trabajo genera la imagen en segundo plano.

El Runtime de simultaneidad proporciona tres maneras de ejecutar tareas: [grupos de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md), y [tareas ligeras](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Aunque puede usar cualquiera de estos mecanismos para quitar el trabajo desde el subproceso de interfaz de usuario, este ejemplo se usa un [Concurrency:: task_group](reference/task-group-class.md) objeto porque los grupos de tareas admiten la cancelación. Más adelante en este tutorial usa la cancelación para reducir la cantidad de trabajo que se realiza cuando se cambia el tamaño de la ventana del cliente y debe realizar una limpieza cuando se destruye la ventana.

Este ejemplo también se usa un [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) objeto para permitir que el subproceso de interfaz de usuario y el subproceso de trabajo se comuniquen entre sí. Una vez que el subproceso de trabajo genera la imagen, envía un puntero a la `Bitmap` de objeto para el `unbounded_buffer` objeto y, a continuación, envía un mensaje de dibujo al subproceso de interfaz de usuario. El subproceso de interfaz de usuario, a continuación, se recibe desde el `unbounded_buffer` objeto el `Bitmap` objeto y lo dibuja en la ventana del cliente.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Para quitar el trabajo de dibujo del subproceso de interfaz de usuario

1. En stdafx.h, agregue la siguiente `#include` directivas:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. En ChildView.h, agregue `task_group` y `unbounded_buffer` variables miembro para el `protected` sección de la `CChildView` clase. El `task_group` objeto contiene las tareas que realizan un dibujo; el `unbounded_buffer` objeto contiene la imagen de Mandelbrot completada.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. En ChildView.cpp, agregue un `using` la directiva a la `concurrency` espacio de nombres.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. En el `CChildView::DrawMandelbrot` método después de llamar a `Bitmap::UnlockBits`, llame a la [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) función para pasar el `Bitmap` objeto al subproceso de interfaz de usuario. A continuación, publicar un mensaje de dibujo al subproceso de interfaz de usuario e invalidar el área de cliente.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Actualización de la `CChildView::OnPaint` método para recibir la actualización `Bitmap` de objetos y dibuje la imagen en la ventana del cliente.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   El `CChildView::OnPaint` método crea una tarea para generar la imagen de Mandelbrot si no existe en el búfer de mensajes. El búfer de mensajes no contendrá un `Bitmap` objeto en casos como el mensaje de dibujo inicial y cuando se mueve la otra ventana delante de la ventana de cliente.

1. Compruebe que la aplicación se ha actualizado correctamente.

La interfaz de usuario es ahora más capacidad de respuesta porque el trabajo de dibujo se realiza en segundo plano.

[[Arriba](#top)]

##  <a name="performance"></a> Mejorar el rendimiento de dibujo

La generación del fractal de Mandelbrot es un buen candidato para la paralelización, dado que el cálculo de cada píxel es independiente de todos los demás cálculos. Para paralelizar el procedimiento de dibujo, convertir el exterior `for` bucle en el `CChildView::DrawMandelbrot` método a una llamada a la [Concurrency:: parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algoritmo, como se indica a continuación.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Dado que el cálculo de cada elemento de mapa de bits es independiente, no es necesario sincronizar las operaciones de dibujo que tienen acceso a la memoria de mapa de bits. Así, puede escalar como el número de procesadores disponibles aumenta el rendimiento.

[[Arriba](#top)]

##  <a name="cancellation"></a> Agregar compatibilidad con la cancelación

En esta sección se describe cómo controlar el cambio de tamaño de ventana y cómo cancelar las tareas de dibujos activas cuando se destruye la ventana.

El documento [cancelación en PPL](cancellation-in-the-ppl.md) explica cómo funciona la cancelación en el tiempo de ejecución. La cancelación es cooperativa; por lo tanto, no ocurre inmediatamente. Para detener una tarea cancelada, el tiempo de ejecución produce una excepción interna durante una llamada subsiguiente de la tarea en tiempo de ejecución. La sección anterior muestra cómo usar el `parallel_for` algoritmo para mejorar el rendimiento de la tarea de dibujo. La llamada a `parallel_for` permite que el tiempo de ejecución detener la tarea y que, por tanto, la cancelación para trabajar.

### <a name="cancelling-active-tasks"></a>Cancelar tareas activas

Crea la aplicación Mandelbrot `Bitmap` objetos cuyas dimensiones coinciden con el tamaño de la ventana del cliente. Cada vez que se cambia el tamaño de la ventana del cliente, la aplicación crea una tarea en segundo plano adicionales para generar una imagen para el nuevo tamaño de ventana. La aplicación no necesita estas imágenes intermedias; requiere solo la imagen para el tamaño de ventana final. Para evitar que la aplicación lleve a cabo este trabajo adicional, puede cancelar las tareas de dibujos activas en los controladores de mensajes para el `WM_SIZE` y `WM_SIZING` mensajes y, a continuación, dibujar reprogramar funcionan después de cambiar el tamaño de la ventana.

Para cancelar las tareas de dibujos activas cuando se cambia el tamaño de la ventana, la aplicación llama a la [task_group](reference/task-group-class.md#cancel) método en los controladores para la `WM_SIZING` y `WM_SIZE` mensajes. El controlador para el `WM_SIZE` mensaje también llama a la [task_group](reference/task-group-class.md#wait) método espera para que active todas las tareas para completar y, a continuación, vuelve a programar la tarea de dibujo para el tamaño de ventana actualizada.

Cuando se destruye la ventana del cliente, es recomendable para cancelar las tareas de dibujos activas. Cancelar las tareas de dibujos activas, se asegura de que los subprocesos de trabajo no publicar mensajes en el subproceso de interfaz de usuario después de que se destruye la ventana del cliente. La aplicación cancela las tareas de dibujos activas en el controlador para el `WM_DESTROY` mensaje.

### <a name="responding-to-cancellation"></a>Responder a la cancelación

El `CChildView::DrawMandelbrot` método, que realiza la tarea de dibujo, debe responder a la cancelación. Dado que el runtime usa el control de excepciones para cancelar las tareas, el `CChildView::DrawMandelbrot` método debe utilizar un mecanismo seguro para excepciones para garantizar que todos los recursos se limpian correctamente. Este ejemplo se usa el *Resource Acquisition Is Initialization* patrón (RAII) para garantizar que el mapa de bits se desbloquean cuando se cancela la tarea.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Para agregar compatibilidad con la cancelación de la aplicación Mandelbrot

1. En ChildView.h, en la `protected` sección de la `CChildView` clase, agregue las declaraciones para el `OnSize`, `OnSizing`, y `OnDestroy` funciones de mapa de mensajes.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. En ChildView.cpp, modifique el mapa de mensajes para que contenga los controladores para la `WM_SIZE`, `WM_SIZING`, y `WM_DESTROY` mensajes.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implemente el método `CChildView::OnSizing`. Este método cancela las tareas de dibujo existentes.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implemente el método `CChildView::OnSize`. Este método cancela las tareas de dibujo existentes y crea una nueva tarea de dibujo para el tamaño de ventana de cliente actualizado.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implemente el método `CChildView::OnDestroy`. Este método cancela las tareas de dibujo existentes.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. En ChildView.cpp, defina el `scope_guard` (clase), que implementa el modelo RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Agregue el código siguiente a la `CChildView::DrawMandelbrot` método después de llamar a `Bitmap::LockBits`:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Este código controla la cancelación mediante la creación de un `scope_guard` objeto. Cuando el objeto sale del ámbito, desbloquea el mapa de bits.

1. Modifique el final de la `CChildView::DrawMandelbrot` método para descartar el `scope_guard` objeto una vez que se desbloquean los bits del mapa de bits, pero antes de que los mensajes se envían al subproceso de interfaz de usuario. Esto garantiza que el subproceso de interfaz de usuario no se actualiza antes de que el mapa de bits se desbloqueen.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. Compruebe que la aplicación se ha actualizado correctamente.

Cuando cambia el tamaño de la ventana, el trabajo de dibujo se realiza solo para el tamaño de ventana final. También se cancelan las tareas de dibujos activas cuando se destruye la ventana.

[[Arriba](#top)]

## <a name="see-also"></a>Vea también

[Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md)
