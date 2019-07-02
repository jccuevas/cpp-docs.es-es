---
title: Soporte técnico de clang/LLVM en proyectos de CMake de Visual Studio
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++
ms.openlocfilehash: 6773d9cdb076ef305ba635306f3bc9c6575d2203
ms.sourcegitcommit: b233f05adae607f75815111006a771c432df5a9d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67517110"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Soporte técnico de clang/LLVM en proyectos de CMake de Visual Studio

::: moniker range="<=vs-2017"

Compatibilidad con clang está disponible en Visual Studio de 2019.

::: moniker-end

::: moniker range="vs-2019"

Puede usar Visual Studio para editar y depurar con Clang C++ los proyectos de CMake ese destino Windows o Linux.

**Windows**: Visual Studio 2019 16.1 versión incluye compatibilidad para la edición, compilación y depuración con Clang/LLVM en proyectos de CMake dirigidos a Windows. 

**Linux**: Para los proyectos de CMake de Linux, no se requiere ninguna compatibilidad especial de Visual Studio. Puede instalar mediante el Administrador de paquetes de la distribución de Clang y agregar los comandos adecuados en el archivo CMakeLists.txt.

## <a name="install"></a>Instalar

Para mejor compatibilidad con IDE de Visual Studio, se recomienda usar las herramientas del compilador de Clang más recientes para Windows. Si aún no tiene las, puede instalarlos abriendo el instalador de Visual Studio y eligiendo **compilador Clang para Windows** en **con el desarrollo de escritorio C++**  componentes opcionales.

![Instalación de componentes de clang](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>Crear una nueva configuración

Para agregar una nueva configuración de Clang a un proyecto de CMake:

1. Haga doble clic en el archivo CMakeLists.txt en **el Explorador de soluciones** y elija **CMake configuración de proyecto**.

1. En **configuraciones**, presione el **Agregar configuración** botón:

   ![Agregar configuración](media/cmake-add-config-icon.png)

1. Elija la configuración deseada de Clang (tenga en cuenta que se proporcionan configuraciones de Clang independientes para Windows y Linux), a continuación, presione **seleccione**:

   ![Configuración de CMake Clang](media/cmake-clang-configuration.png)

1. Para realizar modificaciones en esta configuración, utilice el **Editor de configuración de CMake**. Para obtener más información, consulte [compilación de CMake de personalizar la configuración de Visual Studio](customize-cmake-settings.md).

## <a name="modify-an-existing-configuration-to-use-clang"></a>Modificar una configuración existente para usar Clang

Para modificar una configuración existente para usar Clang, siga estos pasos:

1. Haga doble clic en el archivo CMakeLists.txt en **el Explorador de soluciones** y elija **CMake configuración de proyecto**.

1. En **General** seleccione la **Toolset** lista desplegable y elija el conjunto de herramientas de Clang deseado:

   ![Conjunto de herramientas de CMake Clang](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>Ubicaciones personalizadas de Clang

De forma predeterminada, Visual Studio busca Clang en dos lugares:

- (Windows) La copia internamente instalada de Clang/LLVM que se incluye con el instalador de Visual Studio.
- (Windows y Linux) La variable de entorno PATH.

Puede especificar otra ubicación estableciendo el **CMAKE_C_COMPILER** y **CMAKE_CXX_COMPILER** variables de CMake en **configuración de CMake**:

![Conjunto de herramientas de CMake Clang](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Modos de compatibilidad de clang

Para las configuraciones de Windows, CMake predeterminada invoca Clang en [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) modo y vínculos con la implementación de la biblioteca estándar de Microsoft. De forma predeterminada, **clang cl.exe** se encuentra en `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

 Puede modificar estos valores en **configuración de CMake** en **CMake variables y caché**. Haga clic en **mostrar avanzadas variables**. Desplácese hacia abajo hasta encontrar **CMAKE_CXX_COMPILER**, a continuación, haga clic en el **examinar** botón para especificar una ruta de acceso de compilador diferentes.

## <a name="edit-build-and-debug"></a>Editar, compilar y depurar

Una vez haya configurado una configuración de Clang, puede compilar y depurar el proyecto. Visual Studio detecta que está utilizando el compilador de Clang y proporciona IntelliSense, resaltar, navegación y otras características de edición. Errores y advertencias se muestran en el **ventana de salida**.

Al depurar, puede usar los puntos de interrupción, memoria y visualización de datos y la mayoría otras características de depuración. Algunas características del compilador dependiente como editar y continuar no están disponibles para las configuraciones de Clang.

![Depuración de CMake Clang](media/clang-debug-visualize.png)

::: moniker-end
