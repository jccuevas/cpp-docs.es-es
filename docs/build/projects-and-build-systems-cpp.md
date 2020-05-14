---
title: Proyectos de C/C++ y sistemas de compilación en Visual Studio
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078466"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Proyectos de C/C++ y sistemas de compilación en Visual Studio

Puede usar Visual Studio para editar, compilar y crear cualquier código base de C++ con compatibilidad completa con IntelliSense sin tener que convertir ese código en un proyecto de Visual Studio o compilar con el conjunto de herramientas de MSVC. Por ejemplo, puede editar un proyecto de CMake multiplataforma en Visual Studio en una máquina Windows y, a continuación, compilarlo para Linux con g++ en una máquina remota de Linux.

## <a name="c-compilation"></a>Compilación de C++

*Compilar* un programa de C++ significa compilar el código fuente de uno o más archivos y, a continuación, vincular esos archivos a un archivo ejecutable (.exe), una biblioteca de carga dinámica (.dll) o una biblioteca estática (.lib).

La compilación básica de C++ implica tres pasos principales:

- El preprocesador de C++ transforma todas las directivas y las definiciones de macro en cada archivo de código fuente. Esto crea una *unidad de traducción*.
- El compilador de C++ compila cada unidad de traducción en archivos objeto (.obj) y aplica las opciones del compilador que se han establecido.
- El *enlazador* combina los archivos objeto en un único archivo ejecutable y aplica las opciones del enlazador que se han establecido.

## <a name="the-msvc-toolset"></a>Conjunto de herramientas de MSVC

