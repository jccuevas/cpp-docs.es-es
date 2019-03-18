---
title: Sintaxis de línea de comandos del compilador MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 5cee76d5c053dbcfef33a191dc38a958338e4a82
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821500"
---
# <a name="compiler-command-line-syntax"></a>Sintaxis de la línea de comandos del compilador

La línea de comandos de CL se utiliza la sintaxis siguiente:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

En la tabla siguiente se describe la entrada para el comando de CL.

|Entrada|Significado|
|-----------|-------------|
|*option*|Uno o varios [opciones de CL](compiler-options.md). Tenga en cuenta que todas las opciones se aplican a todos los archivos de origen especificado. Las opciones se especifican mediante una barra diagonal (/) o un guión (-). Si una opción toma un argumento, los documentos de descripción de la opción si se permite un espacio entre la opción y los argumentos. Los nombres de opción (excepto la opción /HELP) distinguen mayúsculas de minúsculas. Consulte [orden de las opciones de CL](order-of-cl-options.md) para obtener más información.|
|`file`|El nombre de uno o varios archivos de código fuente, archivos .obj o bibliotecas. CL compila archivos de código fuente y pasa los nombres de las bibliotecas y los archivos obj al vinculador. Consulte [sintaxis de nombre de archivo de CL](cl-filename-syntax.md) para obtener más información.|
|*lib*|Uno o más nombres de biblioteca. CL pasa estos nombres al vinculador.|
|*command-file*|Un archivo que contiene varias opciones y los nombres de archivo. Consulte [archivos de comandos de CL](cl-command-files.md) para obtener más información.|
|*link-opt*|Uno o varios [las opciones del vinculador MSVC](linker-options.md). CL pasa estas opciones al vinculador.|

Puede especificar cualquier número de opciones, los nombres de archivo y nombres de biblioteca, como el número de caracteres en la línea de comandos no supere los 1024, límite dictado por el sistema operativo.

Para obtener información sobre el valor devuelto de cl.exe, vea [valor devuelto de cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
>  No se garantiza que el límite de 1024 caracteres de entrada de línea de comandos siguen siendo los mismos en futuras versiones de Windows.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)
