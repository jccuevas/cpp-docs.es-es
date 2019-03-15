---
title: Creación de proyectos multiplataforma de C++ en Visual Studio
description: En este tutorial se muestra cómo configurar, compilar y depurar un proyecto de CMake de código abierto de C++ en Visual Studio destinado a Windows y Linux.
author: mikeblome
ms.topic: tutorial
ms.date: 03/05/2019
ms.openlocfilehash: deb2c91d6d09d8945e5eb57a7ac742c5b1705e83
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826377"
---
# <a name="tutorial-create-c-cross-platform-projects-in-visual-studio"></a>Tutorial: Creación de proyectos multiplataforma de C++ en Visual Studio 

El desarrollo de C y C++ en Visual Studio ya no es solo para Windows. En este tutorial se muestra cómo usar Visual Studio para el desarrollo multiplataforma de C++ basado en CMake sin tener que crear o generar proyectos de Visual Studio. Cuando se abre una carpeta que contiene un archivo CMakeLists.txt, Visual Studio configura de forma automática IntelliSense y las opciones compilación. Puede editar, generar y depurar el código rápidamente de forma local en Windows y, después, cambiar la configuración para hacer lo mismo en Linux, todo ello desde dentro de Visual Studio.

En este tutorial aprenderá a:

> [!div class="checklist"]
> * Clonar un proyecto de CMake de código abierto desde GitHub
> * Abrir el proyecto en Visual Studio 
> * Compilar y depurar un destino ejecutable en Windows
> * Agregar una conexión a un equipo Linux
> * Compilar y depurar el mismo destino en Linux

## <a name="prerequisites"></a>Requisitos previos

