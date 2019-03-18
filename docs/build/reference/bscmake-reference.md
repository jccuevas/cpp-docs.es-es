---
title: Referencia de BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: 4303e48e3d02f0f69b177e8a888157a6f90aaa89
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822358"
---
# <a name="bscmake-reference"></a>Referencia de BSCMAKE

> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.

La Utilidad de mantenimiento de información de examen de Microsoft (BSCMAKE. (EXE) genera un archivo de información de examen (.bsc) a partir de archivos .sbr creados durante la compilación. Algunas herramientas de terceros usan .bsc (archivos) para el análisis de código.

Al compilar el programa, puede crear un archivo de información de examen para el programa automáticamente, usando BSCMAKE para generar el archivo. No necesita saber cómo se ejecuta BSCMAKE si crea el archivo de información de examen en el entorno de desarrollo de Visual C++. Sin embargo, puede que desee leer este tema para comprender las opciones disponibles.

Si compila el programa fuera del entorno de desarrollo, aún puede crear un archivo .bsc personalizado que puede examinar en el entorno. Ejecute BSCMAKE en los archivos .sbr que creó durante la compilación.

> [!NOTE]
>  Puede iniciar esta herramienta solo desde el símbolo del sistema de desarrollador de Visual Studio. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

Esta sección contiene los siguientes temas:

- [Compilación de archivos de información de examen: información general](building-browse-information-files-overview.md)

- [Crear un archivo .bsc](building-a-dot-bsc-file.md)

- [Línea de comandos BSCMAKE](bscmake-command-line.md)

- [Archivo de comandos BSCMAKE](bscmake-command-file-response-file.md)

- [Opciones de BSCMAKE](bscmake-options.md)

- [Códigos de salida BSCMAKE](bscmake-exit-codes.md)

## <a name="see-also"></a>Vea también

[Herramientas de generación MSVC adicionales](c-cpp-build-tools.md)
