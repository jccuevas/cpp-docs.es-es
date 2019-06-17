---
title: Creación de un proyecto de C++ para Linux en Visual Studio
ms.date: 06/07/2019
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: e39e60c906901420a4809c22b4f4e71d3b621da1
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821633"
---
# <a name="create-a-new-linux-project"></a>Creación de un proyecto de Linux

::: moniker range="vs-2015"

Los proyectos de Linux están disponibles en Visual Studio 2017 y versiones posteriores.

::: moniker-end

En primer lugar, asegúrese de que está instalada la **carga de trabajo de desarrollo de Linux** para Visual Studio. Para más información, vea [Descargar, instalar y configurar la carga de trabajo de Linux](download-install-and-setup-the-linux-development-workload.md).

Al crear un proyecto de C++ para Linux en Visual Studio, tiene la opción de crear un proyecto de Visual Studio o uno de CMake. En este artículo se describe cómo crear un proyecto de Visual Studio. Para obtener información sobre cómo crear y usar proyectos de CMake existentes, vea [Configuración de un proyecto de CMake de Linux](cmake-linux-project.md).

## <a name="to-create-a-new-linux-project"></a>Para crear un proyecto de Linux

Haga lo siguiente para crear un proyecto de Linux en Visual Studio:

::: moniker range="vs-2019"

1. Seleccione **Archivo > Nuevo proyecto** en Visual Studio o pulse **Ctrl + Mayús + N**.
1. Establezca **Lenguaje** en **C++** y busque "Linux". Seleccione el tipo de proyecto que quiera crear y, después, elija **Siguiente**. Especifique un **Nombre** y una **Ubicación** y elija **Crear**.

   ![Nuevo proyecto de Linux](media/newproject-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

1. Seleccione **Archivo > Nuevo proyecto** en Visual Studio o pulse **Ctrl + Mayús + N**.
1. Seleccione el nodo **Visual C++ > Multiplataforma > Linux** y, luego, seleccione el tipo de proyecto que le gustaría crear. Especifique un **Nombre** y una **Ubicación** y elija **Aceptar**.

   ![Nuevo proyecto de Linux](media/newproject.png)

::: moniker-end

   | Tipo de proyecto | Descripción |
   | ------------ | --- |
   | **Blink (Raspberry)**           | Proyecto destinado a un dispositivo Raspberry Pi con código de ejemplo que hace parpadear un LED |
   | **Aplicación de consola (Linux)** | Proyecto destinado a cualquier equipo Linux con código de ejemplo que muestra texto en la consola |
   | **Proyecto vacío (Linux)**       | Proyecto destinado a cualquier equipo Linux sin código de ejemplo |
   | **Proyecto de archivos MAKE (Linux)**    | Proyecto destinado a cualquier equipo Linux que se compila con un sistema de compilación estándar de archivos Make |

## <a name="next-steps"></a>Pasos siguientes

[Configuración de un proyecto de Linux](configure-a-linux-project.md)
