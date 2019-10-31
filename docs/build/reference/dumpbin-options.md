---
title: Opciones de DUMPBIN
ms.date: 10/24/2019
f1_keywords:
- dumpbin
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 81c66f1971294531a2904a0b681819476bcc1eb2
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144560"
---
# <a name="dumpbin-options"></a>Opciones de DUMPBIN

Una opción consta de un *especificador de opción*, que puede ser un guión (`-`) o una barra diagonal (`/`), seguido del nombre de la opción. Los nombres de opciones no se pueden abreviar. Algunas opciones toman argumentos, especificados después de dos puntos (`:`). No se permiten espacios ni tabulaciones dentro de una especificación de opción. Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos. Los nombres de opciones y sus argumentos de nombre de archivo o palabra clave no distinguen mayúsculas de minúsculas. La mayoría de las opciones se aplican a todos los archivos binarios, pero algunos solo se aplican a determinados tipos de archivos. De forma predeterminada, DUMPBIN envía la información a la salida estándar. Use la opción [/out](out-dumpbin.md) para enviar la salida a un archivo.

## <a name="options-list"></a>Lista de opciones

DUMPBIN tiene las siguientes opciones:

- [/ALL](all.md)

- [/ARCHIVEMEMBERS](archivemembers.md)

- [/CLRHEADER](clrheader.md)

- [/DEPENDENTS](dependents.md)

- [/DIRECTIVES](directives.md)

- [/DISASM\[: {BYTEs\|nobytes}\]](disasm.md)

- [/ERRORREPORT: {NONE | PREGUNTAR | COLA | ENVÍAN](errorreport-dumpbin-exe.md)

- [/EXPORTS](dash-exports.md)

- [/FPO](fpo.md)

- [/HEADERS](headers.md)

- [/IMPORTS\[: nombre de archivo\]](imports-dumpbin.md)

- [/LINENUMBERS](linenumbers.md)

- [\[/LINKERMEMBER: {1 | 2}\]](linkermember.md)

- [/LOADCONFIG](loadconfig.md)

- [/NOPDB](nopdb.md)

- [/OUT: nombrearchivo](out-dumpbin.md)

- [/PDATA](pdata.md)

- [\[/PDBPATH:\] detallado](pdbpath.md)

- [/RANGEE: vaMin\[, vaMax\]](range.md)

- [\[/RAWDATA: {NONE\|1\|2\|4\|8}\[, #\]\]](rawdata.md)

- [/RELOCATIONS](relocations.md)

- [/SECTION: nombre](section-dumpbin.md)

- [/SUMMARY](summary.md)

- [/SYMBOLS](symbols.md)

- [/TLS](tls.md)

Para enumerar las opciones admitidas por DUMPBIN en la línea de comandos, use el comando **/?** desea.

## <a name="see-also"></a>Vea también

\ [adicionales de herramientas de compilación de MSVC](c-cpp-build-tools.md)
\ de [línea de comandos de DUMPBIN](dumpbin-command-line.md)
[Referencia de DUMPBIN](dumpbin-reference.md)
