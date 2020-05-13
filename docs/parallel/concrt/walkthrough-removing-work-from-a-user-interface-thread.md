---
title: 'Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario'
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 52bc98ef339a19c6ec2a53697f532a9a94b6c9a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377439"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario

En este documento se muestra cómo utilizar el Runtime de simultaneidad para mover el trabajo realizado por el subproceso de interfaz de usuario (UI) en una aplicación de Microsoft Foundation Classes (MFC) a un subproceso de trabajo. Este documento también muestra cómo mejorar el rendimiento de una operación de dibujo larga.

Quitar el trabajo del subproceso de interfaz de usuario descargando las operaciones de bloqueo, por ejemplo, dibujar, a subprocesos de trabajo puede mejorar la capacidad de respuesta de la aplicación. Este tutorial utiliza una rutina de dibujo que genera el fractal Mandelbrot para demostrar una operación de bloqueo prolongada. La generación del fractal Mandelbrot también es un buen candidato para la paralelización porque el cálculo de cada píxel es independiente de todos los demás cálculos.

## <a name="prerequisites"></a>Prerrequisitos

Lea los siguientes temas antes de iniciar este tutorial:

- [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funciones de paso de mensajes](../../parallel/concrt/message-passing-functions.md)

- [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)

- [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)

También se recomienda comprender los conceptos básicos del desarrollo de aplicaciones MFC y GDI+GDI+ antes de iniciar este tutorial. Para obtener más información acerca de MFC, vea Aplicaciones de [escritorio MFC](../../mfc/mfc-desktop-applications.md). Para obtener más información acerca de GDI+, consulte [GDI+GDI+.](/windows/win32/gdiplus/-gdiplus-gdi-start)

## <a name="sections"></a><a name="top"></a>Secciones

Este tutorial contiene las siguientes secciones:

