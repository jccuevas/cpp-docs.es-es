---
title: Opciones de DUMPBIN
description: Guía de referencia de las opciones de la línea de comandos de la utilidad Microsoft DUMPBIN.
ms.date: 02/09/2020
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 54f5a22808026f4442f85d5e53a0805702e05868
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440041"
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

- [/errorreport: {None | PREGUNTAR | COLA | SEND}](errorreport-dumpbin-exe.md) (desusado)

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

Para enumerar las opciones admitidas por DUMPBIN en la línea de comandos, use el comando **/?** de la oferta.

## <a name="see-also"></a>Consulte también

\ [adicionales de herramientas de compilación de MSVC](c-cpp-build-tools.md)
\ de [línea de comandos de DUMPBIN](dumpbin-command-line.md)
[Referencia de DUMPBIN](dumpbin-reference.md)
