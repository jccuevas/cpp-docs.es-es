---
title: Sintaxis de línea de comandos del compilador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18fb22ba370a447be8cb4cb2fb96633d702a1089
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710305"
---
# <a name="compiler-command-line-syntax"></a>Sintaxis de la línea de comandos del compilador

La línea de comandos de CL se utiliza la sintaxis siguiente:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

En la tabla siguiente se describe la entrada para el comando de CL.

|Entrada|Significado|
|-----------|-------------|
|*Opción*|Uno o varios [opciones de CL](../../build/reference/compiler-options.md). Tenga en cuenta que todas las opciones se aplican a todos los archivos de origen especificado. Las opciones se especifican mediante una barra diagonal (/) o un guión (-). Si una opción toma un argumento, los documentos de descripción de la opción si se permite un espacio entre la opción y los argumentos. Los nombres de opción (excepto la opción /HELP) distinguen mayúsculas de minúsculas. Consulte [orden de las opciones de CL](../../build/reference/order-of-cl-options.md) para obtener más información.|
|`file`|El nombre de uno o varios archivos de código fuente, archivos .obj o bibliotecas. CL compila archivos de código fuente y pasa los nombres de las bibliotecas y los archivos obj al vinculador. Consulte [sintaxis de nombre de archivo de CL](../../build/reference/cl-filename-syntax.md) para obtener más información.|
|*lib*|Uno o más nombres de biblioteca. CL pasa estos nombres al vinculador.|
|*archivo de comandos*|Un archivo que contiene varias opciones y los nombres de archivo. Consulte [archivos de comandos de CL](../../build/reference/cl-command-files.md) para obtener más información.|
|*vínculo-opt*|Uno o varios [opciones del vinculador](../../build/reference/linker-options.md). CL pasa estas opciones al vinculador.|

Puede especificar cualquier número de opciones, los nombres de archivo y nombres de biblioteca, como el número de caracteres en la línea de comandos no supere los 1024, límite dictado por el sistema operativo.

Para obtener información sobre el valor devuelto de cl.exe, vea [valor devuelto de cl.exe](../../build/reference/return-value-of-cl-exe.md) .

> [!NOTE]
>  No se garantiza que el límite de 1024 caracteres de entrada de línea de comandos siguen siendo los mismos en futuras versiones de Windows.

## <a name="see-also"></a>Vea también

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)