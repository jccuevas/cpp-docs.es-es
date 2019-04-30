---
title: Error de las herramientas del vinculador LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: c8c62da6c1b4ea856f7a0854b998946893f2be63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299098"
---
# <a name="linker-tools-error-lnk2011"></a>Error de las herramientas del vinculador LNK2011

objeto precompilado no vinculado; imagen no se puede ejecutar

Si usa encabezados precompilados, LINK requiere que se vinculen todos los archivos de objeto creado con los encabezados precompilados. Si tiene un archivo de código fuente que se usa para generar un encabezado precompilado para su uso con otros archivos de origen, ahora debe incluir el archivo objeto creado junto con el encabezado precompilado.

Por ejemplo, si compila un archivo denominado STUB.cpp para crear un encabezado precompilado para su uso con otros archivos de origen, debe vincular con STUB.obj o se producirá este error. En las siguientes líneas de comandos, la línea 1 se usa para crear un encabezado precompilado, COMMON.pch, que se usa con PROG1.cpp y PROG2.cpp en las líneas dos y tres. El archivo STUB.cpp sólo contiene `#include` líneas (el mismo `#include` que en PROG1.cpp y PROG2.cpp) y sólo se utiliza para generar los encabezados precompilados. En la última línea, STUB.obj debe estar vinculado para evitar LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```