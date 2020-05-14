---
title: Creación de proyectos multiplataforma de C++ en Visual Studio
description: Cómo configurar, compilar y depurar un proyecto de CMake de código abierto de C++ en Visual Studio destinado a Windows y Linux.
ms.topic: tutorial
ms.date: 01/08/2020
ms.openlocfilehash: aac536f488cf22adf5aa835c9fe5b884fc5d7298
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328747"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Tutorial: Creación de proyectos multiplataforma de C++ en Visual Studio

El desarrollo de C y C++ en Visual Studio ya no es solo para Windows. En este tutorial se muestra cómo usar Visual Studio para el desarrollo de C++ multiplataforma en Windows y Linux. Se basa en CMake, por lo que no tiene que crear ni generar proyectos de Visual Studio. Cuando se abre una carpeta que contiene un archivo CMakeLists.txt, Visual Studio configura IntelliSense y las opciones compilación de forma automática. Puede empezar a editar, compilar y depurar el código rápidamente de forma local en Windows. A continuación, puede cambiar la configuración para hacer lo mismo en Linux, todo ello desde Visual Studio.

En este tutorial aprenderá a:

> [!div class="checklist"]
>
> * Clonar un proyecto de CMake de código abierto desde GitHub
> * Abrir el proyecto en Visual Studio
> * Compilar y depurar un destino ejecutable en Windows
> * Agregar una conexión a un equipo Linux
> * Compilar y depurar el mismo destino en Linux

## <a name="prerequisites"></a>Requisitos previos

