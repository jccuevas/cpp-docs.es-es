---
title: Compatibilidad con Clang/LLVM en proyectos de Visual Studio CMake
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: 46bfe788c13df3a37dd9cba654d16cfe4c3fe177
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323182"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Compatibilidad con Clang/LLVM en proyectos de Visual Studio CMake

::: moniker range="<=vs-2017"

La compatibilidad con Clang está disponible en Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Puede usar Visual Studio con Clang para editar y depurar proyectos de C++ CMake destinados a Windows o Linux.

**Windows**: Visual Studio 2019 versión 16.1 incluye compatibilidad para editar, compilar y depurar con Clang/LLVM en proyectos CMake destinados a Windows.

**Linux:** para proyectos de Linux CMake, no se requiere compatibilidad especial con Visual Studio. Puede instalar Clang con el administrador de paquetes de la distribución y agregar los comandos adecuados en el archivo CMakeLists.txt.

## <a name="install"></a>Instalar

Para obtener la mejor compatibilidad con IDE en Visual Studio, se recomienda usar las herramientas del compilador de Clang más recientes para Windows. Si aún no los tiene, puede instalarlos abriendo el instalador de Visual Studio y eligiendo **el compilador C++ Clang para Windows** en Desarrollo de escritorio con componentes opcionales de **C++.** Cuando utilice una instalación de Clang personalizada, compruebe el componente **C++ Clang-cl para herramientas de compilación v142.**

![Instalación de componentes Clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Crear una nueva configuración

Para agregar una nueva configuración de Clang a un proyecto CMake:

1. Haga clic con el botón derecho en CMakeLists.txt en el **Explorador** de soluciones y elija **Configuración de CMake para el proyecto**.

1. En **Configuraciones**, pulse el botón **Agregar configuración:**

   ![Adición de configuración](media/cmake-add-config-icon.png)

1. Elija la configuración de Clang deseada (tenga en cuenta que se proporcionan configuraciones separadas de Clang para Windows y Linux) y, a continuación, pulse **Seleccionar:**

   ![Configuración de CMake Clang](media/cmake-clang-configuration.png)

1. Para realizar modificaciones en esta configuración, utilice el Editor de configuración de **CMake**. Para obtener más información, vea Personalizar la configuración de [compilación de CMake en Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modifique una configuración existente para utilizar Clang

Para modificar una configuración existente para utilizar Clang, siga estos pasos:

1. Haga clic con el botón derecho en CMakeLists.txt en el **Explorador** de soluciones y elija **Configuración de CMake para el proyecto**.

1. En **General,** seleccione el menú desplegable **Conjunto** de herramientas y elija el conjunto de herramientas Clang deseado:

   ![Conjunto de herramientas CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Ubicaciones personalizadas de Clang

De forma predeterminada, Visual Studio busca Clang en dos lugares:

- (Windows) La copia instalada internamente de Clang/LLVM que viene con el instalador de Visual Studio.
- (Windows y Linux) La variable de entorno PATH.

Puede especificar otra ubicación estableciendo las **variables CMAKE_C_COMPILER** y **CMAKE_CXX_COMPILER** CMake en **Configuración de CMake:**

![Conjunto de herramientas CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Modos de compatibilidad de Clang

Para las configuraciones de Windows, CMake invoca de forma predeterminada Clang en modo [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) y se vincula con la implementación de Microsoft de la biblioteca estándar. De forma predeterminada, **clang-cl.exe** se encuentra en `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Puede modificar estos valores en **Configuración de CMake** en **Variables de CMake y caché**. Haga clic en **Mostrar variables avanzadas**. Desplácese hacia abajo para buscar **CMAKE_CXX_COMPILER**y, a continuación, haga clic en el botón **Examinar** para especificar una ruta de acceso del compilador diferente.

## <a name="edit-build-and-debug"></a>Editar, compilar y depurar

Después de configurar una configuración de Clang, puede compilar y depurar el proyecto. Visual Studio detecta que está utilizando el compilador de Clang y proporciona IntelliSense, resaltado, navegación y otras características de edición. Los errores y advertencias se muestran en la **ventana de salida**.

Al depurar, puede usar puntos de interrupción, visualización de memoria y datos, y la mayoría de las demás características de depuración. Algunas características dependientes del compilador, como Editar y Continuar, no están disponibles para las configuraciones de Clang.

![Depuración de CMake Clang](media/clang-debug-visualize.png)

::: moniker-end
