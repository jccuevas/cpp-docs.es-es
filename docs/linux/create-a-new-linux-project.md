---
title: Creación de un proyecto de C++ para Linux en Visual Studio
ms.date: 10/24/2019
description: Cree un nuevo proyecto de Linux basado en MSBuild en Visual Studio.
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 1e79dd50756b71aabae7ccec75e57178898e7720
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364349"
---
# <a name="create-a-new-linux-project"></a>Creación de un proyecto de Linux

::: moniker range="vs-2015"

Los proyectos de Linux están disponibles en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range="vs-2017"

En primer lugar, asegúrese de que está instalada la **carga de trabajo de desarrollo de Linux** para Visual Studio. Para más información, vea [Descargar, instalar y configurar la carga de trabajo de Linux](download-install-and-setup-the-linux-development-workload.md).

Para la compilación multiplataforma, recomendamos usar CMake. La compatibilidad con CMake es más completa en Visual Studio 2019. Si CMake no es una opción y tiene una solución de Visual Studio de Windows que desea ampliar a fin de compilar para Linux, puede agregar un proyecto de Linux de Visual Studio a la solución de Windows, junto con un proyecto **Elementos compartidos**. Coloque el código que se comparte entre las dos plataformas del proyecto Elementos compartidos y agregue una referencia a ese proyecto desde los proyectos de Windows y Linux.

## <a name="to-create-a-new-linux-project"></a>Para crear un proyecto de Linux

Haga lo siguiente para crear un proyecto de Linux en Visual Studio 2017:

1. Seleccione **Archivo > Nuevo proyecto** en Visual Studio o pulse **Ctrl + Mayús + N**.
1. Seleccione el nodo **Visual C++ > Multiplataforma > Linux** y, luego, seleccione el tipo de proyecto que le gustaría crear. Especifique un **Nombre** y una **Ubicación** y elija **Aceptar**.

   ![Nuevo proyecto de Linux](media/newproject.png)

   | Tipo de proyecto | Descripción |
   | ------------ | --- |
   | **Blink (Raspberry)**           | Proyecto destinado a un dispositivo Raspberry Pi con código de ejemplo que hace parpadear un LED |
   | **Aplicación de consola (Linux)** | Proyecto destinado a cualquier equipo Linux con código de ejemplo que muestra texto en la consola |
   | **Proyecto vacío (Linux)**       | Proyecto destinado a cualquier equipo Linux sin código de ejemplo |
   | **Proyecto de archivos MAKE (Linux)**    | Proyecto destinado a cualquier equipo Linux que se compila con un sistema de compilación estándar de archivos Make |

## <a name="next-steps"></a>Pasos siguientes

[Configuración de un proyecto de Linux](configure-a-linux-project.md)

::: moniker-end

::: moniker range="vs-2019"

En primer lugar, asegúrese de que está instalada la **carga de trabajo de desarrollo de Linux** para Visual Studio. Para más información, vea [Descargar, instalar y configurar la carga de trabajo de Linux](download-install-and-setup-the-linux-development-workload.md).

Al crear un proyecto de C++ para Linux en Visual Studio, tiene la opción de crear un proyecto de Visual Studio o uno de CMake. En este artículo se describe cómo crear un proyecto de Visual Studio. En general, para los nuevos proyectos que pueden incluir código fuente o que tiene previsto compilar para el desarrollo multiplataforma, recomendamos que use CMake con Visual Studio. Con un proyecto de CMake, puede compilar y depurar el mismo proyecto en Windows y Linux. Para obtener más información, vea [Creación y configuración de un proyecto de CMake de Linux](cmake-linux-project.md).

Si tiene una solución de Visual Studio de Windows que desea ampliar a fin de compilar para Linux y CMake no es una opción, puede agregar un proyecto de Linux de Visual Studio a la solución de Windows, junto con un proyecto **Elementos compartidos**. Coloque el código que se comparte entre las dos plataformas del proyecto Elementos compartidos y agregue una referencia a ese proyecto desde los proyectos de Windows y Linux.

## <a name="to-create-a-new-linux-project"></a>Para crear un proyecto de Linux

Haga lo siguiente para crear un proyecto de Linux en Visual Studio 2019:

1. Seleccione **Archivo > Nuevo proyecto** en Visual Studio o pulse **Ctrl + Mayús + N**.
1. Establezca **Lenguaje** en **C++** y busque "Linux". Seleccione el tipo de proyecto que quiera crear y, después, elija **Siguiente**. Especifique un **Nombre** y una **Ubicación** y elija **Crear**.

   ![Nuevo proyecto de Linux](media/newproject-vs2019.png)

   | Tipo de proyecto | Descripción |
   | ------------ | --- |
   | **Blink (Raspberry)**           | Proyecto destinado a un dispositivo Raspberry Pi con código de ejemplo que hace parpadear un LED |
   | **Aplicación de consola (Linux)** | Proyecto destinado a cualquier equipo Linux con código de ejemplo que muestra texto en la consola |
   | **Proyecto vacío (Linux)**       | Proyecto destinado a cualquier equipo Linux sin código de ejemplo |
   | **Proyecto de archivos MAKE (Linux)**    | Proyecto destinado a cualquier equipo Linux que se compila con un sistema de compilación estándar de archivos Make |

## <a name="next-steps"></a>Pasos siguientes

[Configuración de un proyecto de Linux](configure-a-linux-project.md)

::: moniker-end