El compilador de Microsoft C++, el enlazador, las bibliotecas estándar y otras utilidades relacionadas componen el conjunto de herramientas del compilador de MSVC (también denominado "cadena de herramientas" o "herramientas de compilación"). Se incluye en Visual Studio. También puede descargar y usar el conjunto de herramientas como un paquete independiente de forma gratuita desde la [ubicación de descarga de Build Tools para Visual Studio 2019](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Puede compilar programas simples invocando al compilador de MSVC (cl.exe) directamente desde la línea de comandos. El siguiente comando acepta un archivo de código fuente único e invoca a cl.exe para crear un ejecutable llamado *hello.exe*:

```cmd
cl /EHsc hello.cpp
```

Tenga en cuenta que aquí el compilador (cl.exe) invoca automáticamente al preprocesador de C++ y al enlazador para generar el archivo de salida final.  Para obtener más información, vea el artículo sobre cómo [compilar en la línea de comandos](building-on-the-command-line.md).

## <a name="build-systems-and-projects"></a>Proyectos y sistemas de compilación

La mayoría de los programas del mundo real usan algún tipo de *sistema de compilación* para administrar las complejidades de la compilación de varios archivos de código fuente para varias configuraciones (por ejemplo, depuración frente a versión), varias plataformas (x86, x64, ARM, etc.), pasos de compilación personalizados e incluso varios ejecutables que deben compilarse en un orden determinado. La configuración se realiza en un archivo de configuración de compilación, y el sistema de compilación acepta ese archivo como entrada antes de invocar al compilador. El conjunto de archivos de código fuente y los archivos de configuración de compilación necesarios para compilar un archivo ejecutable forman lo que se denomina un *proyecto*.

En la lista siguiente se muestran varias opciones para los proyectos de C++ de Visual Studio:

- Cree un proyecto de Visual Studio con el IDE de Visual Studio y configúrelo mediante páginas de propiedades. Los proyectos de Visual Studio generan programas que se ejecutan en Windows. Para obtener información general, vea [Compilar y generar en Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio) en la documentación de Visual Studio.

- Abra una carpeta que contenga un archivo CMakeLists.txt. La compatibilidad con CMake está integrada en Visual Studio. Puede usar el IDE para editar, probar y depurar sin modificar los archivos CMake de ninguna manera. Esto le permite trabajar en el mismo proyecto de CMake que otros usuarios que podrían usar editores diferentes. CMake es el método recomendado para el desarrollo multiplataforma. Para obtener más información, consulte el artículo sobre los [proyectos de CMake](cmake-projects-in-visual-studio.md).

- Abra una carpeta separada de archivos de código fuente sin un archivo de proyecto. Visual Studio usará la heurística para compilar los archivos. Se trata de una manera fácil de compilar y ejecutar pequeñas aplicaciones de consola. Para obtener más información, vea el artículo sobre los [proyectos Abrir carpeta](open-folder-projects-cpp.md).

- Abra una carpeta que contenga un archivo Make o cualquier otro archivo de configuración del sistema de compilación. Puede configurar Visual Studio para que invoque cualquier comando de compilación arbitrario agregando archivos JSON a la carpeta. Para obtener más información, vea el artículo sobre los [proyectos Abrir carpeta](open-folder-projects-cpp.md).

- Abra un archivo Make de Windows en Visual Studio. Para obtener más información, vea [Referencia de NMAKE](reference/nmake-reference.md).

## <a name="msbuild-from-the-command-line"></a>MSBuild desde la línea de comandos

Puede invocar a MSBuild desde la línea de comandos pasándole un archivo .vcxproj junto con las opciones de la línea de comandos. Este enfoque requiere una buena comprensión de MSBuild y solo se recomienda en los casos estrictamente necesarios. Para obtener más información, vea [MSBuild](msbuild-visual-cpp.md).

## <a name="in-this-section"></a>En esta sección

[Proyectos de Visual Studio](creating-and-managing-visual-cpp-projects.md): cómo crear, configurar y compilar proyectos de C++ en Visual Studio mediante su sistema de compilación nativo (MSBuild).

[Proyectos de CMake](cmake-projects-in-visual-studio.md): cómo codificar, compilar e implementar proyectos de CMake en Visual Studio.

[Proyectos de Abrir carpeta](open-folder-projects-cpp.md): cómo usar Visual Studio para codificar, compilar e implementar proyectos de C++ basados en cualquier sistema de compilación arbitrario o en ningún sistema de compilación en absoluto.

[Compilaciones de versión](release-builds.md): cómo crear y solucionar problemas de las compilaciones de versión optimizadas para su implementación en usuarios finales.

[Uso del conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md)<br/>
Describe cómo usar el compilador de C/C++ y las herramientas de compilación directamente desde la línea de comandos en lugar de usar el IDE de Visual Studio.

[Compilación de archivos DLL en Visual Studio](dlls-in-visual-cpp.md): cómo crear, depurar e implementar archivos DLL (bibliotecas compartidas) de C/C++ en Visual Studio.

[Tutorial: Creación y uso de una biblioteca estática](walkthrough-creating-and-using-a-static-library-cpp.md): cómo crear un archivo binario .lib.

[Compilación de aplicaciones aisladas y ensamblados simultáneos de C/C++](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md): describe el modelo de implementación de aplicaciones de escritorio de Windows según los conceptos de aplicaciones aisladas y ensamblados en paralelo.

[Configuración de proyectos de C++ para destinos x64 de 64 bits](configuring-programs-for-64-bit-visual-cpp.md): cómo establecer el hardware x64 de 64 bits como destino con las herramientas de compilación de MSVC.

[Configuración de proyectos de C++ para procesadores de ARM](configuring-programs-for-arm-processors-visual-cpp.md): cómo usar las herramientas de compilación de MSVC para establecer el hardware de ARM como destino.

[Optimizar el código](optimizing-your-code.md): cómo optimizar el código de varias maneras, incluidas las optimizaciones guiadas mediante programas.

[Configuración de programas para Windows XP](configuring-programs-for-windows-xp.md): cómo establecer Windows XP como destino con las herramientas de compilación de MSVC.

[Referencia de compilación de C/C++](reference/c-cpp-building-reference.md)<br/>
Contiene vínculos a artículos de referencia sobre cómo compilar programas en C++, sobre las opciones de compilador y vinculador, y sobre otras herramientas de compilación.
