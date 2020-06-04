---
title: Referencia de BSCMAKE
ms.date: 05/06/2019
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: f95e34b9599de628463b9f92ebf8f01036237891
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320734"
---
# <a name="bscmake-reference"></a>Referencia de BSCMAKE

> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.

La Utilidad de mantenimiento de información de examen de Microsoft (BSCMAKE. (EXE) genera un archivo de información de examen (.bsc) a partir de archivos .sbr creados durante la compilación. Ciertas herramientas de terceros utilizan archivos .bsc para el análisis de código.

Al compilar el programa, puede crear un archivo de información de examen para el programa automáticamente, usando BSCMAKE para generar el archivo. No es necesario saber cómo ejecutar BSCMAKE si crea el archivo de información de exploración en el entorno de desarrollo de Visual Studio. Sin embargo, puede que desee leer este tema para comprender las opciones disponibles.

Si compila el programa fuera del entorno de desarrollo, aún puede crear un archivo .bsc personalizado que puede examinar en el entorno. Ejecute BSCMAKE en los archivos .sbr que creó durante la compilación.

> [!NOTE]
> Puede iniciar esta herramienta solo desde el símbolo del sistema de Visual Studio Developer. No puede iniciarla desde un símbolo del sistema ni desde el Explorador de archivos.

En esta sección se incluyen los siguientes temas:

- [Compilar archivos de información de examen: información general](building-browse-information-files-overview.md)

- [Creación de un archivo .bsc](building-a-dot-bsc-file.md)

- [Línea de comandos de BSCMAKE](bscmake-command-line.md)

- [Archivo de comandos de BSCMAKE](bscmake-command-file-response-file.md)

- [Opciones de BSCMAKE](bscmake-options.md)

- [Códigos de salida de BSCMAKE](bscmake-exit-codes.md)

## <a name="see-also"></a>Consulte también

[Herramientas de compilación de MSVC adicionales](c-cpp-build-tools.md)
