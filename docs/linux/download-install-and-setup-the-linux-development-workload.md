---
title: Instalación de la carga de trabajo de Linux para C++ en Visual Studio
description: Cómo descargar, instalar y configurar la carga de trabajo de Linux para C++ en Visual Studio.
ms.date: 05/03/2020
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: bc75610aaefe2a3bdd919cbc4dd81413202794c6
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765752"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Descargar, instalar y configurar la carga de trabajo de Linux

::: moniker range="vs-2015"

Los proyectos de Linux son compatibles con Visual Studio 2017 y versiones posteriores. Para ver la documentación de estas versiones, establezca el control selector de **Versión** de Visual Studio para este artículo en Visual Studio 2017 o Visual Studio 2019. Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker-end

::: moniker range=">=vs-2017"

Puede usar el IDE de Visual Studio en Windows para crear, editar y depurar proyectos de C++ que se ejecutan en un sistema Linux remoto, una máquina virtual o el [Subsistema de Windows para Linux](/windows/wsl/about).

Puede trabajar en la base de código existente que utiliza CMake sin tener que convertirla en un proyecto de Visual Studio. Si la base de código es multiplataforma, puede tener como destino Windows y Linux desde dentro de Visual Studio. Por ejemplo, puede editar, compilar y depurar el código en Windows con Visual Studio. Después, redestine rápidamente el proyecto a Linux para compilar y depurar en un entorno de Linux. Los archivos de encabezado de Linux se copian automáticamente en el equipo local. Visual Studio los usa para proporcionar compatibilidad completa con IntelliSense (finalización de instrucciones, Ir a definición, etc.).

Para cualquiera de estos escenarios, se requiere la carga de trabajo de **desarrollo de Linux con C++** .

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalación de Visual Studio

1. Escriba "Instalador de Visual Studio" en el cuadro de búsqueda de Windows:

   ![Cuadro de búsqueda de Windows](media/visual-studio-installer-search.png)

1. Busque el instalador en los resultados de la categoría **Aplicaciones** y haga doble clic en este. Cuando se abra el instalador, elija **Modificar** y después haga clic en la pestaña **Cargas de trabajo**. Desplácese hacia abajo hasta **Otros conjuntos de herramientas** y seleccione la carga de trabajo **Desarrollo de Linux con C++** .

   ![Carga de trabajo Visual C++ for Linux Development](media/linuxworkload.png)

1. Si el destino es IoT o plataformas incrustadas, vaya al panel **Detalles de instalación** a la derecha. En **Desarrollo de Linux con C++** , expanda **Componentes opcionales** y elija los componentes que necesite. La compatibilidad de CMake con Linux está seleccionada de forma predeterminada.

1. Haga clic en **Modificar** para continuar con la instalación.

## <a name="options-for-creating-a-linux-environment"></a>Opciones para crear un entorno Linux

