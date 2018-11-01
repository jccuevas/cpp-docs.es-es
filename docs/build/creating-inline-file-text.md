---
title: Crear el texto de un archivo en línea
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
ms.openlocfilehash: 4989d0757e893a7bc4b0a0e8937afee18719aa4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523123"
---
# <a name="creating-inline-file-text"></a>Crear el texto de un archivo en línea

Archivos en línea son temporales o permanentes.

## <a name="syntax"></a>Sintaxis

```
inlinetext
.
.
.
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Comentarios

Especificar *inlinetext* en la primera línea después del comando. Marcar el final con corchetes angulares dobles (<<) al principio de una línea independiente. El archivo contiene todos los *inlinetext* antes de los delimitadores de corchetes. El *inlinetext* puede tener expansiones de macro y sustituciones, pero no las directivas o los comentarios de archivo MAKE. Literalmente se tratan los espacios, tabuladores y caracteres de nueva línea.

Un archivo temporal existe mientras dure la sesión y puede ser reutilizado por otros comandos. Especificar **mantener** después de los corchetes angulares de cierre para conservar el archivo después de la sesión NMAKE; un archivo sin nombre se conserva en el disco con el nombre de archivo generado. Especificar **NOKEEP** o nada para un archivo temporal. **MANTENER** y **NOKEEP** no distinguen mayúsculas de minúsculas.

## <a name="see-also"></a>Vea también

[Archivos insertados en un archivo MAKE](../build/inline-files-in-a-makefile.md)