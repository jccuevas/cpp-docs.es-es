---
title: Compatibilidad con Clang/LLVM en proyectos de Visual Studio
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 8d7d7fec979d3e7b8f665e56094ee1c309e3b686
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323118"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Compatibilidad con Clang/LLVM en proyectos de Visual Studio

::: moniker range="<=vs-2017"

La compatibilidad con Clang para proyectos de CMake y MSBuild está disponible en Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Puede usar la versión 16.2 de Visual Studio 2019 con Clang para editar, compilar y depurar proyectos de C++ en Visual Studio (MSBuild) que tengan como destino Windows o Linux.

## <a name="install"></a>Instalar

Para obtener la mejor compatibilidad con el IDE de Visual Studio, se recomienda usar las herramientas más recientes del compilador de Clang para Windows. Si aún no las tiene, puede instalarlas mediante el Instalador de Visual Studio si elige **Herramientas de Clang en C++ para Windows** en los componentes opcionales de **Desarrollo para el escritorio con C++** . Si prefiere usar una instalación existente de Clang en su máquina, elija **Herramientas de compilación de Clang-cl en C++ para v142**, otro componente opcional. La biblioteca estándar de Microsoft C++ requiere actualmente al menos Clang 8.0.0; la versión empaquetada de Clang se actualizará automáticamente para mantenerse al día con las actualizaciones de la implementación de Microsoft de la biblioteca estándar.

![Instalación de componentes de Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Configuración de un proyecto de Windows para usar herramientas de Clang

Para configurar un proyecto de Visual Studio para que use Clang, para ello, haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y elija **Propiedades**. Normalmente, primero debe elegir **Todas las configuraciones** en la parte superior del cuadro de diálogo. A continuación, en **General** > **Conjunto de herramientas de la plataforma**, elija **LLVM (clang-cl)** y, a continuación, **Aceptar**.

![Instalación de componentes de Clang](media/clang-msbuild-prop-page.png)

Si usa las herramientas de Clang que se incluyen con Visual Studio, no es necesario que realice ningún paso adicional. En los proyectos de Windows, Visual Studio llama a Clang de forma predeterminada en el modo [clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) y lo vincula con la implementación de Microsoft de la biblioteca estándar. De forma predeterminada, **clang-cl.exe** se encuentra en `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`.

Si usa una instalación de Clang personalizada, puede modificar **Proyecto** > **Propiedades** > **Directorios de VC++**  > **Propiedades de configuración** > **Directorios ejecutables** agregando la raíz de instalación personalizada de Clang como primer directorio, o bien puede cambiar el valor de la propiedad `LLVMInstallDir`. Consulte la sección [Establecimiento de una ubicación de LLVM personalizada](#custom_llvm_location) para obtener más información.

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Configuración de un proyecto de Linux para usar herramientas de Clang

En el caso de los proyectos de Linux, Visual Studio usa el front-end de Clang compatible con GCC. Las propiedades del proyecto y casi todas las marcas del compilador son idénticas.

Para configurar un proyecto de Linux en Visual Studio para que use Clang:

1. Haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y elija **Propiedades**.
1. Normalmente, primero debe elegir **Todas las configuraciones** en la parte superior del cuadro de diálogo.
1. En **General** > **Conjunto de herramientas de la plataforma**, elija **WSL_Clang_1_0** si usa el Subsistema de Windows para Linux, o bien elija **Remote_Clang_1_0** si usa una máquina remota o una máquina virtual.
1. Haga clic en **Aceptar**.

![Instalación de componentes de Clang](media/clang-msbuild-prop-page.png)

En Linux, Visual Studio usa de forma predeterminada la primera ubicación de Clang que encuentra en la propiedad de entorno PATH. Si usa una instalación de Clang personalizada, debe cambiar el valor de la propiedad `LLVMInstallDir`, o bien sustituir una ruta de acceso en **Proyecto** > **Propiedades** > **Directorios de VC++**  > **Propiedades de configuración** > **Directorios ejecutables**. Consulte la sección [Establecimiento de una ubicación de LLVM personalizada](#custom_llvm_location) para obtener más información.

## <a name="set-a-custom-llvm-location"></a><a name="custom_llvm_location"></a> Establecimiento de una ubicación de LLVM personalizada

Puede establecer una ruta de acceso personalizada de LLVM para uno o varios proyectos creando un archivo *Directory.build.props* y agregando ese archivo a la carpeta raíz de cualquier proyecto. Puede agregarlo a la carpeta raíz de la solución para aplicarlo a todos los proyectos de la solución. El archivo debe tener el siguiente aspecto (pero sustituya la ruta por su ruta de acceso real):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Establecimiento de propiedades adicionales, edición, compilación y depuración

Después de establecer una configuración de Clang, vuelva a hacer clic con el botón derecho en el nodo del proyecto y elija **Volver a cargar el proyecto**. Ahora puede compilar y depurar el proyecto con las herramientas de Clang. Visual Studio detecta que está usando el compilador de Clang y proporciona IntelliSense, resaltado, navegación y otras características de edición. Los errores y las advertencias se muestran en **Ventana de salida**. Las páginas de propiedades del proyecto para una configuración de Clang son muy similares a las de MSVC, aunque algunas características dependientes del compilador (como "Editar y continuar") no están disponibles para las configuraciones de Clang. Para establecer una opción del compilador o del enlazador de Clang que no esté disponible en las páginas de propiedades, puede agregarla manualmente en las páginas de propiedades desde **Propiedades de configuración** > **C/C++ (o Enlazador)**  > **Línea de comandos** > **Opciones adicionales**.

Al depurar, puede usar puntos de interrupción, visualización de datos y de la memoria, y la mayoría del resto de características de depuración.  

![Depuración de Clang](media/clang-debug-msbuild.png)

::: moniker-end