Si no dispone de una máquina Linux, puede crear una máquina virtual Linux en Azure. Para obtener más información, vea [Inicio rápido: Creación de una máquina virtual Linux en Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

En Windows 10, puede instalar y tener como destino su distribución de Linux favorita en el subsistema de Windows para Linux (WSL). Para obtener más información, vea [Windows Subsystem for Linux Installation Guide for Windows 10](/windows/wsl/install-win10) (Guía de instalación del subsistema de Windows para Linux en Windows 10). Si no puede obtener acceso a la Tienda Windows, puede [descargar manualmente los paquetes de distribución de WSL](/windows/wsl/install-manual). WSL es un entorno de consola muy conveniente, pero su uso no es aconsejable en aplicaciones gráficas.

::: moniker-end

::: moniker range="vs-2019"

Los proyectos de Linux en Visual Studio requieren que se instalen las siguientes dependencias en el sistema remoto Linux o WSL:

- **Un compilador**: Visual Studio 2019 tiene compatibilidad completa con GCC y [Clang](/cpp/build/clang-support-cmake?view=vs-2019).
- **gdb**: Visual Studio inicia automáticamente gdb en el sistema Linux y usa el front-end del depurador de Visual Studio para proporcionar una experiencia de depuración de plena fidelidad en Linux.
- **rsync** y **zip**: la inclusión de rsync y zip permite a Visual Studio extraer archivos de encabezado del sistema Linux al sistema de archivos de Windows para su uso con IntelliSense.
- **make**
- **openssh-server** (solo para sistemas Linux remotos): Visual Studio se conecta a los sistemas Linux remotos a través de una conexión SSH segura.
- **CMake** (solo proyectos de CMake): puede instalar los [archivos binarios CMake vinculados estáticamente para Linux](https://github.com/microsoft/CMake/releases) de Microsoft.
- **ninja-build** (solo proyectos de CMake): [Ninja](https://ninja-build.org/) es el generador predeterminado para configuraciones de Linux y WSL en Visual Studio 2019, versión 16.6 o posteriores.

Los comandos siguientes suponen que está usando g++ en lugar de clang.

::: moniker-end

::: moniker range="vs-2017"

Los proyectos de Linux en Visual Studio requieren que se instalen las siguientes dependencias en el sistema remoto Linux o WSL:

- **gcc**: Visual Studio 2017 tiene compatibilidad completa con GCC.
- **gdb**: Visual Studio inicia automáticamente gdb en el sistema Linux y usa el front-end del depurador de Visual Studio para proporcionar una experiencia de depuración de plena fidelidad en Linux.
- **rsync** y **zip**: la inclusión de rsync y zip permite a Visual Studio extraer archivos de encabezado del sistema Linux al sistema de archivos de Windows para IntelliSense.
- **make**
- **openssh-server**: Visual Studio se conecta a los sistemas Linux remotos a través de una conexión SSH segura.
- **CMake** (solo proyectos de CMake): puede instalar los [archivos binarios CMake vinculados estáticamente para Linux](https://github.com/microsoft/CMake/releases) de Microsoft.

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Instalación de Linux: Ubuntu en WSL

Cuando el destino sea WSL, no hay necesidad de agregar una conexión remota o configurar SSH para compilar y depurar. **zip** y **rsync** son necesarios para sincronizar automáticamente los encabezados de Linux con Visual Studio para la compatibilidad con IntelliSense. **ninja-build** solo es necesario para los proyectos de CMake. Si las aplicaciones necesarias aún no están instaladas, puede hacerlo con este comando:

```bash
sudo apt-get install g++ gdb make ninja-build rsync zip
```

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu en sistemas Linux remotos

El sistema Linux de destino debe tener **openssh-server**, **g++** , **gdb** y **make** instalados. **ninja-build** solo es necesario para los proyectos de CMake. El demonio de **ssh** debe estar en ejecución. **zip** y **rsync** son necesarios para realizar la sincronización automática de encabezados remotos con el equipo local para la compatibilidad con IntelliSense. Si estas aplicaciones aún no están instaladas, puede hacerlo como se indica a continuación:

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   ```bash
   sudo apt-get install openssh-server g++ gdb make ninja-build rsync zip
   ```

   Es posible que se le pida la contraseña raíz para ejecutar el comando sudo. Si es así, escríbala y continúe. Una vez que finalice, estarán instaladas las herramientas y los servicios requeridos.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   ```bash
   sudo service ssh start
   ```

   Este comando inicia el servicio y lo ejecuta en segundo plano, listo para aceptar conexiones.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora en WSL

Fedora usa el instalador de paquetes **dnf**. Para descargar **g++** , **gdb**, **make**, **rsync**, **ninja-build** y **zip**, ejecute lo siguiente:

   ```bash
   sudo dnf install gcc-g++ gdb rsync ninja-build make zip
   ```

**zip** y **rsync** son necesarios para sincronizar automáticamente los encabezados de Linux con Visual Studio para la compatibilidad con IntelliSense. **ninja-build** solo es necesario para los proyectos de CMake.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora en sistemas Linux remotos

La máquina de destino en la que se ejecuta Fedora usa el instalador de paquetes **dnf**. Para descargar **openssh-server**, **g++** , **gdb**, **make**, **ninja-build**, **rsync** y **zip** y reiniciar el demonio de ssh, siga estas instrucciones: **ninja-build** solo es necesario para los proyectos de CMake.

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb ninja-build make rsync zip
   ```

   Es posible que se le pida la contraseña raíz para ejecutar el comando sudo. Si es así, escríbala y continúe. Una vez que finalice, estarán instaladas las herramientas y los servicios requeridos.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   ```bash
   sudo systemctl start sshd
   ```

   Este comando inicia el servicio y lo ejecuta en segundo plano, listo para aceptar conexiones.

## <a name="next-steps"></a>Pasos siguientes

Ya está listo para crear o abrir un proyecto de Linux y configurarlo para ejecutarse en el sistema de destino. Para obtener más información, consulte:

- [Creación de un proyecto de Linux](create-a-new-linux-project.md)
- [Configuración de un proyecto de CMake en Linux](cmake-linux-project.md)

::: moniker-end
