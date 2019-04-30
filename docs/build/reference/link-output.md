---
title: Resultados de LINK
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: 183f83501d930188032ec4209623ef7cf1a30efa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269181"
---
# <a name="link-output"></a>Resultados de LINK

Resultados de LINK incluyen archivos .exe, DLL, archivos de asignaciones y los mensajes.

##  <a name="_core_output_files"></a> Archivos de salida

El archivo de salida predeterminado del vínculo es un archivo .exe. Si el [/DLL](dll-build-a-dll.md) , LINK generará un archivo DLL. Puede controlar el nombre de archivo de salida con el [nombre de archivo de salida (/out)](out-output-file-name.md) opción.

En el modo incremental, vínculo crea un archivo .ilk para alojar información de estado para las compilaciones incrementales posterior del programa. Para obtener más información acerca de los archivos .ilk, vea [archivos .ilk](dot-ilk-files-as-linker-input.md). Para obtener más información sobre la vinculación incremental, vea la [vincular de forma incremental (/ INCREMENTAL)](incremental-link-incrementally.md) opción.

Cuando se crea el vínculo de un programa que contiene exportaciones (normalmente una DLL), también genera un archivo .lib, a menos que se usó un archivo .exp en la compilación. Puede controlar el nombre de archivo de biblioteca de importación con la [/IMPLIB](implib-name-import-library.md) opción.

Si el [generar archivo de asignaciones (/Map)](map-generate-mapfile.md) , LINK creará un archivo de asignaciones.

Si el [generar información de depuración (/Debug)](debug-generate-debug-info.md) , LINK creará un archivo PDB para que contenga información de depuración del programa.

##  <a name="_core_other_output"></a> Otros resultados

Cuando escriba `link` sin ninguna entrada de línea de comandos, vínculo, muestra un extracto de uso que resume sus opciones.

VÍNCULO muestra un mensaje de copyright y de versión y reproduce el archivo de comandos de entrada, a menos que el [suprimir la pancarta de inicio (/ NOLOGO)](nologo-suppress-startup-banner-linker.md) se usa la opción.

Puede usar el [imprimir mensajes de progreso (/verbose)](verbose-print-progress-messages.md) opción para mostrar detalles adicionales sobre la compilación.

VÍNCULO emite mensajes de error y advertencia en el formulario LNK*nnnn*. LIB, DUMPBIN y EDITBIN también usan este prefijo de error y el intervalo de números.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