- Configuración de Visual Studio para el desarrollo multiplataforma de C++
    - Primero, necesita tener [Visual Studio instalado](https://visualstudio.microsoft.com/vs/). A continuación, confirme que tiene instaladas las cargas de trabajo **Desarrollo para el escritorio con C++** y **Desarrollo de Linux con C++**. La instalación mínima es de solo 3 GB; en función de la velocidad de descarga no debería tardar más de 10 minutos.
- Configuración de un equipo Linux para el desarrollo multiplataforma con C++
    - Visual Studio no requiere ninguna distribución específica de Linux. El sistema operativo se puede ejecutar en un equipo físico, una máquina virtual, la nube o el subsistema de Windows para Linux (WSL). Pero para este tutorial se requiere un entorno gráfico; por tanto, no se recomienda WSL porque está diseñado principalmente para operaciones de línea de comandos.
    - Las herramientas que Visual Studio requiere en el equipo Linux son las siguientes: compiladores de C++, GDB, ssh y zip. En sistemas basados en Debian, puede instalar estas dependencias como sigue.
    
    ```cmd
        sudo apt install -y openssh-server build-essential gdb zip
    ```
    - Visual Studio requiere que el equipo Linux tenga una versión reciente de CMake con el modo de servidor habilitado (al menos la versión 3.8). Microsoft produce una compilación universal de CMake que se puede instalar en cualquier distribución de Linux. Se recomienda usar esta compilación para asegurarse de tener las características más recientes. Puede obtener los archivos binarios de CMake de [la bifurcación de Microsoft del repositorio de CMake](https://github.com/Microsoft/CMake/releases) en GitHub. Vaya a esa página y descargue la versión que coincida con la arquitectura del sistema del equipo Linux, y después márquela como archivo ejecutable:
    
    ```cmd
        wget <path to binary>
        chmod +x cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh
    ```
    - Puede ver las opciones para ejecutar el script con `-–help`. Se recomienda usar la opción `–prefix` para especificar la instalación en la ruta de acceso **/usr/local**, ya que es la ubicación predeterminada donde Visual Studio busca CMake. En el ejemplo siguiente se muestra el script Linux-x86_64. Puede cambiarlo según sea necesario si usa otra plataforma de destino. 
    
    ```cmd
        sudo ./cmake-3.11.18033000-MSVC_2-Linux-x86_64.sh --skip-license --prefix=/usr/local
    ```
- Git para Windows instalado en el equipo Windows.
- Una cuenta de GitHub.

## <a name="clone-an-open-source-cmake-project-from-github"></a>Clonación un proyecto de CMake de código abierto desde GitHub

En este tutorial se usa el SDK Bullet Physics en GitHub, que proporciona detección de colisiones y simulaciones físicas para una variedad de aplicaciones diferentes. Incluye programas ejecutables de ejemplo que se compilan y ejecutan sin necesidad de escribir código adicional. En este tutorial no se modifica ningún script de código fuente o compilación. Para empezar, clone el repositorio bullet3 desde GitHub en el equipo donde haya instalado Visual Studio. 

```cmd

git clone https://github.com/bulletphysics/bullet3.git

```

1. En el menú principal de Visual Studio, seleccione **Archivo > Abrir > CMake** y navegue hasta el archivo CMakeLists.txt en la raíz del repositorio bullet3 que acaba de descargar.

    ![Menú de Visual Studio para Archivo > Abrir > CMake](media/cmake-open-cmake.png)

    Al abrir la carpeta, la estructura de carpetas será visible en el **Explorador de soluciones**.

    ![Vista de carpetas en el Explorador de soluciones de Visual Studio](media/cmake-bullet3-solution-explorer.png)

    En esta vista se muestra exactamente lo que hay en el disco, no una vista filtrada o lógica. De forma predeterminada, los archivos ocultos no se muestran. 

2. Presione el botón **Mostrar todos los archivos** para ver todos los archivos de la carpeta.

    ![Botón Mostrar todos los archivos del Explorador de soluciones de Visual Studio](media/cmake-bullet3-show-all-files.png)

## <a name="switch-to-targets-view"></a>Cambio a la vista de destinos

Cuando se abre una carpeta que usa CMake, Visual Studio genera la caché de CMake de forma automática. Es posible que esta operación tarde unos minutos, en función del tamaño del proyecto. 

1. En la **ventana Salida**, seleccione **Mostrar resultados desde** y después elija **CMake** para supervisar el estado del proceso de generación de la caché. Una vez completada la operación, se mostrará "Extracción de la información de destino realizada".

    ![Ventana Salida de Visual Studio en la que se muestra la salida de CMake](media/cmake-bullet3-output-window.png)

    Una vez completada esta operación, IntelliSense está configurado, se puede compilar el proyecto y se puede depurar la aplicación. Ahora Visual Studio puede proporcionar una vista lógica de la solución en función de los destinos especificados en los archivos de lista de CMake. 

2. Pulse el botón **Soluciones y carpetas** situado en el **Explorador de soluciones** para cambiar a la vista de destinos de CMake.

    ![Botón Soluciones y carpetas del Explorador de soluciones para mostrar la vista de destinos de CMake](media/cmake-bullet3-show-targets.png)

    Este es el aspecto de esa vista para el SDK de Bullet:

    ![Vista de destinos de CMake del Explorador de soluciones](media/cmake-bullet3-targets-view.png)

    En la vista de destinos se proporciona una vista más intuitiva del contenido de esta base de código fuente. Puede ver que algunos destinos son bibliotecas y otros son archivos ejecutables. 

3. Expanda un nodo en la vista de destinos de CMake para ver sus archivos de código fuente, siempre que se encuentren en el disco.

## <a name="set-a-breakpoint-build-and-run"></a>Establecimiento de un punto de interrupción, compilación y ejecución

En este paso, se depurará un programa de ejemplo que demuestra la biblioteca Bullet Physics.
  
1. En el **Explorador de soluciones**, haga clic en AppBasicExampleGui y expándalo. 
1. Abra el archivo `BasicExample.cpp`. 
1. Establezca un punto de interrupción que se alcance al hacer clic en la aplicación en ejecución. El evento de clic se controla en un método dentro de una clase auxiliar. Para acceder rápidamente a ese punto:

    1. Seleccione `CommonRigidBodyBase`, de donde se deriva la struct `BasicExample`, aproximadamente en la línea 30.
    1. Haga clic con el botón derecho y seleccione **Ir a la definición**. Ahora está en el encabezado CommonRigidBodyBase.h. 
    1. En la vista de explorador anterior, el código fuente debe mostrar que se encuentra en `CommonRigidBodyBase`. A la derecha, puede seleccionar miembros para examinarlos. Haga clic en la lista desplegable y seleccione `mouseButtonCallback` para ir a la definición de esa función en el encabezado.

        ![Barra de herramientas de lista de miembros de Visual Studio](media/cmake-bullet3-member-list-toolbar.png)

1. Coloque un punto de interrupción en la primera línea de esta función. A este punto se llegará al hacer clic en un botón del mouse en la ventana de la aplicación cuando se inicia en el depurador de Visual Studio.

1. Para iniciar la aplicación, haga clic en la lista desplegable de inicio con el icono de reproducción que indica "Seleccionar elemento de inicio" en la barra de herramientas. En la lista desplegable, seleccione AppBasicExampleGui.exe. El nombre del archivo ejecutable ahora se muestra en el botón de inicio:

    ![Lista desplegable de inicio de la barra de herramientas de Visual Studio para Seleccionar elemento de inicio](media/cmake-bullet3-launch-button.png)

5.  Presione el botón de inicio para compilar la aplicación y las dependencias necesarias, y después iníciela con el depurador de Visual Studio asociado. Transcurridos unos instantes, aparece la aplicación en ejecución:

    ![Depuración de una aplicación de Windows en Visual Studio](media/cmake-bullet3-launched.png)

6. Mueva el mouse a la ventana de la aplicación, y después haga clic en un botón para desencadenar el punto de interrupción. Esta acción devuelve Visual Studio al primer plano y en el editor se muestra la línea donde se ha detenido la ejecución. Podrá inspeccionar las variables, objetos, subprocesos y memoria de la aplicación. Puede recorrer el código de forma interactiva. Puede hacer clic en **Continuar** para permitir que la aplicación se reanude y salir de ella normalmente, o bien cancelar la ejecución en Visual Studio con el botón de detención.

## <a name="add-an-explicit-windows-x64-debug-configuration"></a>Adición de una configuración x64-Debug explícita de Windows

Hasta ahora, ha usado la configuración **x64-Debug** predeterminada para Windows. Las configuraciones son cómo Visual Studio comprende qué plataforma de destino se va a usar para CMake. La configuración predeterminada no está representada en el disco. Cuando se agrega una configuración de forma explícita, Visual Studio crea un archivo denominado CMakeSettings.json que se rellena con las opciones de todas las configuraciones que se especifiquen. 

1. Para agregar una configuración nueva, haga clic en el menú desplegable Configuración de la barra de herramientas y seleccione **Administrar configuraciones...**.

    ![Menú desplegable Administrar configuraciones](media/cmake-bullet3-manage-configurations.png)

    Se abrirá el cuadro de diálogo **Agregar configuración a CMakeSettings**.

    ![Cuadro de diálogo Agregar configuración a CMakeSettings](media/cmake-bullet3-add-configuration-x64-debug.png)

    En este cuadro de diálogo se muestran todas las configuraciones incluidas con Visual Studio, así como las configuraciones personalizadas que pueda crear. Si quiere seguir usando la configuración **x64-Debug** predeterminada, tendrá que ser la primera que agregue. Al agregar esa configuración, podrá alternar entre configuraciones de Windows y Linux. Seleccione **x64-Debug** y haga clic en **Seleccionar**. Esto crea el archivo CMakeSettings.json con una configuración para **x64-Debug** y cambia Visual Studio para que la use en lugar de la predeterminada. Verá que en la lista desplegable de configuración ya no se incluye "(predeterminada)" como parte del nombre. Puede usar los nombres que quiera para las configuraciones si cambia el parámetro de nombre directamente en CMakeSettings.json.

##  <a name="add-a-linux-configuration-and-connect-to-the-remote-machine"></a>Adición de una configuración de Linux y conexión al equipo remoto

1. Ahora agregará una configuración de Linux. Haga clic con el botón derecho en el archivo CMakeSettings.json en la vista **Explorador de soluciones** y seleccione **Agregar configuración**. Verá el mismo cuadro de diálogo Agregar configuración a CMakeSettings que antes. En esta ocasión, seleccione **Linux-Debug** y después guarde el archivo CMakeSettings.json. 
2. Ahora, seleccione **Linux-Debug** en la lista desplegable de configuración.

    ![Lista desplegable de configuración de inicio con las opciones X64-Debug y Linux-Debug](media/cmake-bullet3-linux-configuration-item.png)

    Si es la primera vez que se conecta a un sistema Linux, se abrirá el cuadro de diálogo **Conectarse con el sistema remoto**.

    ![Cuadro de diálogo Conectarse con el sistema remoto de Visual Studio](media/cmake-bullet3-connection-manager.png)

    Si ya ha agregado una conexión remota, puede abrir esta ventana si selecciona **Herramientas > Opciones > Multiplataforma > Administrador de conexiones**.
 
3. Proporcione la información de conexión al equipo Linux y haga clic en **Conectar**. Visual Studio agrega ese equipo a CMakeSettings.json como valor predeterminado para **Linux-Debug**. También extraerá los encabezados del equipo remoto para que obtenga IntelliSense específico de ese equipo cuando lo use. Ahora, Visual Studio enviará los archivos al equipo remoto, donde después generará la caché de CMake, y cuando termine, se configurará para usar la misma base de código fuente con ese equipo Linux remoto. Estos pasos pueden tardar algún tiempo según la velocidad de la red y la potencia del equipo remoto. Sabrá que ha terminado cuando vea el mensaje "Extracción de la información de destino realizada" en la ventana de salida de CMake.

## <a name="set-a-breakpoint-build-and-run-on-linux"></a>Establecimiento de un punto de interrupción, compilación y ejecución en Linux

Como se trata de una aplicación de escritorio, debe proporcionar información de configuración adicional a la configuración de depuración. 

1. En la vista de destinos de CMake, haga clic con el botón derecho en AppBasicExampleGui y seleccione **Configuración de depuración e inicio** para abrir el archivo launch.vs.json que se encuentra en la subcarpeta oculta **.vs**. Este archivo es local para el entorno de desarrollo. Puede moverlo a la raíz del proyecto si quiere insertarlo en el repositorio y guardarlo con su equipo. En este archivo se ha agregado una configuración para AppBasicExampleGui. Esta configuración predeterminada funciona en la mayoría de los casos, pero al tratarse de una aplicación de escritorio, tendrá que proporcionar información adicional para iniciar el programa de forma que lo pueda ver en el equipo Linux. 
2. Debe conocer el valor de la variable de entorno `DISPLAY` en el equipo Linux; ejecute este comando para obtenerlo.

    ```cmd
    echo $DISPLAY
    ```

    En la configuración de AppBasicExampleGui hay una matriz de parámetros "pipeArgs". En su interior hay una línea "${debuggerCommand}". Es el comando que inicia gdb en el equipo remoto. Visual Studio tiene que exportar la presentación a este contexto antes de que se ejecute ese comando. Por ejemplo, si el valor de la pantalla es :1, modifique esa línea de esta forma:

    ```cmd
    "export DISPLAY=:1;${debuggerCommand}",
    ```
3. Ahora, para iniciar y depurar la aplicación, haga clic en la lista desplegable **Seleccionar elemento de inicio** en la barra de herramientas y elija AppBasicExampleGui. Pulse ese botón o presione **F5**. Con esta acción se compila la aplicación y sus dependencias necesarias en el equipo Linux remoto, y después se inicia con el depurador de Visual Studio asociado. En el equipo Linux remoto, debería abrirse una ventana de aplicación.

4. Mueva el mouse a la ventana de la aplicación, haga clic en un botón y llegará al punto de interrupción. La ejecución del programa se detiene, Visual Studio vuelve al primer plano y estará en el punto de interrupción. También debería ver una ventana de la consola de Linux en Visual Studio. En esta ventana se proporciona la salida del equipo Linux remoto, y también puede aceptar la entrada para `stdin`. Como cualquier ventana de Visual Studio, la puede acoplar donde prefiera para verla, y su posición se conservará en sesiones posteriores.

    ![Ventana de la consola de Linux en Visual Studio](media/cmake-bullet3-linux-console.png)

5. Puede inspeccionar las variables, objetos, subprocesos y memoria de la aplicación, y recorrer el código de forma interactiva mediante Visual Studio. Pero en esta ocasión lo hace todo en un equipo Linux remoto, en lugar del entorno local de Windows. Puede hacer clic en **Continuar** para permitir que la aplicación se reanude y salir de ella normalmente, o bien pulsar el botón de detención, como en la ejecución local.

6. Examine la ventana Pila de llamadas para ver las llamadas a `x11OpenGLWindow` desde que Visual Studio inició la aplicación en Linux.

    ![Ventana Pila de llamadas en la que se muestra la pila de llamadas de Linux](media/cmake-bullet3-linux-callstack.png)

## <a name="what-you-learned"></a>Qué ha aprendido 

En este tutorial, ha visto la clonación directa de una base de código desde GitHub y cómo se ha compilado, ejecutado y depurado en Windows sin modificaciones. La misma base de código, con cambios de configuración mínimos, se ha compilado, ejecutado y depurado en un equipo Linux remoto. 

## <a name="next-steps"></a>Pasos siguientes

Más información sobre cómo configurar y depurar proyectos de CMake en Visual Studio:

> [!div class="nextstepaction"]
> [Proyectos de CMake en Visual Studio](cmake-projects-in-visual-studio.md)<br/><br/>
> [Configuración de un proyecto de CMake en Linux](../linux/cmake-linux-project.md)<br/><br/>
> [Conexión al equipo remoto de Linux](../linux/connect-to-your-remote-linux-computer.md)<br/><br/>
> [Personalización de la configuración de compilación de CMake](customize-cmake-settings.md)<br/><br/>
> [Configuración de sesiones de depuración de CMake](configure-cmake-debugging-sessions.md)<br/><br/>
> [Implementación, ejecución y depuración del proyecto de Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/><br/>
> [Referencia de configuración predefinida de CMake](cmake-predefined-configuration-reference.md)
> 
