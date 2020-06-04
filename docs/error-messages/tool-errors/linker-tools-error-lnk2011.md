---
title: Error de las herramientas del vinculador LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: e08f068099af68375523eae0f0cc4d63960f3261
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194816"
---
# <a name="linker-tools-error-lnk2011"></a>Error de las herramientas del vinculador LNK2011

objeto precompilado no vinculado en; es posible que la imagen no se ejecute

Si usa encabezados precompilados, LINK requiere que todos los archivos objeto creados con encabezados precompilados se vinculen en. Si tiene un archivo de código fuente que utiliza para generar un encabezado precompilado para usarlo con otros archivos de código fuente, ahora debe incluir el archivo objeto creado junto con el encabezado precompilado.

Por ejemplo, Si compila un archivo llamado STUB. cpp para crear un encabezado precompilado para usarlo con otros archivos de código fuente, debe vincular con STUB. obj o obtendrá este error. En las siguientes líneas de comandos, línea uno se usa para crear un encabezado precompilado, COMMON. PCH, que se usa con PROG1. cpp y PROG2. cpp en las líneas dos y tres. El archivo STUB. cpp solo contiene líneas `#include` (las mismas líneas `#include` que en PROG1. cpp y PROG2. cpp) y solo se usa para generar encabezados precompilados. En la última línea, STUB. obj debe estar vinculado en para evitar LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```
