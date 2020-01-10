---
title: Creación de proyectos multiplataforma de C++ en Visual Studio
description: Cómo configurar, compilar y depurar C++ un proyecto de cmake de código abierto en Visual Studio que tenga como destino Linux y Windows.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: 83d71d3078e892a51aef159b225fecec2b581f20
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791768"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Tutorial: crear C++ proyectos multiplataforma en Visual Studio

El desarrollo de C y C++ en Visual Studio ya no es solo para Windows. En este tutorial se muestra cómo usar Visual Studio C++ para el desarrollo multiplataforma en Windows y Linux. Se basa en CMake, por lo que no tiene que crear ni generar proyectos de Visual Studio. Cuando se abre una carpeta que contiene un archivo archivo CMakeLists. txt, Visual Studio configura las opciones de IntelliSense y compilación de forma automática. Puede empezar a editar, compilar y depurar rápidamente el código localmente en Windows. A continuación, cambie la configuración para hacer lo mismo en Linux, todo desde Visual Studio.

En este tutorial aprenderá a:

> [!div class="checklist"]
> * Clonar un proyecto de CMake de código abierto desde GitHub
> * Abrir el proyecto en Visual Studio
> * Compilar y depurar un destino ejecutable en Windows
> * Agregar una conexión a un equipo Linux
> * Compilar y depurar el mismo destino en Linux

## <a name="prerequisites"></a>Requisitos previos

