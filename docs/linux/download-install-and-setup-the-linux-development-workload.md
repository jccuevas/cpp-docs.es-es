---
title: Instalación de la carga de trabajo de Linux para C++ en Visual Studio | Microsoft Docs
description: En este artículo se describe cómo descargar, instalar y configurar la carga de trabajo de Linux para C++ en Visual Studio.
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 403f1bcd8634c3f471f34ff1266501de5bf05d52
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601397"
---
# <a name="download-install-and-setup-the-linux-workload"></a>Descargar, instalar y configurar la carga de trabajo de Linux

Puede usar el IDE de Visual Studio en Windows para crear, editar y depurar proyectos de C++ que se ejecutan en un equipo físico Linux, una máquina virtual o el [subsistema Windows para Linux](/windows/wsl/about). Para cualquiera de estos escenarios, primero debe instalar la carga de trabajo de **Desarrollo de Linux con C++**.

## <a name="visual-studio-setup"></a>Instalación de Visual Studio

1. Escriba "Instalador de Visual Studio" en el menú de búsqueda de Windows; búsquelo en los resultados de **Aplicaciones** y haga doble clic en él. Cuando se abra el instalador, elija **Modificar** y después haga clic en la pestaña **Cargas de trabajo**. Desplácese hacia abajo hasta **Otros conjuntos de herramientas** y seleccione la carga de trabajo **Desarrollo de Linux con C++**.

   ![Carga de trabajo Visual C++ for Linux Development](media/linuxworkload.png)

1. Si utiliza CMake o tiene como destino plataformas incrustadas o IoT, vaya al panel **Detalles de la instalación** de la derecha, debajo de **Desarrollo de Linux con C++**, expanda **Componentes opcionales** y elija los componentes que necesita. 

1. Haga clic en **Modificar** para continuar con la instalación.


## <a name="options-for-creating-a-linux-environment"></a>Opciones para crear un entorno Linux

Si no dispone de una máquina Linux, puede crear una máquina virtual Linux en Azure. Para más información, vea [Guía de inicio rápido: Creación de una máquina virtual Linux en Azure Portal](/azure/virtual-machines/linux/quick-create-portal).

Otra opción, en Windows 10, es activar el subsistema Windows para Linux. Para más información, vea la [guía de instalación de Windows 10](/windows/wsl/install-win10).

## <a name="linux-setup"></a>Instalación de Linux

El equipo Linux de destino debe tener **openssh-server**, **g++**, **gdb** y **gdbserver** instalados y ssh daemon debe estar en ejecución. **ZIP** es necesario para realizar la sincronización automática de encabezados remotos con el equipo local para la compatibilidad con IntelliSense. Si estas aplicaciones aún no están instaladas, puede hacerlo como sigue:

1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   `sudo apt-get install openssh-server g++ gdb gdbserver zip`

   Debido al comando sudo, es posible que se le pida la contraseña raíz.  Si es así, escríbala y continúe.  Una vez que haya finalizado, se instalarán estos servicios y herramientas.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   `sudo service ssh start`

   Esto iniciará el servicio y lo ejecutará en segundo plano, listo para aceptar conexiones.
