---
title: Proyectos deC++ C/y sistemas de compilación en Visual Studio
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 3d82ac4569e06a4472047a79da60032ad2db43ca
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078466"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Proyectos deC++ C/y sistemas de compilación en Visual Studio

Puede usar Visual Studio para editar, compilar y compilar cualquier C++ código base con compatibilidad completa con IntelliSense sin tener que convertir ese código en un proyecto de Visual Studio o compilar con el conjunto de herramientas MSVC. Por ejemplo, puede editar un proyecto de CMake multiplataforma en Visual Studio en un equipo de Windows y, a continuación, compilarlo para Linux con g + + en una máquina remota de Linux.

## <a name="c-compilation"></a>C++previa

Para *compilar un programa* significa compilar el C++ código fuente de uno o más archivos y, a continuación, vincular esos archivos a un archivo ejecutable (. exe), una biblioteca de carga dinámica (. dll) o una biblioteca estática (. lib).

La C++ compilación básica implica tres pasos principales:

- El C++ preprocesador transforma todas las definiciones de macro y #directives en cada archivo de código fuente. Esto crea una *unidad de traducción*.
- El C++ compilador compila cada unidad de traducción en archivos objeto (. obj), aplicando las opciones del compilador que se hayan establecido.
- El *vinculador* combina los archivos objeto en un único archivo ejecutable y aplica las opciones del vinculador que se han establecido.

## <a name="the-msvc-toolset"></a>Conjunto de herramientas MSVC

El compilador de Microsoft C++ , el vinculador, las bibliotecas estándar y las utilidades relacionadas componen el conjunto de herramientas del compilador MSVC (también denominado cadena de herramientas o "herramientas de compilación"). Se incluyen en Visual Studio. También puede descargar y usar el conjunto de herramientas como un paquete independiente de forma gratuita desde la ubicación de descarga de las [herramientas de compilación para Visual Studio 2019](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Puede compilar programas simples invocando el compilador MSVC (cl. exe) directamente desde la línea de comandos. El siguiente comando acepta un archivo de código fuente único e invoca cl. exe para generar un archivo ejecutable denominado *Hello. exe*:

```cmd
cl /EHsc hello.cpp
```

Tenga en cuenta que aquí el compilador (cl. exe) C++ invoca automáticamente el preprocesador y el enlazador para generar el archivo de salida final.  Para obtener más información, vea [compilar en la línea de comandos](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Sistemas de compilación y proyectos

La mayoría de los programas del mundo real usan algún tipo de *sistema de compilación* para administrar las complejidades de la compilación de varios archivos de código fuente para varias configuraciones (por ejemplo, depurar frente a lanzamiento), varias plataformas (x86, x64, ARM, etc.), pasos de compilación personalizados e incluso varios ejecutables que se deben compilar en un orden determinado. La configuración se realiza en un archivo de configuración de compilación, y el sistema de compilación acepta ese archivo como entrada antes de invocar al compilador. El conjunto de archivos de código fuente y los archivos de configuración de compilación necesarios para compilar un archivo ejecutable se denomina *proyecto*.

En la lista siguiente se muestran varias opciones para los proyectos C++de Visual Studio:

- Cree un proyecto de Visual Studio mediante el IDE de Visual Studio y configúrelo mediante páginas de propiedades. Los proyectos de Visual Studio generan programas que se ejecutan en Windows. Para obtener información general, consulte [compilar y generar](/visualstudio/ide/compiling-and-building-in-visual-studio) en la documentación de Visual Studio.

- Abra una carpeta que contenga un archivo archivo CMakeLists. txt. La compatibilidad con CMake se integra en Visual Studio. Puede usar el IDE para editar, probar y depurar sin modificar los archivos CMake de ninguna manera. Esto le permite trabajar en el mismo proyecto de CMake que otros usuarios que pueden estar usando editores diferentes. CMake es el método recomendado para el desarrollo multiplataforma. Para obtener más información, vea [proyectos de CMake](cmake-projects-in-visual-studio.md).

- Abra una carpeta dinámica de archivos de código fuente sin archivo de proyecto. Visual Studio usará la heurística para compilar los archivos. Se trata de una manera fácil de compilar y ejecutar pequeñas aplicaciones de consola. Para obtener más información, consulte [Abrir proyectos de carpeta](open-folder-projects-cpp.md).

- Abra una carpeta que contenga un archivo make o cualquier otro archivo de configuración del sistema de compilación. Puede configurar Visual Studio para que invoque cualquier comando de compilación arbitrario agregando archivos JSON a la carpeta. Para obtener más información, consulte [Abrir proyectos de carpeta](open-folder-projects-cpp.md).

- Abra un archivo make de Windows en Visual Studio. Para obtener más información, vea [referencia de NMAKE](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>MSBuild desde la línea de comandos

Puede invocar MSBuild desde la línea de comandos pasándole un archivo. vcxproj junto con las opciones de la línea de comandos. Este enfoque requiere una buena comprensión de MSBuild y solo se recomienda cuando sea absolutamente necesario. Para obtener más información, vea [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>En esta sección

[Proyectos de Visual Studio](creating-and-managing-visual-cpp-projects.md) Cómo crear, configurar y compilar C++ proyectos en Visual Studio mediante su sistema de compilación nativo (MSBuild).

[Proyectos de CMake](cmake-projects-in-visual-studio.md) Cómo codificar, compilar e implementar proyectos de CMake en Visual Studio.

[Abrir proyectos de carpeta](open-folder-projects-cpp.md) Cómo usar Visual Studio para codificar, compilar C++ e implementar proyectos basados en cualquier sistema de compilación arbitrario o en ningún sistema de compilación. En absoluto.

[Versiones de lanzamiento](release-builds.md) Cómo crear y solucionar problemas de las compilaciones de versiones optimizadas para la implementación en usuarios finales.

[Uso del conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md)<br/>
Describe cómo usar el compilador deC++ C/y las herramientas de compilación directamente desde la línea de comandos en lugar de usar el IDE de Visual Studio.

[Compilar archivos dll en Visual Studio](dlls-in-visual-cpp.md) Cómo crear, depurar e implementar CC++ /dll (bibliotecas compartidas) en Visual Studio.

[Tutorial: crear y usar una biblioteca estática](walkthrough-creating-and-using-a-static-library-cpp.md) Cómo crear un archivo binario. lib.

[CompilarC++ aplicaciones de C/aisladas y ensamblados en paralelo](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md) Describe el modelo de implementación para aplicaciones de escritorio de Windows, en función de la idea de aplicaciones aisladas y ensamblados en paralelo.

[Configuración C++ de proyectos para destinos x64 de 64 bits](configuring-programs-for-64-bit-visual-cpp.md) Cómo dirigirse al hardware de 64 bits x64 con las herramientas de compilación de MSVC.

[Configuración C++ de proyectos para procesadores ARM](configuring-programs-for-arm-processors-visual-cpp.md) Cómo usar las herramientas de compilación de MSVC para tener como destino el hardware ARM.

[Optimizar el código](optimizing-your-code.md) Cómo optimizar el código de varias maneras, incluidas las optimizaciones guiadas por el programa.

[Configuración de programas para Windows XP](configuring-programs-for-windows-xp.md) Cómo establecer como destino Windows XP con las herramientas de compilación de MSVC.

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)<br/>
Contiene vínculos a artículos de referencia sobre cómo compilar programas en C++, sobre las opciones de compilador y vinculador, y sobre otras herramientas de compilación.
