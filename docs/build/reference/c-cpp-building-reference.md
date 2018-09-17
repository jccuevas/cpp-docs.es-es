---
title: Referencia de compilación de C/c ++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- compiling source code [C++], additional information
- cl.exe compiler [C++], building programs
- linker [C++], building reference
- builds [C++], additional information
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 116ddca6ed9f5e0b3ea02652958931f88cc8fc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703227"
---
# <a name="cc-building-reference"></a>Referencia de compilación de C/C++

Visual C++ proporciona dos formas de crear un programa de C o C++. La manera más fácil (y más común) es [compilar dentro del entorno de desarrollo de Visual C++](../../ide/building-cpp-projects-in-visual-studio.md). La otra forma es [construido a partir de un símbolo del sistema mediante herramientas de línea de comandos](../../build/building-on-the-command-line.md). En cualquier caso, puede crear los archivos de origen mediante el editor de código fuente de Visual C++ o un editor de terceros de su elección.

Si el programa utiliza un archivo MAKE en lugar de un archivo .vcxproj, todavía puede crear en el entorno de desarrollo como un [proyecto externo](../../ide/building-external-projects.md).

## <a name="in-this-section"></a>En esta sección

[Compilar un programa de C o C++](../../build/reference/compiling-a-c-cpp-program.md) describe el compilador, que crea un archivo de objeto que contiene código máquina, directivas del vinculador, secciones, las referencias externas y los nombres de función/datos.

[Vinculación](../../build/reference/linking.md) describe el vinculador, que combina el código de los archivos de objeto creados por el compilador y de las bibliotecas vinculadas estáticamente, resuelve las referencias de nombre y crea un archivo ejecutable.

[Versiones de lanzamiento](../../build/reference/release-builds.md) presenta información acerca de por qué y cuándo cambiar de una compilación de depuración a una versión de lanzamiento y también se describen algunos de los problemas que puede surgir al cambiar de una depuración a una versión de lanzamiento.

[Optimizar el código](../../build/reference/optimizing-your-code.md) proporciona vínculos a temas que describen los mecanismos para optimizar el código:

[Herramientas de compilación de C/C ++](../../build/reference/c-cpp-build-tools.md) proporciona las siguientes herramientas de línea de comandos para ver y manipular el resultado de la compilación:

[Errores de compilación de C/C ++](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) presenta la sección de errores de compilación en la tabla de contenido.

## <a name="related-sections"></a>Secciones relacionadas

[Referencia del preprocesador de C/C ++](../../preprocessor/c-cpp-preprocessor-reference.md) describe el preprocesador, que prepara archivos de código fuente para el compilador mediante la conversión de macros, operadores y directivas.

[Introducción a los pasos de compilación personalizada y eventos de compilación](../../ide/understanding-custom-build-steps-and-build-events.md) explica personalizar el proceso de compilación.

[Creación de un programa de C o C++](../../build/building-c-cpp-programs.md) proporciona vínculos a temas que describen cómo generar un programa desde la línea de comandos o desde el entorno de desarrollo integrado de Visual Studio.

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md) describe las opciones de configuración del compilador en el entorno de desarrollo o en la línea de comandos.

[Opciones del compilador](../../build/reference/compiler-options.md) proporciona vínculos a temas que describen las opciones del compilador.

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md) describe las opciones de configuración del vinculador dentro o fuera del entorno de desarrollo integrado.

[Opciones del vinculador](../../build/reference/linker-options.md) proporciona vínculos a temas que describen las opciones del vinculador.

[Referencia de BSCMAKE](../../build/reference/bscmake-reference.md) describe la utilidad de mantenimiento de información de examen de Microsoft (BSCMAKE. (EXE), que genera un archivo de información de examen (.bsc) de .sbr creados durante la compilación de archivos.

[Referencia de LIB](../../build/reference/lib-reference.md) describe el Administrador de bibliotecas de Microsoft (LIB.exe), que crea y administra una biblioteca de archivos de objeto de formato de archivo de objeto común (COFF).

[Referencia de EDITBIN](../../build/reference/editbin-reference.md) describe el Editor de archivos de Microsoft COFF Binary (EDITBIN. (EXE), que modifica los archivos binarios de formato de archivo de objeto común (COFF).

[Referencia de DUMPBIN](../../build/reference/dumpbin-reference.md) describe el Microsoft COFF Binary File Dumper (DUMPBIN. (EXE), que muestra información acerca de los archivos binarios de formato de archivo de objeto común (COFF).

[Referencia de NMAKE](../../build/nmake-reference.md) describe la utilidad de mantenimiento de programas de Microsoft (NMAKE. (EXE), que es una herramienta que compila proyectos en función de los comandos contenidos en un archivo de descripción.