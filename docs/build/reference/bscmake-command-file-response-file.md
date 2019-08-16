---
title: Archivo de comandos de BSCMAKE (Archivo de respuesta)
ms.date: 11/04/2016
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
ms.openlocfilehash: 6a55fd616a00aeb3ade229bf7cff8220f86085b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295050"
---
# <a name="bscmake-command-file-response-file"></a>Archivo de comandos de BSCMAKE (Archivo de respuesta)

> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.

Puede proporcionar la totalidad o parte de la entrada de línea de comandos en un archivo de comandos. Especifique el archivo de comandos utilizando la sintaxis siguiente:

```
BSCMAKE @filename
```

Archivo de solo comandos se permite. Puede especificar una ruta de acceso con *filename*. Preceder *filename* con una arroba (**\@**). BSCMAKE no supone una extensión. Puede especificar otras *sbrfiles* en la línea de comandos después de *filename*. El archivo de comandos es un archivo de texto que contiene la entrada para BSCMAKE en el mismo orden que se especificaría en la línea de comandos. Separe los argumentos de línea de comandos con uno o varios espacios, tabulaciones o caracteres de nueva línea.

El comando siguiente llama mediante un archivo de comandos BSCMAKE:

```
BSCMAKE @prog1.txt
```

Este es un archivo de comandos de ejemplo:

```
/n /v /o main.bsc /El
/S (
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```

## <a name="see-also"></a>Vea también

[Referencia de BSCMAKE](bscmake-reference.md)
