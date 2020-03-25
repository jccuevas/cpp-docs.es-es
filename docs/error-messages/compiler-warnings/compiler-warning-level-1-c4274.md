---
title: ADVERTENCIA del compilador (nivel 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: 5f2350f275f883e7bf18aa1621d08b34132e8dfb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175851"
---
# <a name="compiler-warning-level-1-c4274"></a>ADVERTENCIA del compilador (nivel 1) C4274

se omitió \#identidad; Consulte la documentación de #pragma comment (exestr, ' String ')

La Directiva `#ident`, que inserta una cadena especificada por el usuario en el objeto o el archivo ejecutable, está en desuso. Por consiguiente, el compilador omite la Directiva.

> [!CAUTION]
>  Warning C4274 le aconseja usar la directiva [#pragma comment (exestr, ' String ')](../../preprocessor/comment-c-cpp.md) . Sin embargo, este Consejo está en desuso y se revisará en una versión futura del compilador. Si usa la Directiva `#pragma`, la herramienta vinculador (LINK. exe) omite el registro de comentario generado por la Directiva y emite la advertencia [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). En lugar de la Directiva `#ident`, se recomienda usar una cadena de recurso de versión de archivo en la aplicación.

## <a name="to-correct-this-error"></a>Para corregir este error

- Quite la `#ident "`*cadena*`"` Directiva.

## <a name="see-also"></a>Consulte también

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Advertencia de las herramientas del vinculador LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Trabajo con archivos de recursos](../../windows/working-with-resource-files.md)