* Configuración de Visual Studio para el desarrollo multiplataforma de C++
  * En primer lugar, [instale Visual Studio](https://visualstudio.microsoft.com/vs/) y elija desarrollo de  **C++ escritorio con** y **desarrollo C++ de Linux con cargas de trabajo**. Esta instalación mínima es de solo 3 GB. En función de la velocidad de descarga, la instalación no debe tardar más de 10 minutos.

* Configuración de un equipo Linux para el desarrollo multiplataforma con C++
  * Visual Studio no requiere ninguna distribución específica de Linux. El sistema operativo puede ejecutarse en una máquina física, en una máquina virtual o en la nube. También puede usar el subsistema de Windows para Linux (WSL). Sin embargo, para este tutorial se requiere un entorno gráfico. WSL no se recomienda aquí porque está diseñado principalmente para operaciones de línea de comandos.
  * Visual Studio requiere estas herramientas en la máquina Linux: C++ compiladores, gdb, SSH, sincronización de directorios y código postal. En los sistemas basados en Debian, puede usar este comando para instalar estas dependencias:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync zip
    ```

  * Visual Studio requiere una versión reciente de CMake en la máquina Linux que tiene habilitado el modo de servidor (al menos 3,8). Microsoft produce una compilación universal de CMake que se puede instalar en cualquier distribución de Linux. Se recomienda usar esta compilación para asegurarse de que tiene las características más recientes. Puede obtener los archivos binarios de CMake de [la bifurcación de Microsoft del repositorio de CMake](https://github.com/Microsoft/CMake/releases) en GitHub. Vaya a esa página y descargue la versión que coincida con la arquitectura del sistema en la máquina Linux y, a continuación, márquela como ejecutable:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Puede ver las opciones para ejecutar el script con `-–help`. Se recomienda usar la opción `–prefix` para especificar la instalación en la ruta de acceso de **/usr** , ya que **/usr/bin** es la ubicación predeterminada en la que Visual Studio busca CMake. En el ejemplo siguiente se muestra el script Linux-x86_64. Cámbielo según sea necesario si usa una plataforma de destino diferente.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Git para Windows instalado en el equipo Windows.
* Una cuenta de GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Clonación un proyecto de CMake de código abierto desde GitHub

En este tutorial se usa el SDK de la viñeta física en GitHub. Ofrece detección de colisiones y simulaciones físicas para muchas aplicaciones. El SDK incluye programas ejecutables de ejemplo que se compilan y ejecutan sin tener que escribir código adicional. En este tutorial no se modifican los scripts de código fuente o de compilación. Para empezar, Clone el repositorio *bullet3* de github en la máquina en la que tiene instalado Visual Studio.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. En el menú principal de Visual Studio, elija **archivo > abrir > CMake**. Navegue hasta el archivo archivo CMakeLists. txt en la raíz del repositorio de bullet3 que acaba de descargar.

    ![Menú de Visual Studio para Archivo > Abrir > CMake](media/cmake-open-cmake.png)

    En cuanto Abra la carpeta, la estructura de carpetas se vuelve visible en el **Explorador de soluciones**.

    ![Vista de carpetas en el Explorador de soluciones de Visual Studio](media/cmake-bullet3-solution-explorer.png)

    En esta vista se muestra exactamente lo que hay en el disco, no una vista filtrada o lógica. De forma predeterminada, los archivos ocultos no se muestran.

1. Elija el botón **Mostrar todos los archivos** para ver todos los archivos de la carpeta.

    ![Botón Mostrar todos los archivos del Explorador de soluciones de Visual Studio](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Cambio a la vista de destinos

Cuando se abre una carpeta que usa CMake, Visual Studio genera la caché de CMake de forma automática. Es posible que esta operación tarde unos minutos, en función del tamaño del proyecto.

1. En la **ventana Salida**, seleccione **Mostrar resultados desde** y después elija **CMake** para supervisar el estado del proceso de generación de la caché. Una vez completada la operación, se mostrará "Extracción de la información de destino realizada".

   ![Ventana Salida de Visual Studio en la que se muestra la salida de CMake](media/cmake-bullet3-output-window.png)

   Una vez finalizada esta operación, se configura IntelliSense. Puede compilar el proyecto y depurar la aplicación. Visual Studio ahora muestra una vista lógica de la solución, en función de los destinos especificados en los archivos archivo CMakeLists.

1. Pulse el botón **Soluciones y carpetas** situado en el **Explorador de soluciones** para cambiar a la vista de destinos de CMake.

   ![Botón Soluciones y carpetas del Explorador de soluciones para mostrar la vista de destinos de CMake](media/cmake-bullet3-show-targets.png)

   Este es el aspecto de esa vista para el SDK de Bullet:

   ![Vista de destinos de CMake del Explorador de soluciones](media/cmake-bullet3-targets-view.png)

   En la vista de destinos se proporciona una vista más intuitiva del contenido de esta base de código fuente. Puede ver que algunos destinos son bibliotecas y otros son archivos ejecutables.

1. Expanda un nodo en la vista de destinos de CMake para ver sus archivos de código fuente, siempre que se encuentren en el disco.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Adición de una configuración x64-Debug explícita de Windows

Visual Studio crea una configuración de **x64-Debug** predeterminada para Windows. Las configuraciones son cómo Visual Studio comprende qué plataforma de destino se va a usar para CMake. La configuración predeterminada no está representada en el disco. Cuando se agrega explícitamente una configuración, Visual Studio crea un archivo denominado *CMakeSettings. JSON*. Se rellena con la configuración de todas las configuraciones que especifique.

1. Agregue una nueva configuración. Abra la lista desplegable **configuración** en la barra de herramientas y seleccione **administrar configuraciones**.

   ![Menú desplegable Administrar configuraciones](media/cmake-bullet3-manage-configurations.png)

   Se abre el [Editor de configuración de CMake](customize-cmake-settings.md) . Seleccione el signo más verde en el lado izquierdo del editor para agregar una nueva configuración. Aparece el cuadro de diálogo **Agregar configuración a CMakeSettings** .

   ![Cuadro de diálogo Agregar configuración a CMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

   Este cuadro de diálogo muestra todas las configuraciones incluidas con Visual Studio, además de las configuraciones personalizadas que cree. Si desea seguir usando una configuración de **depuración x64** , debe ser la primera que agregue. Seleccione **x64-Debug**y elija el botón **seleccionar** . Visual Studio crea el archivo CMakeSettings. JSON con una configuración para **x64-Debug**y lo guarda en el disco. Puede usar los nombres que quiera para las configuraciones si cambia el parámetro de nombre directamente en CMakeSettings.json.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Establecer un punto de interrupción, compilar y ejecutar en Windows

En este paso, se depurará un programa de ejemplo que demuestra la biblioteca Bullet Physics.
  
1. En el **Explorador de soluciones**, haga clic en AppBasicExampleGui y expándalo.

1. Abra el archivo `BasicExample.cpp`.

1. Establezca un punto de interrupción que se alcance al hacer clic en la aplicación en ejecución. El evento de clic se controla en un método dentro de una clase auxiliar. Para acceder rápidamente a ese punto:

   1. Seleccione `CommonRigidBodyBase` desde la que se deriva el `BasicExample` de struct. Está alrededor de la línea 30.

   1. Haga clic con el botón derecho y seleccione **Ir a la definición**. Ahora está en el encabezado CommonRigidBodyBase. h.

   1. En la vista de explorador sobre el origen, debería ver que se encuentra en el `CommonRigidBodyBase`. A la derecha, puede seleccionar miembros para examinarlos. Abra la lista desplegable y seleccione `mouseButtonCallback` para ir a la definición de esa función en el encabezado.

      ![Barra de herramientas de lista de miembros de Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Coloque un punto de interrupción en la primera línea de esta función. Se alcanza al hacer clic en un botón del mouse dentro de la ventana de la aplicación, cuando se ejecuta en el depurador de Visual Studio.

1. Para iniciar la aplicación, seleccione la lista desplegable iniciar en la barra de herramientas. Es la que tiene el icono de reproducción verde que indica "seleccionar elemento de inicio". En el menú desplegable, seleccione AppBasicExampleGui. exe. El nombre del archivo ejecutable ahora se muestra en el botón de inicio:

   ![Lista desplegable de inicio de la barra de herramientas de Visual Studio para Seleccionar elemento de inicio](media/cmake-bullet3-launch-button.png)

1. Elija el botón Launch (iniciar) para compilar la aplicación y las dependencias necesarias y, a continuación, iníciela con el depurador de Visual Studio adjunto. Transcurridos unos instantes, aparece la aplicación en ejecución:

   ![Depuración de una aplicación de Windows en Visual Studio](media/cmake-bullet3-launched.png)

1. Mueva el mouse a la ventana de la aplicación, y después haga clic en un botón para desencadenar el punto de interrupción. El punto de interrupción vuelve a mostrar Visual Studio en primer plano y el editor muestra la línea donde se pone en pausa la ejecución. Puede inspeccionar las variables de la aplicación, los objetos, los subprocesos y la memoria, o recorrer el código de forma interactiva. Elija **continuar** para que se reanude la aplicación y, a continuación, salga de ella normalmente. O bien, detenga la ejecución dentro de Visual Studio mediante el botón detener.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Adición de una configuración de Linux y conexión al equipo remoto

1. Agregue una configuración de Linux. Haga clic con el botón derecho en el archivo CMakeSettings.json en la vista **Explorador de soluciones** y seleccione **Agregar configuración**. Verá el mismo cuadro de diálogo Agregar configuración a CMakeSettings que antes. Seleccione **Linux-Debug** esta vez y guarde el archivo CMakeSettings. JSON (Ctrl + s).

1. Seleccione **Linux-Debug** en el menú desplegable configuración.

   ![Lista desplegable de configuración de inicio con las opciones X64-Debug y Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

   Si es la primera vez que se conecta a un sistema Linux, aparece el cuadro de diálogo **conectar con el sistema remoto** .

   ![Cuadro de diálogo Conectarse con el sistema remoto de Visual Studio](media/cmake-bullet3-connection-manager.png)

   Si ya ha agregado una conexión remota, puede abrir esta ventana. para ello, vaya a **herramientas > opciones > Cross Platform > Connection Manager**.

1. Proporcione la [información de conexión a la máquina Linux](/cpp/linux/connect-to-your-remote-linux-computer) y elija **conectar**. Visual Studio agrega esa máquina como CMakeSettings. JSON como conexión predeterminada para **Linux-Debug**. También extrae los encabezados del equipo remoto, por lo que obtiene [IntelliSense específico para esa conexión remota](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Después, Visual Studio envía los archivos a la máquina remota y genera la memoria caché de CMake en el sistema remoto. Estos pasos pueden tardar algún tiempo, en función de la velocidad de la red y de la capacidad de la máquina remota. Sabrá que se ha completado cuando aparece el mensaje "extracción de información de destino" en la ventana de salida de CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Establecimiento de un punto de interrupción, compilación y ejecución en Linux

Dado que se trata de una aplicación de escritorio, debe proporcionar información de configuración adicional a la configuración de depuración.

1. En la vista de destinos de CMake, haga clic con el botón derecho en AppBasicExampleGui y elija **depurar e iniciar configuración** para abrir el archivo Launch. vs. JSON que se encuentra en la subcarpeta Hidden **. vs** . Este archivo es local para el entorno de desarrollo. Puede moverlo a la raíz del proyecto si quiere insertarlo en el repositorio y guardarlo con su equipo. En este archivo, se ha agregado una configuración para AppBasicExampleGui. Estos valores predeterminados funcionan en la mayoría de los casos, pero no aquí. Dado que se trata de una aplicación de escritorio, debe proporcionar información adicional para iniciar el programa para que pueda verlo en el equipo Linux.

1. Para buscar el valor de la variable de entorno `DISPLAY` en el equipo Linux, ejecute este comando:

   ```cmd
   echo $DISPLAY
   ```

   En la configuración de AppBasicExampleGui, hay una matriz de parámetros, "pipeArgs". Contiene una línea: "$ {debuggerCommand}". Es el comando que inicia gdb en el equipo remoto. Visual Studio debe exportar la presentación en este contexto antes de que se ejecute el comando. Por ejemplo, si el valor de la pantalla es `:1`, modifique esa línea como se indica a continuación:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Inicie y depure la aplicación. Abra la lista desplegable **Seleccionar elemento de inicio** en la barra de herramientas y elija **AppBasicExampleGui**. A continuación, elija el icono de reproducción verde en la barra de herramientas o presione **F5**. La aplicación y sus dependencias se compilan en el equipo de Linux remoto y, a continuación, se inician con el depurador de Visual Studio adjunto. En el equipo Linux remoto, debería abrirse una ventana de aplicación.

1. Mueva el mouse a la ventana de la aplicación y haga clic en un botón. Se alcanza el punto de interrupción. La ejecución del programa se pausa, Visual Studio vuelve al primer plano y verá el punto de interrupción. También debería ver una ventana de la consola de Linux en Visual Studio. La ventana proporciona la salida del equipo Linux remoto y también puede aceptar la entrada de `stdin`. Al igual que cualquier ventana de Visual Studio, puede acoplarla donde prefiera verla. Su posición se conserva en futuras sesiones.

   ![Ventana de la consola de Linux en Visual Studio](media/cmake-bullet3-linux-console.png)

1. Puede inspeccionar las variables, objetos, subprocesos y memoria de la aplicación, y recorrer el código de forma interactiva mediante Visual Studio. Pero esta vez, lo está haciendo todo en un equipo Linux remoto en lugar de en su entorno local de Windows. Puede elegir **continuar** para permitir que la aplicación se reanude y salga normalmente, o bien puede elegir el botón detener, al igual que con la ejecución local.

1. Examine la ventana Pila de llamadas para ver las llamadas a `x11OpenGLWindow` desde que Visual Studio inició la aplicación en Linux.

   ![Ventana Pila de llamadas en la que se muestra la pila de llamadas de Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Qué ha aprendido

En este tutorial, ha clonado una base de código directamente desde GitHub. Ha generado, ejecutado y depurado en Windows sin modificaciones. Después, usó la misma base de código, con cambios de configuración menores, para compilar, ejecutar y depurar en una máquina remota de Linux.

## <a name="next-steps"></a>Pasos siguientes

Más información sobre cómo configurar y depurar proyectos de CMake en Visual Studio:

> [!div class="nextstepaction"]
> [Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)<br/><br/>
> [Conexión al equipo remoto de Linux](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Personalización de la configuración de compilación de CMake](customize-cmake-settings.md)<br/><br/>
> [Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)
>
