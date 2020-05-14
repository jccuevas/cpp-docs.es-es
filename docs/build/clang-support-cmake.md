---
title: Compatibilidad con Clang/LLVM en proyectos de CMake de Visual Studio
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323182"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Compatibilidad con Clang/LLVM en proyectos de CMake de Visual Studio

::: moniker range="<=vs-2017"

La compatibilidad con Clang está disponible en Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Puede usar Visual Studio con Clang para editar y depurar proyectos de CMake en C++ que tengan como destino Windows o Linux.

**Windows**: La versión 16.1 de Visual Studio 2019 incluye compatibilidad para editar, compilar y depurar con Clang/LLVM en proyectos de CMake que tienen como destino Windows.

**Linux**: En el caso de los proyectos de CMake de Linux, no se requiere ninguna compatibilidad especial con Visual Studio. Puede instalar Clang mediante el administrador de paquetes de distribución y agregar los comandos adecuados en el archivo CMakeLists.txt.

## <a name="install"></a>Instalar

Para obtener la mejor compatibilidad con el IDE de Visual Studio, se recomienda usar las herramientas más recientes del compilador de Clang para Windows. Si aún no las tiene, puede instalarlas mediante el Instalador de Visual Studio si elige **Compilador de Clang en C++ para Windows** en los componentes opcionales de **Desarrollo para el escritorio con C++** . Al usar una instalación personalizada de Clang, compruebe el componente **Herramientas de compilación de Clang-cl en C++ para v142**.

![Instalación de componentes de Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Creación de una nueva configuración

Para agregar una nueva configuración de Clang a un proyecto de CMake:

1. Haga clic con el botón derecho en el archivo CMakeLists.txt en el **Explorador de soluciones** y seleccione **CMake settings for project** (Configuración de CMake para el proyecto).

1. En **Configuraciones**, presione el botón **Agregar configuración**:

   ![Agregar configuración](media/cmake-add-config-icon.png)

1. Elija la configuración de Clang que quiera (tenga en cuenta que se proporcionan configuraciones de Clang independientes para Windows y Linux) y, a continuación, haga clic en **Seleccionar**:

   ![Configuración de CMake de Clang](media/cmake-clang-configuration.png)

1. Para realizar modificaciones en esta configuración, use el **Editor de configuración de CMake**. Para obtener más información, vea [Personalización de la configuración de compilación de CMake en Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modificación de una configuración existente para usar Clang

Para modificar una configuración existente para que use Clang, siga estos pasos:

1. Haga clic con el botón derecho en el archivo CMakeLists.txt en el **Explorador de soluciones** y seleccione **CMake settings for project** (Configuración de CMake para el proyecto).

1. En **General**, seleccione la lista desplegable **Conjunto de herramientas** y elija el conjunto de herramientas de Clang que quiera:

   ![Conjunto de herramientas de Clang para CMake](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Ubicaciones de Clang personalizadas

De forma predeterminada, Visual Studio busca Clang en dos ubicaciones:

- (Windows) La copia instalada internamente de Clang/LLVM que viene con el instalador de Visual Studio.
- (Windows y Linux) La variable de entorno PATH.

Para especificar otra ubicación, establezca las variables **CMAKE_C_COMPILER** y **CMAKE_CXX_COMPILER** de CMake en **Configuración de CMake**:

![Conjunto de herramientas de Clang para CMake](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Modos de compatibilidad de Clang

En las configuraciones de Windows, CMake llama a Clang de forma predeterminada en el modo [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) y lo vincula con la implementación de Microsoft de la biblioteca estándar. De forma predeterminada, **clang-cl.exe** se encuentra en `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Puede modificar estos valores desde **Configuración de CMake** en **Caché y variables de CMake**. Haga clic en **Mostrar variables avanzadas**. Desplácese hacia abajo hasta encontrar **CMAKE_CXX_COMPILER** y, a continuación, haga clic en el botón **Examinar** para especificar una ruta de 
acceso del compilador diferente.

## <a name="edit-build-and-debug"></a>Edición, compilación y depuración

Después de especificar una configuración de Clang, puede compilar y depurar el proyecto. Visual Studio detecta que está usando el compilador de Clang y proporciona IntelliSense, resaltado, navegación y otras características de edición. Los errores y las advertencias se muestran en **Ventana de salida**.

Al depurar, puede usar puntos de interrupción, visualización de datos y de la memoria, y la mayoría del resto de características de depuración. Algunas características que dependen del compilador, como "Editar y continuar", no están disponibles para las configuraciones de Clang.

![Depuración de Clang en CMake](media/clang-debug-visualize.png)

::: moniker-end
