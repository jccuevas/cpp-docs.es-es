---
title: Compatibilidad con Clang/LLVM en proyectos de CMake de Visual Studio
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 4e912c905dd7d0f742768da4c7a2acb968b4ca8e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218232"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Compatibilidad con Clang/LLVM en proyectos de CMake de Visual Studio

::: moniker range="<=vs-2017"

La compatibilidad con Clang está disponible en Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Puede usar Visual Studio con Clang para editar y depurar C++ proyectos de cmake que tengan como destino Windows o Linux.

**Windows**: Visual Studio 2019 versión 16,1 incluye compatibilidad para editar, compilar y depurar con Clang/LLVM en proyectos de CMake que tienen como destino Windows. 

**Linux**: En el caso de los proyectos de CMake de Linux, no se requiere ninguna compatibilidad especial con Visual Studio. Puede instalar Clang mediante el administrador de paquetes de distribución y agregar los comandos adecuados en el archivo archivo CMakeLists. txt.

## <a name="install"></a>Install

Para obtener la mejor compatibilidad con el IDE de Visual Studio, se recomienda usar las herramientas de compilador de Clang más recientes para Windows. Si aún no los tiene, puede instalarlos abriendo el instalador de Visual Studio y eligiendo  **C++ compilador de Clang para Windows** en **desarrollo de C++ escritorio con** componentes opcionales. Al usar una instalación de Clang personalizada, compruebe el  **C++ componente Clang-cl para v142 build tools** .

![Instalación de componentes de Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Crear una nueva configuración

Para agregar una nueva configuración de Clang a un proyecto de CMake:

1. Haga clic con el botón derecho en archivo CMakeLists. txt en **Explorador de soluciones** y elija **CMake Settings for Project**.

1. En **configuraciones**, haga clic en el botón **Agregar configuración** :

   ![Agregar configuración](media/cmake-add-config-icon.png)

1. Elija la configuración de Clang deseada (tenga en cuenta que se proporcionan configuraciones de Clang independientes para Windows y Linux) y, a continuación, presione **seleccionar**:

   ![Configuración de CMake Clang](media/cmake-clang-configuration.png)

1. Para realizar modificaciones en esta configuración, use el **Editor de configuración de CMake**. Para obtener más información, vea [personalizar la configuración de compilación de CMake en Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modificar una configuración existente para usar Clang

Para modificar una configuración existente para que use Clang, siga estos pasos:

1. Haga clic con el botón derecho en archivo CMakeLists. txt en **Explorador de soluciones** y elija **CMake Settings for Project**.

1. En **General** , seleccione la lista desplegable **Toolset** y elija el conjunto de herramientas de Clang deseado:

   ![Conjunto de herramientas de CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Ubicaciones de Clang personalizadas

De forma predeterminada, Visual Studio busca Clang en dos lugares:

- Windows La copia instalada internamente de Clang/LLVM que viene con el instalador de Visual Studio.
- (Windows y Linux) La variable de entorno PATH.

Puede especificar otra ubicación mediante el establecimiento de las variables **CMAKE_C_COMPILER** y **CMAKE_CXX_COMPILER** CMake en la **configuración de CMake**:

![Conjunto de herramientas de CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Modos de compatibilidad de Clang

En las configuraciones de Windows, CMake invoca de forma predeterminada Clang en modo [Clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) y vincula con la implementación de Microsoft de la biblioteca estándar. De forma predeterminada, **Clang-cl. exe** se encuentra `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`en.

 Puede modificar estos valores en la **configuración de CMake** en **CMake variables y caché**. Haga clic en **Mostrar variables avanzadas**. Desplácese hacia abajo hasta encontrar **CMAKE_CXX_COMPILER**y, a continuación, haga clic en el botón **examinar** para especificar una ruta de acceso del compilador diferente.

## <a name="edit-build-and-debug"></a>Editar, compilar y depurar

Después de configurar una configuración de Clang, puede compilar y depurar el proyecto. Visual Studio detecta que está usando el compilador Clang y proporciona IntelliSense, resaltado, navegación y otras características de edición. Los errores y las advertencias se muestran en el **ventana de salida**.

Al depurar, puede usar puntos de interrupción, la memoria y la visualización de datos, y la mayoría de las demás características de depuración. Algunas características que dependen del compilador, como editar y continuar, no están disponibles para las configuraciones de Clang.

![Depuración de CMake Clang](media/clang-debug-visualize.png)

::: moniker-end
