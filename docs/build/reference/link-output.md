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
ms.openlocfilehash: 8323723f2049d3db469e874c91b99f4cfb561c72
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439316"
---
# <a name="link-output"></a>Resultados de LINK

La salida de vínculos incluye archivos. exe, dll, asignaciones y mensajes.

##  <a name="_core_output_files"></a>Archivos de salida

El archivo de salida predeterminado de LINK es un archivo. exe. Si se especifica la opción [/dll](dll-build-a-dll.md) , Link crea un archivo. dll. Puede controlar el nombre del archivo de salida con la opción [nombre de archivo de salida (/out)](out-output-file-name.md) .

En el modo incremental, LINK crea un archivo. İlk para contener información de estado de las compilaciones incrementales posteriores del programa. Para obtener más información acerca de los archivos. ILK, consulte [archivos. İlk](dot-ilk-files-as-linker-input.md). Para obtener más información sobre la vinculación incremental, vea la opción [Link incrementalmente (/incremental)](incremental-link-incrementally.md) .

Cuando LINK crea un programa que contiene exportaciones (normalmente un archivo DLL), también crea un archivo. lib, a menos que se use un archivo. exp en la compilación. Puede controlar el nombre de archivo de la biblioteca de importación con la opción [/ImpLib](implib-name-import-library.md) .

Si se especifica la opción [generar Mapfile (/MAP)](map-generate-mapfile.md) , Link crea un mapa de asignaciones.

Si se especifica la opción [generar información de depuración (/debug)](debug-generate-debug-info.md) , Link crea un archivo PDB para que contenga información de depuración del programa.

##  <a name="_core_other_output"></a>Otro resultado

Cuando escribe `link` sin ningún otro tipo de entrada de línea de comandos, el vínculo muestra una instrucción de uso que resume sus opciones.

VÍNCULO muestra un mensaje de copyright y de versión y repite la entrada del archivo de comandos, a menos que se use la opción [suprimir banner de inicio (/nologo)](nologo-suppress-startup-banner-linker.md) .

Puede usar la opción [Imprimir mensajes de progreso (/verbose)](verbose-print-progress-messages.md) para mostrar detalles adicionales sobre la compilación.

LINK emite mensajes de error y de advertencia con el formato LNK*nnnn*. LIB, DUMPBIN y EDITBIN también usan este prefijo de error y el intervalo de números.

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