* Configuración de Visual Studio para el desarrollo multiplataforma de C++
  * En primer lugar, [instale Visual Studio](https://visualstudio.microsoft.com/vs/) y elija las cargas de trabajo **Desarrollo para el escritorio con C++** y **Desarrollo de Linux con C++** . La instalación mínima es de solo 3 GB. En función de la velocidad de descarga, la instalación no debería tardar más de 10 minutos.

* Configuración de un equipo Linux para el desarrollo multiplataforma con C++
  * Visual Studio no requiere ninguna distribución específica de Linux. El sistema operativo se puede ejecutar en una máquina física, en una máquina virtual o en la nube. También puede usar el Subsistema de Windows para Linux (WSL). Sin embargo, para este tutorial se requiere un entorno gráfico. No se recomienda WSL en este caso porque está diseñado principalmente para operaciones de línea de comandos.
  * Visual Studio requiere estas herramientas en la máquina Linux: compiladores de C++, gdb, ssh, rsync, ninja y zip. En sistemas basados en Debian, puede usar este comando para instalar estas dependencias:

    ```cmd
    sudo apt install -y openssh-server build-essential gdb rsync ninja-build zip
    ```

  * Visual Studio requiere una versión reciente de CMake en la máquina Linux que tiene el modo de servidor habilitado (al menos la versión 3.8). Microsoft produce una compilación universal de CMake que se puede instalar en cualquier distribución de Linux. Se recomienda usar esta compilación para asegurarse de tener las características más recientes. Puede obtener los archivos binarios de CMake de [la bifurcación de Microsoft del repositorio de CMake](https://github.com/Microsoft/CMake/releases) en GitHub. Vaya a esa página y descargue la versión que coincida con la arquitectura del sistema de la máquina Linux, y después márquela como archivo ejecutable:

    ```cmd
    wget <path to binary>
    chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```

  * Puede ver las opciones para ejecutar el script con `-–help`. Se recomienda usar la opción `–prefix` para especificar la instalación en la ruta de acceso **/usr**, ya que **/usr/bin** es la ubicación predeterminada donde Visual Studio busca CMake. En el ejemplo siguiente se muestra el script Linux-x86_64. Puede cambiarlo según sea necesario si usa otra plataforma de destino.

    ```cmd
    sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr
    ```

* Git para Windows instalado en el equipo Windows.
* Una cuenta de GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Clonación un proyecto de CMake de código abierto desde GitHub

En este tutorial se usa el SDK Bullet Physics en GitHub. Proporciona detección de colisiones y simulaciones físicas para muchas aplicaciones. El SDK incluye programas ejecutables de ejemplo que se compilan y ejecutan sin necesidad de escribir código adicional. En este tutorial no se modifica ningún script de código fuente o de compilación. Para empezar, clone el repositorio *bullet3* desde GitHub en la máquina donde haya instalado Visual Studio.

```cmd
git clone https://github.com/bulletphysics/bullet3.git
```

1. En el menú principal de Visual Studio, seleccione **Archivo > Abrir > CMake**. Navegue hasta el archivo CMakeLists.txt en la raíz del repositorio bullet3 que acaba de descargar.

    ![Menú de Visual Studio para Archivo > Abrir > CMake](media/cmake-open-cmake.png)

    Al abrir la carpeta, la estructura de carpetas será visible en el **Explorador de soluciones**.

    ![Vista de carpetas en el Explorador de soluciones de Visual Studio](media/cmake-bullet3-solution-explorer.png)

    En esta vista se muestra exactamente lo que hay en el disco, no una vista filtrada o lógica. De forma predeterminada, los archivos ocultos no se muestran.

1. Haga clic en el botón **Mostrar todos los archivos** para ver todos los archivos de la carpeta.

    ![Botón Mostrar todos los archivos del Explorador de soluciones de Visual Studio](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Cambio a la vista de destinos

Cuando se abre una carpeta que usa CMake, Visual Studio genera la caché de CMake de forma automática. Es posible que esta operación tarde unos minutos, en función del tamaño del proyecto.

1. En la **ventana Salida**, seleccione **Mostrar resultados desde** y después elija **CMake** para supervisar el estado del proceso de generación de la caché. Una vez completada la operación, se mostrará "Extracción de la información de destino realizada".

   ![Ventana Salida de Visual Studio en la que se muestra la salida de CMake](media/cmake-bullet3-output-window.png)

   Una vez completada esta operación, IntelliSense está configurado. Ya puede compilar el proyecto y depurar la aplicación. Ahora Visual Studio muestra una vista lógica de la solución en función de los destinos especificados en los archivos CMakeLists.

1. Pulse el botón **Soluciones y carpetas** situado en el **Explorador de soluciones** para cambiar a la vista de destinos de CMake.

   ![Botón Soluciones y carpetas del Explorador de soluciones para mostrar la vista de destinos de CMake](media/cmake-bullet3-show-targets.png)

   Este es el aspecto de esa vista para el SDK de Bullet:

   ![Vista de destinos de CMake del Explorador de soluciones](media/cmake-bullet3-targets-view.png)

   En la vista de destinos se proporciona una vista más intuitiva del contenido de esta base de código fuente. Puede ver que algunos destinos son bibliotecas y otros son archivos ejecutables.

1. Expanda un nodo en la vista de destinos de CMake para ver sus archivos de código fuente, siempre que se encuentren en el disco.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Adición de una configuración x64-Debug explícita de Windows

Visual Studio crea una configuración **x64-Debug** predeterminada para Windows. Las configuraciones son cómo Visual Studio comprende qué plataforma de destino se va a usar para CMake. La configuración predeterminada no está representada en el disco. Cuando se agrega explícitamente una configuración, Visual Studio crea un archivo denominado *CMakeSettings.josn*. Se rellena con la configuración de todas las opciones que especifique.

1. Agregue una nueva configuración. Abra el menú desplegable **Configuración** en la barra de herramientas y seleccione **Administrar configuraciones**.

   ![Menú desplegable Administrar configuraciones](media/cmake-bullet3-manage-configurations.png)

   Se abrirá el [Editor de configuración de CMake](customize-cmake-settings.md). Seleccione el signo más de color verde situado en el lado izquierdo del editor para agregar una nueva configuración. Se abrirá el cuadro de diálogo **Agregar configuración a CMakeSettings**.

   ![Cuadro de diálogo Agregar configuración a CMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

   En este cuadro de diálogo se muestran todas las configuraciones incluidas con Visual Studio, así como las configuraciones personalizadas que crea. Si quiere seguir usando una configuración **x64-Debug**, esa tendrá que ser la primera que agregue. Seleccione **x64-Debug** y, a continuación, haga clic en el botón **Seleccionar**. Visual Studio crea el archivo CMakeSettings.json con una configuración para **x64-Debug** y lo guarda en el disco. Puede usar los nombres que quiera para las configuraciones si cambia el parámetro de nombre directamente en CMakeSettings.json.

## <a name="set-a-breakpoint-build-and-run-on-windows"></a>Establecimiento de un punto de interrupción, compilación y ejecución en Windows

En este paso, se depurará un programa de ejemplo que demuestra la biblioteca Bullet Physics.
  
1. En el **Explorador de soluciones**, haga clic en AppBasicExampleGui y expándalo.

1. Abra el archivo `BasicExample.cpp`.

1. Establezca un punto de interrupción que se alcance al hacer clic en la aplicación en ejecución. El evento de clic se controla en un método dentro de una clase auxiliar. Para acceder rápidamente a ese punto:

   1. Seleccione `CommonRigidBodyBase`, de donde se deriva el struct `BasicExample`. Aproximadamente en la línea 30.

   1. Haga clic con el botón derecho y seleccione **Ir a la definición**. Ahora está en el encabezado CommonRigidBodyBase.h.

   1. En la vista de explorador encima del origen, debería ver que se encuentra en `CommonRigidBodyBase`. A la derecha, puede seleccionar miembros para examinarlos. Abra la lista desplegable y seleccione `mouseButtonCallback` para ir a la definición de esa función en el encabezado.

      ![Barra de herramientas de lista de miembros de Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Coloque un punto de interrupción en la primera línea de esta función. Se alcanzará al hacer clic en un botón del mouse en la ventana de la aplicación cuando se ejecute en el depurador de Visual Studio.

1. Para iniciar la aplicación, haga clic en la lista desplegable de inicio en la barra de herramientas. Es la que tiene el icono de reproducción verde que indica "Seleccionar elemento de inicio". En la lista desplegable, seleccione AppBasicExampleGui.exe. El nombre del archivo ejecutable ahora se muestra en el botón de inicio:

   ![Lista desplegable de inicio de la barra de herramientas de Visual Studio para Seleccionar elemento de inicio](media/cmake-bullet3-launch-button.png)

1. Seleccione el botón de inicio para compilar la aplicación y las dependencias necesarias, y después iníciela con el depurador de Visual Studio asociado. Transcurridos unos instantes, aparece la aplicación en ejecución:

   ![Depuración de una aplicación de Windows en Visual Studio](media/cmake-bullet3-launched.png)

1. Mueva el mouse a la ventana de la aplicación, y después haga clic en un botón para desencadenar el punto de interrupción. Este punto de interrupción devuelve Visual Studio al primer plano y en el editor se muestra la línea donde se ha detenido la ejecución. Puede inspeccionar las variables, los objetos, los subprocesos y la memoria de la aplicación, o recorrer el código de forma interactiva. Haga clic en **Continuar** para que se reanude la aplicación y, a continuación, salga de ella normalmente. O bien, detenga la ejecución en Visual Studio con el botón de detención.

## <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Adición de una configuración de Linux y conexión al equipo remoto

1. Agregue una configuración de Linux. Haga clic con el botón derecho en el archivo CMakeSettings.json en la vista **Explorador de soluciones** y seleccione **Agregar configuración**. Verá el mismo cuadro de diálogo Agregar configuración a CMakeSettings que antes. En esta ocasión, seleccione **Linux-Debug** y después guarde el archivo CMakeSettings.json (Ctrl+S).

1. Seleccione **Linux-Debug** en la lista desplegable de configuración.

   ![Lista desplegable de configuración de inicio con las opciones X64-Debug y Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

   Si es la primera vez que se conecta a un sistema Linux, se abrirá el cuadro de diálogo **Conectar con el sistema remoto**.

   ![Cuadro de diálogo Conectarse con el sistema remoto de Visual Studio](media/cmake-bullet3-connection-manager.png)

   Si ya ha agregado una conexión remota, puede abrir esta ventana si selecciona **Herramientas > Opciones > Multiplataforma > Administrador de conexiones**.

1. Proporcione la [información de conexión a la máquina Linux](/cpp/linux/connect-to-your-remote-linux-computer) y seleccione **Conectar**. Visual Studio agrega esa máquina a CMakeSettings.json como conexión predeterminada para **Linux-Debug**. También extrae los encabezados de la máquina remota, por lo que obtiene [IntelliSense específico de esa conexión remota](/cpp/linux/configure-a-linux-project?view=vs-2019#remote_intellisense). Después, Visual Studio envía los archivos a la máquina remota y genera la caché de CMake en el sistema remoto. Estos pasos pueden tardar algún tiempo según la velocidad de la red y la potencia de la máquina remota. Sabrá que ha terminado cuando vea el mensaje "Extracción de la información de destino realizada" en la ventana de salida de CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Establecimiento de un punto de interrupción, compilación y ejecución en Linux

Como se trata de una aplicación de escritorio, debe proporcionar información de configuración adicional a la configuración de depuración.

1. En la vista de destinos de CMake, haga clic con el botón derecho en AppBasicExampleGui y seleccione **Configuración de depuración e inicio** para abrir el archivo launch.vs.json que se encuentra en la subcarpeta oculta **.vs**. Este archivo es local para el entorno de desarrollo. Puede moverlo a la raíz del proyecto si quiere insertarlo en el repositorio y guardarlo con su equipo. En este archivo se ha agregado una configuración para AppBasicExampleGui. Esta configuración predeterminada funciona en la mayoría de los casos, pero no aquí. Al tratarse de una aplicación de escritorio, tendrá que proporcionar información adicional para iniciar el programa de forma que lo pueda ver en su máquina Linux.

1. Para buscar el valor de la variable de entorno `DISPLAY` en la máquina Linux, ejecute este comando:

   ```cmd
   echo $DISPLAY
   ```

   En la configuración de AppBasicExampleGui hay una matriz de parámetros "pipeArgs". Contiene una línea "${debuggerCommand}". Es el comando que inicia gdb en la máquina remota. Visual Studio tiene que exportar la presentación a este contexto antes de que se ejecute ese comando. Por ejemplo, si el valor de la pantalla es `:1`, modifique esa línea de esta forma:

   ```cmd
   "export DISPLAY=:1;${debuggerCommand}",
   ```

1. Ejecute y depure la aplicación. Abra el menú desplegable **Seleccionar elemento de inicio** en la barra de herramientas y elija **AppBasicExampleGui**. A continuación, elija el icono de reproducción verde situado en la barra de herramientas o presione **F5**. La aplicación y sus dependencias se compilan en la máquina remota Linux y, después, se inician con el depurador de Visual Studio asociado. En el equipo Linux remoto, debería abrirse una ventana de aplicación.

1. Mueva el mouse a la ventana de la aplicación y haga clic en un botón. Se alcanza el punto de interrupción. La ejecución del programa se detiene, Visual Studio vuelve al primer plano y ve el punto de interrupción. También debería ver una ventana de la consola de Linux en Visual Studio. En esta ventana se proporciona la salida del equipo Linux remoto, y también puede aceptar la entrada para `stdin`. Como cualquier ventana de Visual Studio, puede acoplarla donde prefiera para verla. Su posición se conservará en futuras sesiones.

   ![Ventana de la consola de Linux en Visual Studio](media/cmake-bullet3-linux-console.png)

1. Puede inspeccionar las variables, objetos, subprocesos y memoria de la aplicación, y recorrer el código de forma interactiva mediante Visual Studio. Pero, en esta ocasión, lo hará todo en una máquina Linux remota, en lugar de en el entorno local de Windows. Puede seleccionar **Continuar** para permitir que la aplicación se reanude y salir de ella normalmente, o bien pulsar el botón de detención, como en la ejecución local.

1. Examine la ventana Pila de llamadas para ver las llamadas a `x11OpenGLWindow` desde que Visual Studio inició la aplicación en Linux.

   ![Ventana Pila de llamadas en la que se muestra la pila de llamadas de Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Qué ha aprendido

En este tutorial, ha clonado un código base directamente desde GitHub. Lo ha generado, ejecutado y depurado en Windows sin modificaciones. A continuación, ha usado el mismo código base, con cambios de configuración mínimos, para compilarlo, ejecutarlo y depurarlo en una máquina Linux remota.

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
