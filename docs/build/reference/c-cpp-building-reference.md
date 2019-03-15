---
title: Referencia de compilación de C o C++ - Visual Studio
description: Contenido de referencia de herramientas de compilación y de sistema de proyectos de C o C++ en Visual Studio.
ms.date: 12/10/2018
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
ms.openlocfilehash: 4c3f7aa598a9c43af04c148ed0d4b3f555566ec7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812491"
---
# <a name="cc-building-reference"></a>Referencia de compilación de C/C++

Visual C++ proporciona dos formas de crear un programa de C o C++. La manera más fácil (y más común) es [generar desde el IDE de Visual Studio](../creating-and-managing-visual-cpp-projects.md). La otra forma es [construido a partir de un símbolo del sistema mediante herramientas de línea de comandos](../building-on-the-command-line.md). En cualquier caso, puede crear y editar los archivos de código fuente con Visual Studio o un editor de terceros de su elección.

## <a name="in-this-section"></a>En esta sección

[Referencia de MSBuild para proyectos de C++](msbuild-visual-cpp-overview.md)

[Referencia del compilador MSVC](compiling-a-c-cpp-program.md)<br/>
Describe el compilador MSVC, que crea un archivo de objeto que contiene código máquina, directivas del vinculador, secciones, las referencias externas y los nombres de función/datos.

[Referencia MSVC del vinculador](linking.md)<br/>
Describe al vinculador, que combina el código de los archivos de objeto creados por el compilador y de las bibliotecas vinculadas estáticamente, resuelve las referencias de nombre y crea un archivo ejecutable.

[Compatibilidad con Unicode en el compilador y el vinculador](unicode-support-in-the-compiler-and-linker.md)

[Herramientas de generación MSVC adicionales](c-cpp-build-tools.md)<br/>
Herramientas de línea de comandos adicionales para C++.

[Errores de compilación de C/C++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)<br/>
Presenta la sección de errores de compilación en la tabla de contenido.

## <a name="related-sections"></a>Secciones relacionadas

[Referencia del preprocesador de C/C++](../../preprocessor/c-cpp-preprocessor-reference.md)<br/>
Describe el preprocesador, que prepara archivos de código fuente para el compilador mediante la conversión de macros, operadores y directivas.

[Descripción de los pasos de compilación personalizada y los eventos de compilación](../understanding-custom-build-steps-and-build-events.md)<br/>
Describe la personalización del proceso de compilación.

[Creación de un programa de C o C++](../projects-and-build-systems-cpp.md)<br/>
Ofrece vínculos a temas en los que se describe la compilación de programas desde la línea de comandos o desde el entorno de desarrollo integrado de Visual Studio.

[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
Describe las opciones de configuración del compilador en el entorno de desarrollo o en la línea de comandos.

[Opciones del compilador MSVC](compiler-options.md)<br/>
Proporciona vínculos a temas que describen las opciones del compilador.

[Referencia MSVC del vinculador](linking.md)<br/>
Describe las opciones de configuración del vinculador dentro o fuera del entorno de desarrollo integrado.

[Opciones del vinculador MSVC](linker-options.md)<br/>
Proporciona vínculos a temas que describen las opciones del vinculador.

[Referencia de BSCMAKE](bscmake-reference.md)<br/>
Describe la utilidad de mantenimiento de información de examen de Microsoft (BSCMAKE. (EXE), que genera un archivo de información de examen (.bsc) de .sbr creados durante la compilación de archivos.

[Referencia de LIB](lib-reference.md)<br/>
Describe el Administrador de bibliotecas de Microsoft (LIB.exe), que crea y administra una biblioteca de archivos de objeto de formato de archivo de objeto común (COFF).

[Referencia de EDITBIN](editbin-reference.md)<br/>
Describe el Editor de archivos de Microsoft COFF Binary (EDITBIN. (EXE), que modifica los archivos binarios de formato de archivo de objeto común (COFF).

[Referencia de DUMPBIN](dumpbin-reference.md)<br/>
Describe el Microsoft COFF Binary File Dumper (DUMPBIN. (EXE), que muestra información acerca de los archivos binarios de formato de archivo de objeto común (COFF).

[Referencia de NMAKE](nmake-reference.md)<br/>
Describe la utilidad de mantenimiento de programas de Microsoft (NMAKE. (EXE), que es una herramienta que compila proyectos en función de los comandos contenidos en un archivo de descripción.
