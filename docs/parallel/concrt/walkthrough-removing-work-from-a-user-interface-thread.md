---
title: 'Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario'
ms.date: 04/25/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 214796777968c8aec7116a848e791aeef0d3af7b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512266"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario

En este documento se muestra cómo usar el Runtime de simultaneidad para trasladar el trabajo que realiza el subproceso de la interfaz de usuario (UI) en una aplicación Microsoft Foundation Classes (MFC) a un subproceso de trabajo. En este documento también se muestra cómo mejorar el rendimiento de una operación de dibujo prolongada.

Quitar el trabajo del subproceso de la interfaz de usuario mediante la descarga de las operaciones de bloqueo, por ejemplo, el dibujo, a los subprocesos de trabajo puede mejorar la capacidad de respuesta de la aplicación. En este tutorial se usa una rutina de dibujo que genera el fractal de Mandelbrot para mostrar una operación de bloqueo prolongada. La generación del fractal de Mandelbrot también es una buena candidata para la paralelización porque el cálculo de cada píxel es independiente de todos los demás cálculos.

## <a name="prerequisites"></a>Requisitos previos

Lea los siguientes temas antes de iniciar este tutorial:

- [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)

- [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)

- [Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)

También se recomienda que comprenda los aspectos básicos del desarrollo de aplicaciones MFC y GDI+ antes de comenzar este tutorial. Para obtener más información sobre MFC, vea [aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md). Para obtener más información sobre GDI+, vea [GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

##  <a name="top"></a> Secciones

Este tutorial contiene las siguientes secciones:

- [Crear la aplicación MFC](#application)

- [Implementar la versión en serie de la aplicación Mandelbrot](#serial)

- [Quitar el trabajo del subproceso de la interfaz de usuario](#removing-work)

- [Mejorar el rendimiento del dibujo](#performance)

- [Agregar compatibilidad para la cancelación](#cancellation)

##  <a name="application"></a>Crear la aplicación MFC

En esta sección se describe cómo crear la aplicación MFC básica.

### <a name="to-create-a-visual-c-mfc-application"></a>Para crear una aplicación C++ de Visual MFC

1. Utilice el **Asistente para aplicaciones MFC** para crear una aplicación MFC con todos los valores de configuración predeterminados. Vea [Tutorial: Usar los nuevos controles](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md) de Shell de MFC para obtener instrucciones sobre cómo abrir el Asistente para su versión de Visual Studio.

1. Escriba un nombre para el proyecto, por ejemplo, `Mandelbrot`y, a continuación, haga clic en **Aceptar** para mostrar el **Asistente para aplicaciones MFC**.

1. En el panel **tipo de aplicación** , seleccione **documento único**. Asegúrese de que la casilla **compatibilidad con la arquitectura de documento/vista** está desactivada.

1. Haga clic en **Finalizar** para crear el proyecto y cerrar el **Asistente para aplicaciones MFC**.

   Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela. Para compilar la aplicación, en el menú compilar, haga clic en compilar **solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo clic en **iniciar** depuración en el menú Depurar.

##  <a name="serial"></a>Implementar la versión en serie de la aplicación Mandelbrot

En esta sección se describe cómo dibujar el fractal de Mandelbrot. Esta versión dibuja el fractal de Mandelbrot en un objeto de [mapa de bits](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) de GDI+ y, a continuación, copia el contenido de ese mapa de bits en la ventana del cliente.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>Para implementar la versión en serie de la aplicación Mandelbrot

1. En stdafx. h, agregue la siguiente `#include` Directiva:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. En ChildView. h, después de `pragma` la Directiva, defina `BitmapPtr` el tipo. El `BitmapPtr` tipo permite que varios componentes compartan un puntero a un `Bitmap` objeto. El `Bitmap` objeto se elimina cuando ningún componente ya no hace referencia a él.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. En ChildView. h, agregue el código siguiente a la `protected` sección de la `CChildView` clase:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. En ChildView. cpp, comente o quite las líneas siguientes.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   En las compilaciones de depuración, este paso `DEBUG_NEW` evita que la aplicación use el asignador, que es incompatible con GDI+.

1. En ChildView. cpp, agregue una `using` directiva `Gdiplus` al espacio de nombres.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Agregue el código siguiente al constructor y al destructor de la `CChildView` clase para inicializar y cerrar GDI+.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implemente el método `CChildView::DrawMandelbrot`. Este método dibuja el fractal de Mandelbrot en el `Bitmap` objeto especificado.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implemente el método `CChildView::OnPaint`. Este método llama `CChildView::DrawMandelbrot` a y, a continuación, copia `Bitmap` el contenido del objeto en la ventana.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Compilar y ejecutar la aplicación para comprobar que se ha actualizado correctamente.

En la ilustración siguiente se muestran los resultados de la aplicación Mandelbrot.

![La aplicación Mandelbrot](../../parallel/concrt/media/mandelbrot.png "La aplicación Mandelbrot")

Dado que el cálculo de cada píxel es costoso, el subproceso de interfaz de usuario no puede procesar mensajes adicionales hasta que finalice el cálculo global. Esto puede reducir la capacidad de respuesta de la aplicación. Sin embargo, puede aliviar este problema quitando el trabajo del subproceso de interfaz de usuario.

[[Arriba](#top)]

##  <a name="removing-work"></a>Quitar el trabajo del subproceso de interfaz de usuario

En esta sección se muestra cómo quitar el trabajo de dibujo del subproceso de interfaz de usuario de la aplicación Mandelbrot. Al mover el trabajo de dibujo del subproceso de interfaz de usuario a un subproceso de trabajo, el subproceso de interfaz de usuario puede procesar los mensajes a medida que el subproceso de trabajo genera la imagen en segundo plano.

El Runtime de simultaneidad proporciona tres maneras de ejecutar tareas: [grupos de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)y [tareas ligeras](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Aunque puede usar cualquiera de estos mecanismos para quitar el trabajo del subproceso de interfaz de usuario, en este ejemplo se usa un objeto [Concurrency:: task_group](reference/task-group-class.md) porque los grupos de tareas admiten la cancelación. En este tutorial se usa posteriormente la cancelación para reducir la cantidad de trabajo que se realiza cuando se cambia el tamaño de la ventana del cliente y para realizar la limpieza cuando se destruye la ventana.

En este ejemplo también se usa un objeto [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) para permitir que el subproceso de interfaz de usuario y el subproceso de trabajo se comuniquen entre sí. Una vez que el subproceso de trabajo genera la imagen, envía un `Bitmap` puntero al objeto `unbounded_buffer` al objeto y, a continuación, envía un mensaje de dibujo al subproceso de la interfaz de usuario. A continuación, el subproceso de `unbounded_buffer` la interfaz `Bitmap` de usuario recibe del objeto el objeto y lo dibuja en la ventana del cliente.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>Para quitar el trabajo de dibujo del subproceso de interfaz de usuario

1. En stdafx. h, agregue las siguientes `#include` directivas:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. En ChildView. h, agregue `task_group` las `unbounded_buffer` variables de miembro y `protected` a la sección `CChildView` de la clase. El `task_group` objeto contiene las tareas que realizan el dibujo; `unbounded_buffer` el objeto contiene la imagen de Mandelbrot completada.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. En ChildView. cpp, agregue una `using` directiva `concurrency` al espacio de nombres.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. En el `CChildView::DrawMandelbrot` método, después de la llamada `Bitmap::UnlockBits`a, llame a la función Concurrency [:: Send](reference/concurrency-namespace-functions.md#send) para `Bitmap` pasar el objeto al subproceso de la interfaz de usuario. Después, publique un mensaje de Paint en el subproceso de la interfaz de usuario e invalide el área cliente.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Actualice el `CChildView::OnPaint` método para recibir el objeto `Bitmap` actualizado y dibuje la imagen en la ventana del cliente.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   El `CChildView::OnPaint` método crea una tarea para generar la imagen de Mandelbrot si no existe ninguna en el búfer de mensajes. El búfer de mensajes no contendrá `Bitmap` un objeto en casos como el mensaje de dibujo inicial y el momento en que se mueve otra ventana delante de la ventana de cliente.

1. Compilar y ejecutar la aplicación para comprobar que se ha actualizado correctamente.

La interfaz de usuario ahora tiene mayor capacidad de respuesta porque el trabajo de dibujo se realiza en segundo plano.

[[Arriba](#top)]

##  <a name="performance"></a>Mejorar el rendimiento del dibujo

La generación del fractal de Mandelbrot es una buena candidata para la paralelización porque el cálculo de cada píxel es independiente de todos los demás cálculos. Para paralelizar el procedimiento de dibujo, convierta el `for` bucle exterior en `CChildView::DrawMandelbrot` el método en una llamada al algoritmo [Concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) , como se indica a continuación.

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Dado que el cálculo de cada elemento de mapa de bits es independiente, no es necesario sincronizar las operaciones de dibujo que tienen acceso a la memoria de mapa de bits. Esto permite escalar el rendimiento a medida que aumenta el número de procesadores disponibles.

[[Arriba](#top)]

##  <a name="cancellation"></a>Agregar compatibilidad para la cancelación

En esta sección se describe cómo controlar el cambio de tamaño de las ventanas y cómo cancelar cualquier tarea de dibujo activa cuando se destruye la ventana.

La cancelación del documento [en la biblioteca PPL](cancellation-in-the-ppl.md) explica cómo funciona la cancelación en tiempo de ejecución. La cancelación es Cooperativa; por lo tanto, no se produce inmediatamente. Para detener una tarea cancelada, el tiempo de ejecución produce una excepción interna durante una llamada subsiguiente de la tarea en el tiempo de ejecución. En la sección anterior se muestra cómo usar `parallel_for` el algoritmo para mejorar el rendimiento de la tarea de dibujo. La llamada a `parallel_for` permite al motor en tiempo de ejecución detener la tarea y, por tanto, permite que la cancelación funcione.

### <a name="cancelling-active-tasks"></a>Cancelar tareas activas

La aplicación Mandelbrot crea `Bitmap` objetos cuyas dimensiones coinciden con el tamaño de la ventana de cliente. Cada vez que se cambia el tamaño de la ventana de cliente, la aplicación crea una tarea en segundo plano adicional para generar una imagen para el nuevo tamaño de la ventana. La aplicación no requiere estas imágenes intermedias; solo requiere la imagen para el tamaño de ventana final. Para evitar que la aplicación realice este trabajo adicional, puede cancelar cualquier tarea de dibujo activa en los controladores de mensajes para los `WM_SIZE` mensajes `WM_SIZING` y y, a continuación, volver a programar el trabajo de dibujo una vez que se cambie el tamaño de la ventana.

Para cancelar las tareas de dibujo activas cuando se cambia el tamaño de la ventana, la aplicación llama al método Concurrency [:: task_group:: CANCEL](reference/task-group-class.md#cancel) en los controladores `WM_SIZING` de `WM_SIZE` los mensajes y. El controlador `WM_SIZE` del mensaje también llama al método [Concurrency:: task_group:: wait](reference/task-group-class.md#wait) para esperar a que se completen todas las tareas activas y, a continuación, vuelve a programar la tarea de dibujo para el tamaño de la ventana actualizado.

Cuando se destruye la ventana de cliente, se recomienda cancelar las tareas de dibujo activas. Al cancelar cualquier tarea de dibujo activa, se asegura de que los subprocesos de trabajo no publiquen mensajes en el subproceso de la interfaz de usuario después de que se destruya la ventana cliente. La aplicación cancela cualquier tarea de dibujo activa en el controlador para el `WM_DESTROY` mensaje.

### <a name="responding-to-cancellation"></a>Responder a la cancelación

El `CChildView::DrawMandelbrot` método, que realiza la tarea de dibujo, debe responder a la cancelación. Dado que el motor en tiempo de ejecución utiliza el control `CChildView::DrawMandelbrot` de excepciones para cancelar las tareas, el método debe utilizar un mecanismo seguro para excepciones para garantizar que todos los recursos se limpien correctamente. En este ejemplo se usa el patrón *Resource Acquisition Is Initialization* (RAII) para garantizar que los bits de mapa de bits se desbloqueen cuando se cancele la tarea.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>Para agregar compatibilidad para la cancelación en la aplicación Mandelbrot

1. En ChildView. h, en la `protected` sección de la `CChildView` clase, agregue las declaraciones de las `OnSize`funciones `OnSizing`de asignación `OnDestroy` de mensajes, y.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. En ChildView. cpp, modifique el mapa de mensajes para que contenga controladores `WM_SIZE`para `WM_SIZING`los mensajes `WM_DESTROY` , y.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implemente el método `CChildView::OnSizing`. Este método cancela cualquier tarea de dibujo existente.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implemente el método `CChildView::OnSize`. Este método cancela cualquier tarea de dibujo existente y crea una nueva tarea de dibujo para el tamaño de la ventana del cliente actualizado.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implemente el método `CChildView::OnDestroy`. Este método cancela cualquier tarea de dibujo existente.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. En ChildView. cpp, defina la `scope_guard` clase, que implementa el patrón RAII.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Agregue el código siguiente al `CChildView::DrawMandelbrot` método después de la llamada a: `Bitmap::LockBits`

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Este código controla la cancelación mediante la `scope_guard` creación de un objeto. Cuando el objeto abandona el ámbito, desbloquea los bits de mapa de bits.

1. Modifique el final del `CChildView::DrawMandelbrot` método para descartar el `scope_guard` objeto una vez desbloqueados los bits de mapa de bits, pero antes de que se envíen mensajes al subproceso de la interfaz de usuario. Esto garantiza que el subproceso de la interfaz de usuario no se actualice antes de que se desbloqueen los bits de mapa de bits.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. Compilar y ejecutar la aplicación para comprobar que se ha actualizado correctamente.

Al cambiar el tamaño de la ventana, el trabajo de dibujo solo se realiza para el tamaño de ventana final. Las tareas de dibujo activas también se cancelan cuando se destruye la ventana.

[[Arriba](#top)]

## <a name="see-also"></a>Vea también

[Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)<br/>
[Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)<br/>
[Cancelación en la biblioteca PPL](cancellation-in-the-ppl.md)<br/>
[Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md)
