---
title: Compatibilidad con Clang/LLVM en proyectos de Visual Studio Visual Studio
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 8d7d7fec979d3e7b8f665e56094ee1c309e3b686
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323118"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Compatibilidad con Clang/LLVM en proyectos de Visual Studio

::: moniker range="<=vs-2017"

La compatibilidad de Clang para proyectos CMake y MSBuild está disponible en Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Puede usar Visual Studio 2019 versión 16.2 con Clang para editar, compilar y depurar proyectos de C++ Visual Studio (MSBuild) destinados a Windows o Linux.

## <a name="install"></a>Instalar

Para obtener la mejor compatibilidad con IDE en Visual Studio, se recomienda usar las herramientas del compilador de Clang más recientes para Windows. Si aún no los tiene, puede instalarlos abriendo el instalador de Visual Studio y eligiendo **las herramientas c++ Clang para Windows** en Desarrollo de escritorio con componentes opcionales de **C++.** Si prefiere utilizar una instalación de Clang existente en su equipo, elija **C++ Clang-cl para las herramientas de compilación v142.** componente opcional. La biblioteca estándar de Microsoft C++ actualmente requiere al menos Clang 8.0.0; la versión incluida de Clang se actualizará automáticamente para mantenerse al día con las actualizaciones en la implementación de Microsoft de la biblioteca estándar.

![Instalación de componentes Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Configurar un proyecto de Windows para usar las herramientas de Clang

Para configurar un proyecto de Visual Studio para usar Clang, haga clic con el botón secundario en el nodo del proyecto en el **Explorador** de soluciones y elija **Propiedades**. Normalmente, primero debe elegir **Todas las configuraciones** en la parte superior del cuadro de diálogo. A continuación, en **General** > **Platform Toolset**, elija **LLVM (clang-cl)** y, a continuación, **OK**.

![Instalación de componentes Clang](media/clang-msbuild-prop-page.png)

Si usa las herramientas de Clang que se incluyen con Visual Studio, no se requieren pasos adicionales. Para los proyectos de Windows, Visual Studio invoca de forma predeterminada Clang en modo [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) y vínculos con la implementación de Microsoft de la biblioteca estándar. De forma predeterminada, **clang-cl.exe** se encuentra en `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

**Properties** > Si utiliza una instalación de Clang personalizada,**Configuration Properties** > puede **modificar** > los**directorios ejecutables** de propiedades de configuración**VC++ DIrectories** > de propiedades `LLVMInstallDir` del proyecto agregando la raíz de instalación de Clang personalizada como el primer directorio allí o cambiar el valor de la propiedad. Consulte [Establecer una ubicación LLVM personalizada](#custom_llvm_location) para obtener más información.

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Configurar un proyecto de Linux para utilizar las herramientas de Clang

Para proyectos de Linux, Visual Studio usa el front-end compatible con Clang GCC. Las propiedades del proyecto y casi todos los indicadores del compilador son idénticos

Para configurar un proyecto de Visual Studio Linux para usar Clang:

1. Haga clic con el botón derecho en el nodo del proyecto en el **Explorador** de soluciones y elija **Propiedades**.
1. Normalmente, primero debe elegir **Todas las configuraciones** en la parte superior del cuadro de diálogo.
1. En **General** > **Platform Toolset**, elija **WSL_Clang_1_0** si está utilizando el subsistema de Windows para Linux o **Remote_Clang_1_0** si está utilizando una máquina virtual o una máquina virtual remota.
1. Presione **Aceptar**.

![Instalación de componentes Clang](media/clang-msbuild-prop-page.png)

En Linux, Visual Studio usa de forma predeterminada la primera ubicación de Clang que encuentra en la propiedad de entorno PATH. Si utiliza una instalación de Clang personalizada, debe `LLVMInstallDir` cambiar el valor de la propiedad o, de lo contrario, sustituir una ruta de acceso en**Propiedades** >  **del proyecto** > **VC++ Propiedades** > de**configuración** > **Directorios ejecutables**. Consulte [Establecer una ubicación LLVM personalizada](#custom_llvm_location) para obtener más información.

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a>Establecer una ubicación LLVM personalizada

Puede establecer una ruta de acceso personalizada para LLVM para uno o varios proyectos creando un archivo *Directory.build.props* y agregando ese archivo a la carpeta raíz de cualquier proyecto. Puede agregarlo a la carpeta de la solución raíz para aplicarlo a todos los proyectos de la solución. El archivo debe tener este aspecto (pero sustituya su ruta real):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Establezca propiedades adicionales, edite, cree y depure

Después de configurar una configuración de Clang, vuelva a hacer clic con el botón derecho en el nodo del proyecto y elija **Volver a cargar el proyecto**. Ahora puede compilar y depurar el proyecto con las herramientas de Clang. Visual Studio detecta que está utilizando el compilador de Clang y proporciona IntelliSense, resaltado, navegación y otras características de edición. Los errores y advertencias se muestran en la **ventana de salida**. Las páginas de propiedades del proyecto para una configuración de Clang son muy similares a las de MSVC, aunque algunas características dependientes del compilador, como Editar y Continuar, no están disponibles para las configuraciones de Clang. Para establecer una opción de compilador o vinculador de Clang que no está disponible en las páginas de propiedades, puede agregarla manualmente en las páginas de propiedades en **Propiedades** > de configuración**C/C++ (o Vinculador)** > **Opciones adicionales**de línea > de**comandos**.

Al depurar, puede usar puntos de interrupción, visualización de memoria y datos, y la mayoría de las demás características de depuración.  

![Depuración de Clang](media/clang-debug-msbuild.png)

::: moniker-end
