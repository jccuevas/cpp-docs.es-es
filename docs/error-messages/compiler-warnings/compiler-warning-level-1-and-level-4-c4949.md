---
title: Advertencia del compilador (niveles 1 y 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 8050edbd7a653776d046bc7b4155fd43094d9a5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187527"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Advertencia del compilador (niveles 1 y 4) C4949

pragmas 'managed' y 'unmanaged' solamente son significativas cuando se compilan con ' / clr [: opción]'

El compilador omite la [administrada](../../preprocessor/managed-unmanaged.md) y no administrados pragmas si no se compila el código fuente con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). La advertencia es informativa.

El ejemplo siguiente genera C4949:

```
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

Cuando **#pragma unmanaged** se usa sin **/CLR**, C4949 es una advertencia de nivel 4.

El ejemplo siguiente genera C4949:

```
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```