---
title: Sintaxis de línea de comandos del compilador MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 6a56474b537d78a3d0bea8a74d9082007cd2e295
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320544"
---
# <a name="compiler-command-line-syntax"></a>Sintaxis de la línea de comandos del compilador

La línea de mandatos CL utiliza la sintaxis siguiente:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

En la tabla siguiente se describe la entrada al mandato CL.

|Entrada|Significado|
|-----------|-------------|
|*Opción*|Una o más [opciones CL](compiler-options.md). Tenga en cuenta que todas las opciones se aplican a todos los archivos de origen especificados. Las opciones se especifican mediante una barra diagonal (/) o un guión (-). Si una opción toma un argumento, la descripción de la opción documenta si se permite un espacio entre la opción y los argumentos. Los nombres de opciones (excepto la opción /HELP) distinguen entre mayúsculas y minúsculas. Consulte [Orden de opciones de CL](order-of-cl-options.md) para obtener más información.|
|`file`|El nombre de uno o más archivos de origen, archivos .obj o bibliotecas. CL compila archivos de origen y pasa los nombres de los archivos .obj y bibliotecas al vinculador. Consulte [Sintaxis de nombre de archivo CL](cl-filename-syntax.md) para obtener más información.|
|*Lib*|Uno o más nombres de biblioteca. CL pasa estos nombres al vinculador.|
|*comando-archivo*|Archivo que contiene varias opciones y nombres de archivo. Consulte [Archivos de comandos CL](cl-command-files.md) para obtener más información.|
|*link-opt*|Una o más opciones de [vinculador MSVC](linker-options.md). CL pasa estas opciones al vinculador.|

Puede especificar cualquier número de opciones, nombres de archivo y nombres de biblioteca, siempre que el número de caracteres en la línea de comandos no supere 1024, el límite dictado por el sistema operativo.

Para obtener información sobre el valor devuelto de cl.exe, vea [Valor devuelto de cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
> No se garantiza que el límite de entrada de línea de comandos de 1024 caracteres siga siendo el mismo en futuras versiones de Windows.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)
