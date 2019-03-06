---
title: Sintaxis de la línea de comandos del compilador
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: f5e611064f7f4670056a42e5ccee1f291fbdd567
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421238"
---
# <a name="compiler-command-line-syntax"></a>Sintaxis de la línea de comandos del compilador

La línea de comandos de CL se utiliza la sintaxis siguiente:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

En la tabla siguiente se describe la entrada para el comando de CL.

|Entrada|Significado|
|-----------|-------------|
|*option*|Uno o varios [opciones de CL](../../build/reference/compiler-options.md). Tenga en cuenta que todas las opciones se aplican a todos los archivos de origen especificado. Las opciones se especifican mediante una barra diagonal (/) o un guión (-). Si una opción toma un argumento, los documentos de descripción de la opción si se permite un espacio entre la opción y los argumentos. Los nombres de opción (excepto la opción /HELP) distinguen mayúsculas de minúsculas. Consulte [orden de las opciones de CL](../../build/reference/order-of-cl-options.md) para obtener más información.|
|`file`|El nombre de uno o varios archivos de código fuente, archivos .obj o bibliotecas. CL compila archivos de código fuente y pasa los nombres de las bibliotecas y los archivos obj al vinculador. Consulte [sintaxis de nombre de archivo de CL](../../build/reference/cl-filename-syntax.md) para obtener más información.|
|*lib*|Uno o más nombres de biblioteca. CL pasa estos nombres al vinculador.|
|*command-file*|Un archivo que contiene varias opciones y los nombres de archivo. Consulte [archivos de comandos de CL](../../build/reference/cl-command-files.md) para obtener más información.|
|*link-opt*|Uno o varios [opciones del vinculador](../../build/reference/linker-options.md). CL pasa estas opciones al vinculador.|

Puede especificar cualquier número de opciones, los nombres de archivo y nombres de biblioteca, como el número de caracteres en la línea de comandos no supere los 1024, límite dictado por el sistema operativo.

Para obtener información sobre el valor devuelto de cl.exe, vea [valor devuelto de cl.exe](../../build/reference/return-value-of-cl-exe.md) .

> [!NOTE]
>  No se garantiza que el límite de 1024 caracteres de entrada de línea de comandos siguen siendo los mismos en futuras versiones de Windows.

## <a name="see-also"></a>Vea también

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)
