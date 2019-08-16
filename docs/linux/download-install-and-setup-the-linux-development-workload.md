---
title: Instalación de la carga de trabajo de Linux para C++ en Visual Studio
description: En este artículo se describe cómo descargar, instalar y configurar la carga de trabajo de Linux para C++ en Visual Studio.
ms.date: 06/11/2019
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
ms.openlocfilehash: 5df7b323d202f398059e92abaeeeedbf73439fa4
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299793"
---
# <a name="download-install-and-set-up-the-linux-workload"></a>Descargar, instalar y configurar la carga de trabajo de Linux

::: moniker range="vs-2015"

Los proyectos de Linux son compatibles con Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

Puede usar el IDE de Visual Studio en Windows para crear, editar y depurar proyectos de C++ que se ejecutan en un equipo físico Linux, una máquina virtual o el [subsistema Windows para Linux](/windows/wsl/about). 

Puede trabajar en la base de código existente que usa CMake o cualquier otro sistema de compilación sin tener que convertirla en un proyecto de Visual Studio. Si la base de código es multiplataforma, puede tener como destino Windows y Linux desde dentro de Visual Studio. Por ejemplo, puede editar y depurar el código y generar perfiles de este en Windows con Visual Studio y, después, rápidamente redestinar el proyecto para que Linux realice más pruebas. Los archivos de encabezado de Linux se copian automáticamente en el equipo local, donde Visual Studio los usa para proporcionar compatibilidad completa con IntelliSense (finalización de instrucciones, Ir a definición, etc.). 
 
Para cualquiera de estos escenarios, se requiere la carga de trabajo de **desarrollo de Linux con C++** . 

::: moniker-end

::: moniker range="vs-2019"

En Visual Studio 2019 se pueden especificar destinos independientes para la compilación y depuración. Cuando el destino es WSL, ya no es necesario agregar una conexión remota o configurar SSH.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="visual-studio-setup"></a>Instalación de Visual Studio

1. Escriba "Instalador de Visual Studio" en el cuadro de búsqueda de Windows:

   ![Cuadro de búsqueda de Windows](media/visual-studio-installer-search.png)

2. Busque el instalador en los resultados de la categoría **Aplicaciones** y haga doble clic en este. Cuando se abra el instalador, elija **Modificar** y después haga clic en la pestaña **Cargas de trabajo**. Desplácese hacia abajo hasta **Otros conjuntos de herramientas** y seleccione la carga de trabajo **Desarrollo de Linux con C++** .

   ![Carga de trabajo Visual C++ for Linux Development](media/linuxworkload.png)

1. Si tiene como destino plataformas incrustadas o IoT, vaya al panel **Detalles de la instalación** de la derecha y, debajo de **Desarrollo de Linux con C++** , expanda **Componentes opcionales** y elija los componentes que necesita. La compatibilidad de CMake con Linux está seleccionada de forma predeterminada.

1. Haga clic en **Modificar** para continuar con la instalación.

## <a name="options-for-creating-a-linux-environment"></a>Opciones para crear un entorno Linux

Si no dispone de una máquina Linux, puede crear una máquina virtual Linux en Azure. Para obtener más información, vea [Inicio rápido: Creación de una máquina virtual Linux en Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

En Windows 10, puede instalar y tener como destino su distribución de Linux favorita en el subsistema de Windows para Linux (WSL). Para obtener más información, vea [Windows Subsystem for Linux Installation Guide for Windows 10](/windows/wsl/install-win10) (Guía de instalación del subsistema de Windows para Linux en Windows 10). WSL es un entorno de consola muy conveniente, pero su uso no es aconsejable en aplicaciones gráficas. 

::: moniker-end

::: moniker range="vs-2019"

## <a name="linux-setup-ubuntu-on-wsl"></a>Instalación de Linux: Ubuntu en WSL

Cuando el destino sea WSL, no hay ninguna necesidad de agregar una conexión remota o configurar SSH con el fin de compilar y depurar. **zip** y **rsync** son necesarios para sincronizar automáticamente los encabezados de Linux con Visual Studio para la compatibilidad con IntelliSense. Si las aplicaciones necesarias aún no están instaladas, puede hacerlo como sigue:

```bash
sudo apt-get install g++ gdb make rsync zip
```
::: moniker-end

::: moniker range=">=vs-2017"

## <a name="ubuntu-on-remote-linux-systems"></a>Ubuntu en sistemas Linux remotos

El sistema Linux de destino debe tener **openssh-server**, **g++** , **gdb** y **gdbserver** instalados, y ssh daemon debe estar en ejecución. **ZIP** es necesario para realizar la sincronización automática de encabezados remotos con el equipo local para la compatibilidad con IntelliSense. Si estas aplicaciones aún no están instaladas, puede hacerlo como sigue:

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   ```bash
   sudo apt-get install openssh-server g++ gdb gdbserver zip
   ```

   Debido al comando sudo, es posible que se le pida la contraseña raíz.  Si es así, escríbala y continúe. Una vez que finalice, estarán instaladas las herramientas y los servicios requeridos.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   ```bash
   sudo service ssh start
   ```
   Esto inicia el servicio y lo ejecuta en segundo plano, listo para aceptar conexiones.

::: moniker-end

::: moniker range="vs-2019"

## <a name="fedora-on-wsl"></a>Fedora en WSL

Fedora usa el instalador de paquetes **dnf**. Para descargar **g++** , **gdb**, **rsync** y **zip**, ejecute lo siguiente:

   ```bash
   sudo dnf install gcc-g++ gdb rsync zip
   ```

**zip** y **rsync** son necesarios para sincronizar automáticamente los encabezados de Linux con Visual Studio para la compatibilidad con IntelliSense.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="fedora-on-remote-linux-systems"></a>Fedora en sistemas Linux remotos

La máquina de destino en la que se ejecuta Fedora usa el instalador de paquetes **dnf**. Para descargar **openssh-server**, **g++** , **gdb**, **gdbserver** y **zip** y reiniciar el demonio de ssh, siga estas instrucciones:

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   ```bash
   sudo dnf install openssh-server gcc-g++ gdb gdb-gdbserver zip
   ```
   Debido al comando sudo, es posible que se le pida la contraseña raíz.  Si es así, escríbala y continúe. Una vez que finalice, estarán instaladas las herramientas y los servicios requeridos.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   ```bash
   sudo systemctl start sshd
   ```

   Esto inicia el servicio y lo ejecuta en segundo plano, listo para aceptar conexiones.

::: moniker-end

::: moniker range="vs-2015"

La compatibilidad con el desarrollo de C++ Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

## <a name="next-steps"></a>Pasos siguientes

Ya está listo para crear o abrir un proyecto de Linux y configurarlo para ejecutarse en el sistema de destino. Para obtener más información, consulte:

- [Creación de un proyecto de Linux](create-a-new-linux-project.md)
- [Configuración de un proyecto de CMake en Linux](cmake-linux-project.md)
