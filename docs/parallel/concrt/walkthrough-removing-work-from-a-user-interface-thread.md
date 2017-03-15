---
title: "Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "quitar trabajo de los subprocesos de interfaz de usuario [Runtime de simultaneidad]"
  - "subprocesos de interfaz de usuario, quitar trabajo de [Runtime de simultaneidad]"
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Tutorial: Quitar trabajo de un subproceso de la interfaz de usuario
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este documento se muestra cómo se usa el Runtime de simultaneidad para trasladar el trabajo realizado por un subproceso de la interfaz de usuario de una aplicación Microsoft Foundation Classes \(MFC\) a un subproceso de trabajo.  En este documento se muestra también cómo puede mejorarse el rendimiento de una operación de dibujo larga.  
  
 La capacidad de respuesta de una aplicación puede mejorar si se quita trabajo de un subproceso de la interfaz de usuario trasladando las operaciones en bloque, como por ejemplo las operaciones de dibujo, a subprocesos de trabajo.  En este tutorial se usa una rutina de dibujo que genera el fractal de Mandelbrot para ilustrar una operación en bloque larga.  La generación del fractal de Mandelbrot también resulta adecuada para la paralelización, ya que el cálculo de cada píxel se realiza independientemente de todos los demás cálculos.  
  
## Requisitos previos  
 Lea los siguientes temas antes de iniciar este tutorial:  
  
-   [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
-   [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)  
  
-   [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)  
  
-   [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)  
  
 También es recomendable que conozca los fundamentos de desarrollo de la aplicación MFC y [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] antes de iniciar este tutorial.  Para obtener más información sobre MFC, vea [Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md).  Para obtener más información sobre [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)], vea [GDI\+](_gdiplus_GDI_start_cpp).  
  
##  <a name="top"></a> Secciones  
 Este tutorial contiene las siguientes secciones:  
  
