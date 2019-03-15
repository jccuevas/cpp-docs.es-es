---
title: Los proyectos de C o C++ y los sistemas de compilación en Visual Studio
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 12/08/2018
f1_keywords:
- vcbuilding
- buildingaprogramVC
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.openlocfilehash: 0c4a74ce69f5c52eb6fc107ea477e5715e86ecd2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826584"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Los proyectos de C o C++ y los sistemas de compilación en Visual Studio

Puede usar Visual Studio 2017 para editar, compilar y generar cualquier base con compatibilidad completa de IntelliSense de código de C++ sin tener que convertir ese código en un proyecto de Visual Studio o compilar con el conjunto de herramientas MSVC. Por ejemplo, puede editar un proyecto de CMake multiplataforma en Visual Studio en un equipo Windows y luego lo compilará para Linux con g ++ en un equipo Linux remoto.

## <a name="c-compilation"></a>Compilación de C++

Para *compilar* significa que un programa de C++ compilar código fuente a partir de uno o varios archivos y, a continuación, vincular esos archivos en un archivo ejecutable (.exe), una biblioteca de carga dinámica (.dll) o una biblioteca estática (.lib). 

Compilación en C++ básica implica tres pasos principales:

- El preprocesador de C++ transforma todas las definiciones de macros y #directives en cada archivo de código fuente. Esto crea un *unidad de traducción*.
- El compilador de C++ compila cada unidad de traducción en archivos objeto (.obj), aplicar cualquier opción del compilador se han establecido.
- El *vinculador* combina los archivos de objeto en un único archivo ejecutable, aplicar las opciones del vinculador que se han establecido. 

## <a name="the-msvc-toolset"></a>El conjunto de herramientas MSVC

El compilador, vinculador, bibliotecas estándar y utilidades relacionadas de Microsoft C++ conforman el conjunto de herramientas del compilador MSCV (también denominada una cadena de herramientas o "herramientas de compilación"). Estos se incluyen en Visual Studio. También puede descargar y usar el conjunto de herramientas como un paquete independiente de forma gratuita desde el [ubicación de descarga de Build Tools para Visual Studio 2017](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017).

Puede crear programas sencillos al invocar el compilador de MSVC (cl.exe) directamente desde la línea de comandos. El comando siguiente acepta un archivo de código fuente único e invoca cl.exe para compilar un archivo ejecutable denominado *hello.exe*: 

```cmd
cl /EHsc hello.cpp
```
Tenga en cuenta que aquí el compilador (cl.exe) invoca automáticamente el preprocesador de C++ y el vinculador para generar el archivo de salida final.  Para obtener más información, consulte [a partir de la línea de comandos](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Crear sistemas y proyectos

Mayoría de los programas reales de utiliza algunas *sistema de compilación* para administrar las complejidades de varios archivos de origen para varias configuraciones de compilación (es decir, debug frente a versión), varias plataformas (x86, x64, ARM, y así sucesivamente), compilación personalizada los pasos e incluso varios archivos ejecutables que deben compilarse en un orden determinado. Asegúrese de configuración en los archivos de configuración de compilación y el sistema de compilación acepta ese archivo como entrada antes de invocar el compilador. El conjunto de archivos de código fuente y archivos de configuración de compilación necesarios para compilar un archivo ejecutable se denomina un *proyecto*. 

La lista siguiente muestra varias opciones para proyectos de Visual Studio - C++:

- crear un proyecto de Visual Studio mediante el IDE de Visual Studio y configurarlo mediante el uso de páginas de propiedades. Proyectos de Visual Studio producen programas que se ejecutan en Windows. Para obtener información general, consulte [compilar y generar](/visualstudio/ide/compiling-and-building-in-visual-studio) en la documentación de Visual Studio.

- abrir una carpeta que contiene un archivo CMakeLists.txt. Se integra compatibilidad con CMake en Visual Studio. Puede usar el IDE para editar, probar y depurar sin modificar los archivos de CMake de ninguna manera. Esto le permite trabajar en el mismo proyecto de CMake que otras personas que podría estar usando los distintos editores. CMake es el enfoque recomendado para el desarrollo multiplataforma. Para obtener más información, consulte [proyectos CMake](cmake-projects-in-visual-studio.md).
 
- Abra una carpeta de archivos de origen no estricta con ningún archivo de proyecto. Visual Studio usará heurística para compilar los archivos. Se trata de una manera fácil de compilar y ejecutar aplicaciones de consola pequeño. Para obtener más información, consulte [proyectos Abrir carpeta](open-folder-projects-cpp.md).

- Abra una carpeta que contiene un archivo MAKE, o cualquier otro archivo de configuración del sistema de compilación. Puede configurar Visual Studio para invocar cualquier comando de compilación arbitraria mediante la adición de archivos JSON a la carpeta. Para obtener más información, consulte [proyectos Abrir carpeta](open-folder-projects-cpp.md).
 
- Abra un archivo MAKE de Windows en Visual Studio. Para obtener más información, consulte [referencia de NMAKE](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>MSBuild desde la línea de comandos 

Puede invocar MSBuild desde la línea de comandos, pasando un archivo .vcxproj junto con las opciones de línea de comandos. Este enfoque requiere una buena comprensión de MSBuild y se recomienda sólo cuando sea absolutamente necesario. Para obtener más información, vea [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>En esta sección

[Proyectos de Visual Studio](creating-and-managing-visual-cpp-projects.md) cómo creación, configuración y compilación de C++ (MSBuild) de sistema de compilación de proyectos en Visual Studio con su nativo.

[Los proyectos de CMake](cmake-projects-in-visual-studio.md) cómo codificar, compilar e implementar proyectos de CMake en Visual Studio.

[Abrir carpeta proyectos](open-folder-projects-cpp.md) en función de cómo usar Visual Studio para codificar, compilar e implementar proyectos de C++ en cualquier sistema de compilación arbitraria o ningún sistema de compilación. En absoluto. 

[Versiones de lanzamiento](release-builds.md) compilaciones de creación y solución de problemas de lanzamiento optimizadas para la implementación a los usuarios finales.

[Usar el conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md)<br/>
Describe cómo usar el compilador de C/C ++ y crear herramientas directamente desde la línea de comandos en lugar de utilizar el IDE de Visual Studio.

[Generar archivos DLL en Visual Studio](dlls-in-visual-cpp.md) cómo crear, depurar e implementar archivos DLL de C o C++ (bibliotecas compartidas) en Visual Studio.

[Compilar aplicaciones aisladas de C/C ++ y ensamblados en paralelo](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) describe el modelo de implementación de aplicaciones de escritorio de Windows, en función de la idea de aplicaciones aisladas y ensamblados en paralelo.

[Configurar los proyectos de C++ de 64 bits, x64 destinos](configuring-programs-for-64-bit-visual-cpp.md) cómo al destino de 64 bits x64 hardware con el MSVC las herramientas de compilación.

[Configurar proyectos de C++ para procesadores ARM](configuring-programs-for-arm-processors-visual-cpp.md) cómo usar las herramientas de generación MSVC para hardware ARM de destino.

[Optimizar el código](optimizing-your-code.md) cómo optimizar el código de varias maneras, incluidas las optimizaciones guiadas por el programa.

[Configurar programas para Windows XP](configuring-programs-for-windows-xp.md) cómo las herramientas de compilación de Windows XP con el MSVC de destino.

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)<br/>
Contiene vínculos a artículos de referencia sobre cómo compilar programas en C++, sobre las opciones de compilador y vinculador, y sobre otras herramientas de compilación.
