---
title: Instalación de la carga de trabajo de Linux para C++ en Visual Studio
description: En este artículo se describe cómo descargar, instalar y configurar la carga de trabajo de Linux para C++ en Visual Studio.
ms.date: 03/05/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 74155724abb3a0e02cc27dd8a8d144f142ee4b6f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747727"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Descargar, instalar y configurar la carga de trabajo de Linux

Puede usar el IDE de Visual Studio 2017 en Windows para crear, editar y depurar proyectos de C++ que se ejecutan en un equipo físico Linux, una máquina virtual o el [subsistema de Windows para Linux](/windows/wsl/about). 

Puede trabajar en la base de código existente que usa CMake o cualquier otro sistema de compilación sin tener que convertirla en un proyecto de Visual Studio. Si la base de código es multiplataforma, puede tener como destino Windows y Linux desde dentro de Visual Studio. Por ejemplo, puede editar y depurar el código y generar perfiles de este en Windows con Visual Studio y, después, rápidamente redestinar el proyecto para que Linux realice más pruebas. Los archivos de encabezado de Linux se copian automáticamente en el equipo local, donde Visual Studio los usa para proporcionar compatibilidad completa con IntelliSense (finalización de instrucciones, Ir a definición, etc.).
 
Para cualquiera de estos escenarios, se requiere la carga de trabajo de **desarrollo de Linux con C++**. 

## <a name="visual-studio-setup"></a>Instalación de Visual Studio

1. Escriba "Instalador de Visual Studio" en el cuadro de búsqueda de Windows: ![Cuadro de búsqueda de Windows](media/visual-studio-installer-search.png)
2. Busque el instalador en los resultados de la categoría **Aplicaciones** y haga doble clic en este. Cuando se abra el instalador, elija **Modificar** y después haga clic en la pestaña **Cargas de trabajo**. Desplácese hacia abajo hasta **Otros conjuntos de herramientas** y seleccione la carga de trabajo **Desarrollo de Linux con C++**.

   ![Carga de trabajo Visual C++ for Linux Development](media/linuxworkload.png)

1. Si utiliza CMake o tiene como destino plataformas incrustadas o IoT, vaya al panel **Detalles de la instalación** de la derecha, debajo de **Desarrollo de Linux con C++**, expanda **Componentes opcionales** y elija los componentes que necesita.

    **Visual Studio 2017, versión 15.4 y posteriores**<br/>: Al instalar la carga de trabajo C++ de Linux para Visual Studio, se activa de forma predeterminada la compatibilidad de CMake con Linux.

1. Haga clic en **Modificar** para continuar con la instalación.

## <a name="options-for-creating-a-linux-environment"></a>Opciones para crear un entorno Linux

Si no dispone de una máquina Linux, puede crear una máquina virtual Linux en Azure. Para obtener más información, vea [Inicio rápido: Creación de una máquina virtual Linux en Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

Otra opción, en Windows 10, es activar el subsistema Windows para Linux. Para más información, vea la [guía de instalación de Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup-ubuntu"></a>Instalación de Linux: Ubuntu

El equipo Linux de destino debe tener **openssh-server**, **g++**, **gdb** y **gdbserver** instalados y ssh daemon debe estar en ejecución. **ZIP** es necesario para realizar la sincronización automática de encabezados remotos con el equipo local para la compatibilidad con IntelliSense. Si estas aplicaciones aún no están instaladas, puede hacerlo como sigue:

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Debido al comando sudo, es posible que se le pida la contraseña raíz.  Si es así, escríbala y continúe. Una vez que finalice, estarán instaladas las herramientas y los servicios requeridos.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   `sudo service ssh start`

   Esto inicia el servicio y lo ejecuta en segundo plano, listo para aceptar conexiones.

## <a name="linux-setup-fedora"></a>Instalación de Linux: Fedora

La máquina de destino en la que se ejecuta Fedora usa el instalador de paquetes **dnf**. Para descargar **openssh-server**, **g++**, **gdb**, **gdbserver** y **zip** y reiniciar el demonio de ssh, siga estas instrucciones:

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   `sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip`

   Debido al comando sudo, es posible que se le pida la contraseña raíz.  Si es así, escríbala y continúe. Una vez que finalice, estarán instaladas las herramientas y los servicios requeridos.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   `sudo systemctl start sshd`

   Esto inicia el servicio y lo ejecuta en segundo plano, listo para aceptar conexiones.

## <a name="ensure-you-have-cmake-38-on-the-remote-linux-machine"></a>Asegúrese de que tiene CMake 3.8 en el equipo Linux remoto

La distribución de Linux puede tener una versión anterior de CMake. La compatibilidad de CMake en Visual Studio requiere la compatibilidad de modo de servidor que se introdujo en CMake 3.8. Para ver una variante de CMake proporcionada por Microsoft, descargue los archivos binarios creados previamente más recientes en el equipo Linux en [https://github.com/Microsoft/CMake/releases](https://github.com/Microsoft/CMake/releases).