- [Creación de la aplicación MFC](#application)

- [Implementación de la versión en serie de la aplicación Mandelbrot](#serial)

- [Eliminación del trabajo del subproceso de interfaz de usuario](#removing-work)

- [Mejorar el rendimiento del dibujo](#performance)

- [Adición de soporte para la cancelación](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a>Creación de la aplicación MFC

En esta sección se describe cómo crear la aplicación MFC básica.

### <a name="to-create-a-visual-c-mfc-application"></a>Para crear una aplicación MFC de Visual C++

1. Utilice el **Asistente para aplicaciones MFC** para crear una aplicación MFC con toda la configuración predeterminada. Consulte [Tutorial: uso](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) de los nuevos controles de shell MFC para obtener instrucciones sobre cómo abrir el asistente para la versión de Visual Studio.

1. Escriba un nombre para el `Mandelbrot`proyecto, por ejemplo, y, a continuación, haga clic en **Aceptar** para mostrar el **Asistente para aplicaciones MFC**.

1. En el panel Tipo de **aplicación,** seleccione **Documento único**. Asegúrese de que la casilla de verificación **Compatibilidad con la arquitectura de documento/vista** esté desactivada.

1. Haga clic en **Finalizar** para crear el proyecto y cerrar el **Asistente para aplicaciones MFC.**

   Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el menú **Compilar,** haga clic en **Compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo clic en **Iniciar depuración** en el menú **Depurar.**

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a>Implementación de la versión en serie de la aplicación Mandelbrot

Esta sección describe cómo dibujar el fractal mandelbrot. Esta versión dibuja el fractal Mandelbrot en un objeto [GDI+ Bitmap](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) y, a continuación, copia el contenido de ese mapa de bits en la ventana del cliente.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Para implementar la versión en serie de la aplicación Mandelbrot

1. En *pch.h* (*stdafx.h* en Visual Studio 2017 `#include` y versiones anteriores), agregue la siguiente directiva:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. En ChildView.h, `pragma` después de `BitmapPtr` la directiva, defina el tipo. El `BitmapPtr` tipo permite que `Bitmap` varios componentes compartan un puntero a un objeto. El `Bitmap` objeto se elimina cuando ningún componente hace referencia a él.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. En ChildView.h, agregue el `protected` código siguiente `CChildView` a la sección de la clase:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. En ChildView.cpp, comente o quite las siguientes líneas.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   En compilaciones de depuración, este `DEBUG_NEW` paso impide que la aplicación use el asignador, que es incompatible con GDI+GDI+.

1. En ChildView.cpp, `using` agregue una `Gdiplus` directiva al espacio de nombres.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Agregue el código siguiente al constructor `CChildView` y destructor de la clase para inicializar y cerrar GDI+GDI+.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implemente el método `CChildView::DrawMandelbrot`. Este método dibuja el fractal Mandelbrot `Bitmap` en el objeto especificado.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implemente el método `CChildView::OnPaint`. Este método `CChildView::DrawMandelbrot` llama y, a `Bitmap` continuación, copia el contenido del objeto en la ventana.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Compruebe que la aplicación se actualizó correctamente mediante la creación y ejecución.

En la siguiente ilustración se muestran los resultados de la aplicación Mandelbrot.

![La aplicación Mandelbrot](../../parallel/concrt/media/mandelbrot.png "La aplicación Mandelbrot")

Dado que el cálculo de cada píxel es costoso desde el punto de vista informático, el subproceso de interfaz de usuario no puede procesar mensajes adicionales hasta que finalice el cálculo general. Esto podría disminuir la capacidad de respuesta en la aplicación. Sin embargo, puede aliviar este problema quitando el trabajo del subproceso de interfaz de usuario.

[[Superior](#top)]

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a>Eliminación del trabajo del subproceso de interfaz de usuario

En esta sección se muestra cómo quitar el trabajo de dibujo del subproceso de interfaz de usuario en la aplicación Mandelbrot. Al mover el trabajo de dibujo desde el subproceso de interfaz de usuario a un subproceso de trabajo, el subproceso de interfaz de usuario puede procesar mensajes a medida que el subproceso de trabajo genera la imagen en segundo plano.

El Runtime de simultaneidad proporciona tres formas de ejecutar tareas: [grupos de tareas,](../../parallel/concrt/task-parallelism-concurrency-runtime.md) [agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)y [tareas ligeras.](../../parallel/concrt/task-scheduler-concurrency-runtime.md) Aunque puede usar cualquiera de estos mecanismos para quitar el trabajo del subproceso de interfaz de usuario, en este ejemplo se usa un objeto [concurrency::task_group](reference/task-group-class.md) porque los grupos de tareas admiten la cancelación. En este tutorial se usa más adelante la cancelación para reducir la cantidad de trabajo que se realiza cuando se cambia el tamaño de la ventana del cliente y para realizar la limpieza cuando se destruye la ventana.

En este ejemplo también se usa un objeto [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) para permitir que el subproceso de interfaz de usuario y el subproceso de trabajo se comuniquen entre sí. Después de que el subproceso de trabajo `Bitmap` genera la `unbounded_buffer` imagen, envía un puntero al objeto al objeto y, a continuación, publica un mensaje de pintura en el subproceso de interfaz de usuario. A continuación, el `unbounded_buffer` subproceso de `Bitmap` interfaz de usuario recibe del objeto el objeto y lo dibuja en la ventana del cliente.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Para quitar el trabajo de dibujo del subproceso de interfaz de usuario

1. En *pch.h* (*stdafx.h* en Visual Studio 2017 `#include` y versiones anteriores), agregue las siguientes directivas:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. En ChildView.h, `task_group` `unbounded_buffer` agregue y las `protected` variables `CChildView` miembro a la sección de la clase. El `task_group` objeto contiene las tareas que realizan el dibujo; el `unbounded_buffer` objeto contiene la imagen completa de Mandelbrot.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. En ChildView.cpp, `using` agregue una `concurrency` directiva al espacio de nombres.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. En `CChildView::DrawMandelbrot` el método, después de la llamada a `Bitmap::UnlockBits`, llame a la función [concurrency::send](reference/concurrency-namespace-functions.md#send) para pasar el `Bitmap` objeto al subproceso de interfaz de usuario. A continuación, publique un mensaje de pintura en el subproceso de interfaz de usuario e invalide el área de cliente.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Actualice `CChildView::OnPaint` el método para `Bitmap` recibir el objeto actualizado y dibujar la imagen en la ventana del cliente.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   El `CChildView::OnPaint` método crea una tarea para generar la imagen de Mandelbrot si no existe una en el búfer de mensajes. El búfer de mensajes `Bitmap` no contendrá un objeto en casos como el mensaje de pintura inicial y cuando se mueve otra ventana delante de la ventana del cliente.

1. Compruebe que la aplicación se actualizó correctamente mediante la creación y ejecución.

La interfaz de usuario ahora es más sensible porque el trabajo de dibujo se realiza en segundo plano.

[[Superior](#top)]

## <a name="improving-drawing-performance"></a><a name="performance"></a>Mejorar el rendimiento del dibujo

La generación del fractal Mandelbrot es un buen candidato para la paralelización porque el cálculo de cada píxel es independiente de todos los demás cálculos. Para paralelizar el procedimiento `for` de `CChildView::DrawMandelbrot` dibujo, convierta el bucle externo del método en una llamada al algoritmo [concurrency::parallel_for,](reference/concurrency-namespace-functions.md#parallel_for) como se indica a continuación.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Dado que el cálculo de cada elemento de mapa de bits es independiente, no es necesario sincronizar las operaciones de dibujo que tienen acceso a la memoria de mapa de bits. Esto permite que el rendimiento se escale a medida que aumenta el número de procesadores disponibles.

[[Superior](#top)]

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a>Adición de soporte para la cancelación

En esta sección se describe cómo controlar el cambio de tamaño de ventana y cómo cancelar las tareas de dibujo activas cuando se destruye la ventana.

El documento [Cancelación en la PPL](cancellation-in-the-ppl.md) explica cómo funciona la cancelación en tiempo de ejecución. La cancelación es cooperativa; por lo tanto, no ocurre inmediatamente. Para detener una tarea cancelada, el tiempo de ejecución produce una excepción interna durante una llamada posterior de la tarea en el tiempo de ejecución. En la sección anterior `parallel_for` se muestra cómo utilizar el algoritmo para mejorar el rendimiento de la tarea de dibujo. La llamada `parallel_for` permite que el tiempo de ejecución detenga la tarea y, por lo tanto, permite que la cancelación funcione.

### <a name="cancelling-active-tasks"></a>Cancelación de tareas activas

La aplicación Mandelbrot crea `Bitmap` objetos cuyas dimensiones coinciden con el tamaño de la ventana de cliente. Cada vez que se cambia el tamaño de la ventana de cliente, la aplicación crea una tarea en segundo plano adicional para generar una imagen para el nuevo tamaño de ventana. La aplicación no requiere estas imágenes intermedias; sólo requiere la imagen para el tamaño final de la ventana. Para evitar que la aplicación realice este trabajo adicional, puede cancelar cualquier `WM_SIZE` tarea `WM_SIZING` de dibujo activa en los controladores de mensajes para los mensajes y, a continuación, reprogramar el trabajo de dibujo después de cambiar el tamaño de la ventana.

Para cancelar las tareas de dibujo activas cuando se cambia el tamaño de la ventana, `WM_SIZING` la `WM_SIZE` aplicación llama al método [concurrency::task_group::cancel](reference/task-group-class.md#cancel) en los controladores de los mensajes y. El controlador `WM_SIZE` del mensaje también llama al método [concurrency::task_group::wait](reference/task-group-class.md#wait) para esperar a que se completen todas las tareas activas y, a continuación, reprograma la tarea de dibujo para el tamaño de ventana actualizado.

Cuando se destruye la ventana de cliente, se recomienda cancelar las tareas de dibujo activas. La cancelación de las tareas de dibujo activas garantiza que los subprocesos de trabajo no publiquen mensajes en el subproceso de interfaz de usuario después de destruir la ventana de cliente. La aplicación cancela las tareas de dibujo `WM_DESTROY` activas en el controlador del mensaje.

### <a name="responding-to-cancellation"></a>Responder a la cancelación

El `CChildView::DrawMandelbrot` método, que realiza la tarea de dibujo, debe responder a la cancelación. Dado que el tiempo de ejecución `CChildView::DrawMandelbrot` usa el control de excepciones para cancelar tareas, el método debe usar un mecanismo seguro para excepciones para garantizar que todos los recursos se limpian correctamente. En este ejemplo se utiliza el patrón *Resource Acquisition Is Initialization* (RAII) para garantizar que los bits de mapa de bits se desbloquean cuando se cancela la tarea.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Para añadir soporte para cancelación en la aplicación Mandelbrot

1. En ChildView.h, `protected` en la `CChildView` sección de la `OnSize`clase, agregue declaraciones para las funciones , `OnSizing`, y `OnDestroy` mapa de mensajes.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. En ChildView.cpp, modifique el mapa de `WM_SIZE`mensajes `WM_SIZING`para `WM_DESTROY` que contenga controladores para los mensajes , , y .

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implemente el método `CChildView::OnSizing`. Este método cancela las tareas de dibujo existentes.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implemente el método `CChildView::OnSize`. Este método cancela las tareas de dibujo existentes y crea una nueva tarea de dibujo para el tamaño de ventana de cliente actualizado.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implemente el método `CChildView::OnDestroy`. Este método cancela las tareas de dibujo existentes.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. En ChildView.cpp, `scope_guard` defina la clase, que implementa el patrón RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Agregue el siguiente `CChildView::DrawMandelbrot` código al método `Bitmap::LockBits`después de la llamada a:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Este código controla `scope_guard` la cancelación mediante la creación de un objeto. Cuando el objeto deja el ámbito, desbloquea los bits de mapa de bits.

1. Modifique el final `CChildView::DrawMandelbrot` del método `scope_guard` para descartar el objeto después de desbloquear los bits de mapa de bits, pero antes de que se envíen mensajes al subproceso de interfaz de usuario. Esto garantiza que el subproceso de interfaz de usuario no se actualiza antes de que se desbloqueen los bits de mapa de bits.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. Compruebe que la aplicación se actualizó correctamente mediante la creación y ejecución.

Al cambiar el tamaño de la ventana, el trabajo de dibujo se realiza solo para el tamaño final de la ventana. Las tareas de dibujo activas también se cancelan cuando se destruye la ventana.

[[Superior](#top)]

## <a name="see-also"></a>Consulte también

[Tutoriales en tiempo de ejecución de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones de paso de mensajes](../../parallel/concrt/message-passing-functions.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md)
