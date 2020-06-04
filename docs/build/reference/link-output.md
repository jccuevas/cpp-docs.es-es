---
title: Resultados de LINK
ms.date: 11/04/2016
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
ms.openlocfilehash: 253f88ed50b9f064edf976277a4618e4f101ec7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331785"
---
# <a name="link-output"></a>Resultados de LINK

La salida del vínculo incluye archivos .exe, archivos DLL, archivos de mapa y mensajes.

## <a name="output-files"></a><a name="_core_output_files"></a>Archivos de salida

El archivo de salida predeterminado de LINK es un archivo .exe. Si se especifica la opción [/DLL,](dll-build-a-dll.md) LINK genera un archivo .dll. Puede controlar el nombre del archivo de salida con la opción Nombre de archivo de salida [(/OUT).](out-output-file-name.md)

En modo incremental, LINK crea un archivo .ilk para contener información de estado para compilaciones incrementales posteriores del programa. Para obtener más información sobre los archivos .ilk, consulte [Archivos .ilk](dot-ilk-files-as-linker-input.md). Para obtener más información acerca de la vinculación incremental, consulte la opción [Vincular incrementalmente (/INCREMENTAL).](incremental-link-incrementally.md)

Cuando LINK crea un programa que contiene exportaciones (normalmente un archivo DLL), también crea un archivo .lib, a menos que se haya utilizado un archivo .exp en la compilación. Puede controlar el nombre de archivo de biblioteca de importación con la opción [/IMPLIB.](implib-name-import-library.md)

Si se especifica la opción [Generar archivo de mapa (/MAP),](map-generate-mapfile.md) LINK crea un archivo de mapa.

Si se especifica la opción Generar información de [depuración (/DEBUG),](debug-generate-debug-info.md) LINK crea una PDB para contener información de depuración para el programa.

## <a name="other-output"></a><a name="_core_other_output"></a>Otros resultados

Al escribir `link` sin ninguna otra entrada de línea de comandos, LINK muestra una instrucción de uso que resume sus opciones.

LINK muestra un mensaje de copyright y de versión y se hace eco de la entrada del archivo de comandos, a menos que se utilice la opción Suprimir banner de [inicio (/NOLOGO).](nologo-suppress-startup-banner-linker.md)

Puede utilizar la opción Imprimir mensajes de [progreso (/VERBOSE)](verbose-print-progress-messages.md) para mostrar detalles adicionales sobre la compilación.

LINK emite mensajes de error y advertencia con el formato LNK*nnnnn*. Este prefijo de error y el rango de números también son utilizados por LIB, DUMPBIN y EDITBIN.

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones de MSVC Linker](linker-options.md)
