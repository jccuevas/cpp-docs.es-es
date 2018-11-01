---
title: Compilador advertencia (nivel 1) C4274
ms.date: 11/04/2016
f1_keywords:
- C4274
helpviewer_keywords:
- C4274
ms.assetid: 5a948680-7ed1-469f-978d-ae99d154e161
ms.openlocfilehash: dcdf804ac6e02d2bb161751db054d7f1f62ddbb5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564598"
---
# <a name="compiler-warning-level-1-c4274"></a>Compilador advertencia (nivel 1) C4274

\#Ident omitida; Consulte la documentación de #pragma comment (exestr, 'string')

El `#ident` directiva, que inserta una cadena especificada por el usuario en el objeto o archivo ejecutable, está en desuso. Por lo tanto, el compilador omite la directiva.

> [!CAUTION]
>  C4274 advertencia le informa de que se va a usar el [#pragma comment (exestr, 'string')](../../preprocessor/comment-c-cpp.md) directiva. Sin embargo, este Consejo está en desuso y se revisarán en una versión futura del compilador. Si usas el `#pragma` la directiva, la herramienta del vinculador (LINK.exe) omite el registro de comentario producido por la directiva y emite la advertencia [LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md). En lugar de la `#ident` la directiva, se recomienda usar una cadena de recurso de la versión de archivo en la aplicación.

## <a name="to-correct-this-error"></a>Para corregir este error

- Quitar el `#ident "` *cadena* `"` directiva.

## <a name="see-also"></a>Vea también

[comment (C/C++)](../../preprocessor/comment-c-cpp.md)<br/>
[Advertencia de las herramientas del vinculador LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)<br/>
[Trabajo con archivos de recursos](../../windows/working-with-resource-files.md)