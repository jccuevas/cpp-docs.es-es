---
title: Línea de comandos de BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
ms.openlocfilehash: a5a1e8f8e1d022fab9dc1bf4f67713302c11f758
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446727"
---
# <a name="bscmake-command-line"></a>Línea de comandos de BSCMAKE

Para ejecutar BSCMAKE, use la sintaxis de línea de comandos siguiente:

```
BSCMAKE [options] sbrfiles
```

Las opciones solo pueden aparecer en el `options` campo en la línea de comandos.

El *sbrfiles* campo especifica uno o más archivos .sbr creados mediante un compilador o ensamblador. Separe los nombres de los archivos .sbr con espacios o tabulaciones. Debe especificar la extensión; No hay ningún valor predeterminado. Puede especificar una ruta de acceso con el nombre de archivo, y puede usar caracteres comodín del sistema operativo (\* y?).

Durante una compilación incremental, puede especificar nuevos archivos .sbr que no formaban parte de la compilación original. Si desea que todas las contribuciones a permanecer en el archivo de información de examen, debe especificar todos los archivos .sbr (incluidos los archivos truncados) que se usaron originalmente para crear el archivo .bsc. Si se omite un archivo .sbr, se quita la contribución de dicho archivo para el archivo de información de examen.

No especifique un archivo .sbr truncado para una compilación completa. Una compilación completa requiere que las contribuciones de todos los archivos .sbr especificado. Antes de realizar una compilación completa, vuelva a compilar el proyecto y cree un nuevo archivo .sbr para cada archivo vacío.

El comando siguiente ejecuta BSCMAKE para generar un archivo denominado Main.bsc a partir de tres archivos .sbr:

```
BSCMAKE main.sbr file1.sbr file2.sbr
```

Para obtener información relacionada, consulte [archivo de comandos de BSCMAKE](../../build/reference/bscmake-command-file-response-file.md) y [opciones de BSCMAKE](../../build/reference/bscmake-options.md).

## <a name="see-also"></a>Vea también

[Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)