-   [Crear la aplicación MFC](#application)  
  
-   [Implementar la versión de serie de la aplicación Mandelbrot](#serial)  
  
-   [Quitar trabajo del subproceso de la interfaz de usuario](#removing-work)  
  
-   [Mejorar el rendimiento de las operaciones de dibujo](#performance)  
  
-   [Agregar compatibilidad con la operación de cancelación](#cancellation)  
  
##  <a name="application"></a> Crear la aplicación MFC  
 En esta sección se describe cómo se crea una aplicación MFC básica.  
  
### Para crear una aplicación MFC con Visual C\+\+  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en el panel **Plantillas instaladas**, seleccione **Visual C\+\+** y, a continuación, seleccione **Aplicación MFC** en el recuadro **Plantillas**.  Escriba un nombre para el proyecto, por ejemplo, `Mandelbrot` y, a continuación, haga clic en **Aceptar** para mostrar el **Asistente para aplicaciones MFC**.  
  
3.  En el panel **Tipo de aplicación**, seleccione **Documento único**.  Asegúrese de que la casilla **Compatibilidad con la arquitectura documento\/vista** está desactivada.  
  
4.  Haga clic en **Finalizar** para crear el proyecto y cerrar el **Asistente para aplicaciones MFC**.  
  
     Compruebe que la aplicación se creó correctamente; para ello, compílela y ejecútela.  Para compilar la aplicación, en el menú **Generar**, haga clic en **Generar solución**.  Si la aplicación se compila correctamente, en el menú **Depurar**, haga clic en **Iniciar depuración** para ejecutarla.  
  
##  <a name="serial"></a> Implementar la versión de serie de la aplicación Mandelbrot  
 En esta sección se describe cómo se dibuja el fractal de Mandelbrot.  En esta versión, el fractal de Mandelbrot se dibuja en un objeto [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)] [Bitmap](https://msdn.microsoft.com/en-us/library/ms534420.aspx) y, a continuación, se copia el contenido de ese mapa de bits en la ventana del cliente.  
  
#### Para implementar la versión de serie de la aplicación Mandelbrot  
  
1.  En stdafx.h, agregue la directiva `#include` siguiente:  
  
     [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_1.h)]  
  
2.  En ChildView.h, después de la directiva `pragma`, defina el tipo `BitmapPtr`.  El tipo `BitmapPtr` habilita un puntero en un objeto `Bitmap` que van a compartir varios componentes.  El objeto `Bitmap` se elimina cuando ya ningún componente hace referencia a él.  
  
     [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_2.h)]  
  
3.  En ChildView.h, agregue el código siguiente a la sección `protected` de la clase `CChildView`:  
  
     [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_3.h)]  
  
4.  En ChildView.cpp, marque como comentario o quite las siguientes líneas.  
  
     [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]  
  
     En las compilaciones de depuración, este paso impide que la aplicación use el asignador de `DEBUG_NEW`, que no es compatible con [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
5.  En ChildView.cpp, agregue una directiva `using` al espacio de nombres `Gdiplus`.  
  
     [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]  
  
6.  Agregue el siguiente código al constructor y destructor de la clase `CChildView` para inicializar y cerrar [!INCLUDE[ndptecgdiplus](../../parallel/concrt/includes/ndptecgdiplus_md.md)].  
  
     [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]  
  
7.  Implemente el método `CChildView::DrawMandelbrot`.  Este método dibuja el fractal de Mandelbrot en el objeto `Bitmap` especificado.  
  
     [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]  
  
8.  Implemente el método `CChildView::OnPaint`.  Este método llama a `CChildView::DrawMandelbrot` y copia el contenido del objeto `Bitmap` en la ventana.  
  
     [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]  
  
9. Compruebe que la aplicación se ha actualizado correctamente; para ello, compílela y ejecútela.  
  
 En la ilustración siguiente se muestran los resultados de la aplicación Mandelbrot.  
  
 ![La aplicación Mandelbrot](../../parallel/concrt/media/mandelbrot.png "Mandelbrot")  
  
 Como el cálculo de cada píxel consume muchos recursos, el subproceso de la interfaz de usuario no puede procesar otros mensajes hasta que finaliza todo el cálculo.  Esto puede reducir la capacidad de respuesta de la aplicación.  Sin embargo, puede aliviar este problema quitando el trabajo del subproceso de la interfaz de usuario.  
  
 \[[Arriba](#top)\]  
  
##  <a name="removing-work"></a> Quitar el trabajo del subproceso de la interfaz de usuario  
 En esta sección se muestra cómo se quita el trabajo de dibujo del subproceso de la interfaz de usuario de la aplicación Mandelbrot.  Al desplazar el trabajo de dibujo del subproceso de la interfaz de usuario a un subproceso de trabajo, el subproceso de la interfaz de usuario puede procesar los mensajes mientras el subproceso de trabajo genera la imagen en segundo plano.  
  
 El Runtime de simultaneidad proporciona tres mecanismos para ejecutar las tareas: [grupos de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md) y [tareas ligeras](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  Aunque puede utilizar cualquiera de estos mecanismos para quitar el trabajo del subproceso de la interfaz de usuario, en este ejemplo se usa un objeto de [concurrency::task\_group](../Topic/task_group%20Class.md) porque los grupos de tareas admiten la cancelación.  En este tutorial, más adelante se usa la cancelación para reducir la cantidad de trabajo que se realiza cuando cambia el tamaño de la ventana del cliente y para realizar la limpieza cuando se destruye la ventana.  
  
 Este ejemplo también utiliza un objeto de [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) para permitir que el subproceso de la interfaz de usuario y el subproceso de trabajo para comunicarse entre sí.  Una vez que el subproceso de trabajo genera la imagen, envía un puntero al objeto `Bitmap` en el objeto `unbounded_buffer` y envía un mensaje de dibujo al subproceso de la interfaz de usuario.  A continuación, el subproceso de la interfaz de usuario recibe el objeto `Bitmap` del objeto `unbounded_buffer` y lo dibuja en la ventana del cliente.  
  
#### Para quitar el trabajo de dibujo del subproceso de la interfaz de usuario  
  
1.  En stdafx.h, agregue las directivas `#include` siguientes:  
  
     [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_9.h)]  
  
2.  En ChildView.h, agregue las variables miembro `task_group` y `unbounded_buffer` a la sección `protected` de la clase `CChildView`.  El objeto `task_group` contiene las tareas que realizan las operaciones de dibujo; el objeto `unbounded_buffer` contiene la imagen completada de Mandelbrot.  
  
     [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_10.h)]  
  
3.  En ChildView.cpp, agregue una directiva `using` al espacio de nombres `concurrency`.  
  
     [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]  
  
4.  En el método de `CChildView::DrawMandelbrot` , después de la llamada a `Bitmap::UnlockBits`, llame a la función de [concurrency::send](../Topic/send%20Function.md) para pasar el objeto de `Bitmap` al subproceso de la interfaz de usuario.  A continuación, envíe un mensaje del dibujo al subproceso de la interfaz de usuario e invalide el área cliente.  
  
     [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]  
  
5.  Actualice el método `CChildView::OnPaint` que va a recibir el objeto `Bitmap` actualizado y dibuje la imagen en la ventana del cliente.  
  
     [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]  
  
     El método `CChildView::OnPaint` crea una tarea para generar la imagen de Mandelbrot si no existe ninguna en el búfer de mensajes.  El búfer de mensajes no contendrá ningún objeto `Bitmap` en casos como el del mensaje del dibujo inicial y cuando otra ventana se sitúa delante de la ventana de cliente.  
  
6.  Compruebe que la aplicación se ha actualizado correctamente; para ello, compílela y ejecútela.  
  
 La Interfaz de usuario tiene ahora mayor capacidad de respuesta porque el trabajo de dibujo se realiza en segundo plano.  
  
 \[[Arriba](#top)\]  
  
##  <a name="performance"></a> Mejorar el rendimiento de las operaciones de dibujo  
 La generación del fractal de Mandelbrot también resulta adecuada para la paralelización, ya que el cálculo de cada píxel se realiza independientemente de todos los demás cálculos.  Para paralelizar el procedimiento de dibujo, convierta el bucle externo de `for` en el método de `CChildView::DrawMandelbrot` a una llamada al algoritmo de [concurrency::parallel\_for](../Topic/parallel_for%20Function.md) , como sigue.  
  
 [!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]  
  
 Dado que el cálculo de cada elemento de mapa de bits es independiente, no tiene que sincronizar las operaciones de dibujo que tienen acceso a la memoria del mapa de bits.  De este modo, se puede escalar el rendimiento cuando aumenta el número de procesadores disponibles.  
  
 \[[Arriba](#top)\]  
  
##  <a name="cancellation"></a> Agregar compatibilidad con la operación de cancelación  
 En esta sección se describe cómo se administra el cambio de tamaño de la ventana y cómo se cancelan las tareas de dibujo activas cuando se destruye la ventana.  
  
 En el documento [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md) se explica cómo funciona la cancelación en el runtime.  La cancelación es una operación cooperativa; por tanto, no se produce inmediatamente.  Para detener una tarea cancelada, el runtime inicia una excepción interna durante una llamada posterior desde la tarea al runtime.  En la sección anterior se muestra cómo se usa el algoritmo `parallel_for` para mejorar el rendimiento de la tarea de dibujo.  La llamada a `parallel_for` permite al runtime detener la tarea y, por tanto, permite que la cancelación funcione.  
  
### Cancelar tareas activas  
 La aplicación Mandelbrot crea objetos `Bitmap` cuyas dimensiones coinciden con el tamaño de la ventana del cliente.  Cada vez que cambia el tamaño de la ventana del cliente, la aplicación crea una tarea adicional en segundo plano para generar una imagen del nuevo tamaño de la ventana.  La aplicación no necesita estas imágenes intermedias; solamente necesita la imagen con el tamaño de ventana final.  Para evitar que la aplicación realice este trabajo adicional, puede cancelar las ventanas de dibujo activas en los controladores de mensajes `WM_SIZE` y `WM_SIZING` y volver a programar el trabajo de dibujo tras cambiar el tamaño de la ventana.  
  
 Para cancelar las tareas de dibujo activas cuando se cambia el tamaño de la ventana, la aplicación llama al método de [concurrency::task\_group::cancel](../Topic/task_group::cancel%20Method.md) en los controladores de los mensajes de `WM_SIZING` y de `WM_SIZE` .  El controlador del mensaje de `WM_SIZE` también llama al método de [concurrency::task\_group::wait](../Topic/task_group::wait%20Method.md) para esperar a que todas las tareas activas de completar y después reprograma la tarea de dibujo para el tamaño de la ventana actualizado.  
  
 Cuando se destruye la ventana del cliente, resulta conveniente cancelar las tareas de dibujo activas.  Al cancelar las tareas de dibujo activas, se asegura de que los subprocesos de trabajo no envían mensajes al subproceso de interfaz de usuario una vez que la ventana del cliente se ha destruido.  La aplicación cancela las tareas de dibujo activas en el controlador del mensaje `WM_DESTROY`.  
  
### Responder a la cancelación  
 El método `CChildView::DrawMandelbrot`, que realiza la tarea de dibujo, debe responder a la cancelación.  Como el runtime usa el control de excepciones para cancelar tareas, el método `CChildView::DrawMandelbrot` debe usar un mecanismo seguro ante excepciones para garantizar que todos los recursos se limpian correctamente.  En este ejemplo se usa el modelo *Resource Acquisition Is Initialization* \(RAII\) para garantizar que los bits del mapa de bits se desbloquean cuando se cancela la tarea.  
  
##### Para agregar compatibilidad con la operación de cancelación en la aplicación Mandelbrot  
  
1.  En ChildView.h, en la sección `protected` de la clase `CChildView`, agregue las declaraciones de las funciones de asignación de mensajes `OnSize`, `OnDestroy` y `OnSizing`.  
  
     [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_15.h)]  
  
2.  En ChildView.cpp, modifique la asignación de mensajes para que incluya controladores de los mensajes `WM_SIZE`, `WM_SIZING` y `WM_DESTROY`.  
  
     [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]  
  
3.  Implemente el método `CChildView::OnSizing`.  Este método cancela las tareas de dibujo existentes.  
  
     [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]  
  
4.  Implemente el método `CChildView::OnSize`.  Este método cancela las tareas de dibujo existentes y crea una nueva tarea de dibujo para el tamaño actualizado de la ventana del cliente.  
  
     [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]  
  
5.  Implemente el método `CChildView::OnDestroy`.  Este método cancela las tareas de dibujo existentes.  
  
     [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]  
  
6.  En ChildView.cpp, defina la clase `scope_guard`, que implementa el modelo RAII.  
  
     [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]  
  
7.  Agregue el código siguiente al método `CChildView::DrawMandelbrot` después de la llamada a `Bitmap::LockBits`.  
  
     [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]  
  
     Este código administra la cancelación creando un objeto `scope_guard`.  Cuando el objeto abandona el ámbito, desbloquea los bits del mapa de bits.  
  
8.  Modifique el final del método `CChildView::DrawMandelbrot` para desechar el objeto `scope_guard` una vez que se desbloquean los bits del mapa de bits, pero antes de que se envíe ningún mensaje al subproceso de interfaz de usuario.  De este modo, se asegura de que el subproceso de interfaz de usuario no se actualiza antes de que los bits del mapa de bits se desbloqueen.  
  
     [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/CPP/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]  
  
9. Compruebe que la aplicación se ha actualizado correctamente; para ello, compílela y ejecútela.  
  
 Al cambiar el tamaño de la ventana, el trabajo de dibujo se realiza únicamente de acuerdo con el tamaño de ventana final.  Las tareas de dibujo activas se cancelan también cuando se destruye la ventana.  
  
 \[[Arriba](#top)\]  
  
## Vea también  
 [Tutoriales del Runtime de simultaneidad](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Paralelismo de tareas](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)   
 [Algoritmos paralelos](../../parallel/concrt/parallel-algorithms.md)   
 [Cancelación](../../parallel/concrt/cancellation-in-the-ppl.md)   
 [Aplicaciones de escritorio de MFC](../../mfc/mfc-desktop-applications.md)