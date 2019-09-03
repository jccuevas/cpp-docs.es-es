---
title: Compatibilidad con Clang/LLVM en proyectos de Visual Studio Visual Studio
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: f0142c2583eeef10f159cd83451e1f3866990b75
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222634"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Compatibilidad con Clang/LLVM en proyectos de Visual Studio

::: moniker range="<=vs-2017"

La compatibilidad con Clang para proyectos de CMake y MSBuild está disponible en Visual Studio 2019.

::: moniker-end

::: moniker range="vs-2019"

Puede usar la versión 16,2 de Visual Studio 2019 con Clang para editar, compilar C++ y depurar proyectos de Visual Studio (MSBuild) que tengan como destino Windows o Linux.

## <a name="install"></a>Install

Para obtener la mejor compatibilidad con el IDE de Visual Studio, se recomienda usar las herramientas de compilador de Clang más recientes para Windows. Si aún no los tiene, puede instalarlos abriendo el instalador de Visual Studio y eligiendo  **C++ herramientas de Clang para Windows** en **desarrollo de escritorio con C++**  componentes opcionales. Si prefiere usar una instalación existente de Clang en su equipo, elija las  **C++ herramientas de compilación Clang-cl para v142.** componente opcional. La biblioteca C++ estándar de Microsoft requiere actualmente al menos Clang 8.0.0; la versión agrupada de Clang se actualizará automáticamente para mantenerse al día con las actualizaciones de la implementación de Microsoft de la biblioteca estándar. 

![Instalación de componentes de Clang](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Configurar un proyecto de Windows para usar herramientas de Clang

Para configurar un proyecto de Visual Studio para que use Clang, haga clic con el botón derecho en el nodo del proyecto en **Explorador de soluciones** y elija **propiedades**. Normalmente, primero debe elegir **todas las configuraciones** en la parte superior del cuadro de diálogo. Después, en**conjunto de herramientas**de la plataforma **General** > , elija **LLVM (Clang-cl)** y, después, **Aceptar**.

![Instalación de componentes de Clang](media/clang-msbuild-prop-page.png)

Si usa las herramientas de Clang que se incluyen con Visual Studio, no es necesario realizar ningún paso adicional. En el caso de los proyectos de Windows, Visual Studio invoca de forma predeterminada Clang en modo [Clang-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf) y vincula con la implementación de Microsoft de la biblioteca estándar. De forma predeterminada, **Clang-cl. exe** se encuentra `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`en.

 > Si usa una instalación de Clang personalizada, puede modificar >  > **las propiedades**del **proyecto**de**VC + +** **propiedades** > de configuración del**archivo ejecutable.** Agregue la raíz de instalación de Clang personalizada como primer directorio o cambie el valor de la `LLVMInstallDir` propiedad. Consulte [establecimiento de una ubicación de LLVM personalizada](#custom_llvm_location) para obtener más información.

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Configuración de un proyecto de Linux para usar herramientas de Clang

En el caso de los proyectos de Linux, Visual Studio usa el front-end compatible con Clang GCC. Las propiedades del proyecto y casi todas las marcas del compilador son idénticas

Para configurar un proyecto de Visual Studio Linux para usar Clang:

1. Haga clic con el botón secundario en el nodo del proyecto en **Explorador de soluciones** y elija **propiedades**. 
1. Normalmente, primero debe elegir **todas las configuraciones** en la parte superior del cuadro de diálogo. 
1. En **conjunto de herramientas**de la plataforma **General** > , elija **WSL_Clang_1_0** si usa el subsistema de Windows para Linux o **Remote_Clang_1_0** si usa un equipo remoto o una máquina virtual.
1. Haga clic en **Aceptar**.

![Instalación de componentes de Clang](media/clang-msbuild-prop-page.png)

En Linux, Visual Studio usa de forma predeterminada la primera ubicación de Clang que encuentra en la propiedad de entorno PATH. Si usa una instalación de Clang personalizada, debe cambiar el `LLVMInstallDir` valor de la propiedad, o bien sustituir una ruta de acceso en**propiedades** > del **proyecto** > directorios >   **de VC + +. Propiedades de configuración** **directorios ejecutables.**  >  Consulte [establecimiento de una ubicación de LLVM personalizada](#custom_llvm_location) para obtener más información.

## <a name="custom_llvm_location"></a>Establecer una ubicación de LLVM personalizada

Puede establecer una ruta de acceso personalizada para LLVM para uno o varios proyectos creando un archivo *Directory. Build. props* y agregando ese archivo a la carpeta raíz de cualquier proyecto. Puede agregarlo a la carpeta raíz de la solución para aplicarlo a todos los proyectos de la solución. El archivo debe tener este aspecto (pero sustituya su ruta de acceso real):

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>Establecer propiedades adicionales, editar, compilar y depurar

Después de configurar una configuración de Clang, vuelva a hacer clic con el botón secundario en el nodo del proyecto y elija volver a **cargar el proyecto**. Ahora puede compilar y depurar el proyecto mediante las herramientas de Clang. Visual Studio detecta que está usando el compilador Clang y proporciona IntelliSense, resaltado, navegación y otras características de edición. Los errores y las advertencias se muestran en el **ventana de salida**. Las páginas de propiedades del proyecto para una configuración de Clang son muy similares a las de MSVC, aunque algunas características dependientes del compilador, como editar y continuar, no están disponibles para las configuraciones de Clang. Para establecer una opción del compilador o del vinculador Clang que no esté disponible en las páginas de propiedades, puede agregarla manualmente en las páginas de propiedades en la**línea de comandos** de **propiedades** > de configuración**C/C++ (o enlazador).**  >  **Opciones adicionales**.  > 

Al depurar, puede usar puntos de interrupción, la memoria y la visualización de datos, y la mayoría de las demás características de depuración.  

![Depuración Clang](media/clang-debug-msbuild.png)

::: moniker-end
