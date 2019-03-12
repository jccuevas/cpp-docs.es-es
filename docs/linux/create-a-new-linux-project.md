---
title: Creación de un proyecto de C++ para Linux en Visual Studio
ms.date: 09/12/2018
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: bd5ab1d2bc1077f366082bf8767f8f690173ac8b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745163"
---
# <a name="create-a-new-linux-project"></a>Crear un nuevo proyecto de Linux

En primer lugar, asegúrese de que está instalada la **carga de trabajo de desarrollo de Linux** para Visual Studio. Para más información, vea [Descargar, instalar y configurar la carga de trabajo de Linux](download-install-and-setup-the-linux-development-workload.md).

Al crear un proyecto de C++ en Visual Studio para Linux, tiene la opción de crear un proyecto de Visual Studio o un proyecto de CMake. En este tema se describe cómo crear un proyecto de Visual Studio. Para obtener información sobre la creación y el uso de proyectos de CMake existentes, vea [Configuración de un proyecto de CMake de Linux](cmake-linux-project.md).

Para crear un nuevo proyecto de Linux en Visual Studio, haga lo siguiente:

1. Seleccione **Archivo > Nuevo proyecto** en Visual Studio o pulse **Ctrl + Mayús + N**.
1. Seleccione el nodo **Visual C++ > Multiplataforma > Linux** y, luego, seleccione el tipo de proyecto que le gustaría crear, escriba un nombre o ubicación y haga clic en Aceptar.

   ![Nuevo proyecto de Linux](media/newproject.png)

   | Tipo de proyecto | Descripción
   | ------------ | ---
   | **Blink (Raspberry)**           | Proyecto destinado a un dispositivo Raspberry Pi con código de ejemplo escrito para hacer parpadear un LED
   | **Aplicación de consola (Linux)** | Proyecto destinado a cualquier equipo Linux con código de ejemplo escrito para mostrar texto en la consola
   | **Proyecto vacío (Linux)**       | Proyecto destinado a cualquier equipo Linux sin código de ejemplo escrito
   | **Proyecto de archivos MAKE (Linux)**    | Proyecto destinado a cualquier equipo Linux que se compilará con un sistema de compilación estándar de archivos Make
