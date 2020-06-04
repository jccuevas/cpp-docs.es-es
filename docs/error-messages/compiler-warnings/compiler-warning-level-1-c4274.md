---
title: Advertencia del compilador (nivel 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5d005fccc5920aea61698a65edf9284d56366a1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377075"
---
# <a name="compiler-warning-level-1-c4274"></a>Advertencia del compilador (nivel 1) C4274

\#identidad ignorada; ver documentación para #pragma comentario (exestr, 'string')

La `#ident` directiva, que inserta una cadena especificada por el usuario en el objeto o archivo ejecutable, está en desuso. Por consiguiente, el compilador omite la directiva.

> [!CAUTION]
> Advertencia C4274 le aconseja utilizar la [directiva #pragma comment(exestr, 'string').](../../preprocessor/comment-c-cpp.md) Sin embargo, este consejo está en desuso y se revisará en una versión futura del compilador. Si utiliza `#pragma` la directiva, la herramienta del vinculador (LINK.exe) omite el registro de comentarios generado por la directiva y emite la advertencia [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). En lugar `#ident` de la directiva, se recomienda usar una cadena de recursos de versión de archivo en la aplicación.

## <a name="to-correct-this-error"></a>Para corregir este error

- Quite `#ident "`la directiva *string.* `"`

## <a name="see-also"></a>Consulte también

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Advertencia de herramientas del vinculador LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Trabajar con archivos de recursos](../../windows/working-with-resource-files.md)
