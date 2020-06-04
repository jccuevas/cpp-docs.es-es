---
title: Advertencia del compilador (niveles 1 y 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 7ce8b3242def187e4b8b442f403f92f013a9ca6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164786"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Advertencia del compilador (niveles 1 y 4) C4949

las pragmas ' Managed ' y ' Unmanaged ' solo son significativas cuando se compilan con '/CLR [: opción] '

El compilador omite las pragmas [administradas](../../preprocessor/managed-unmanaged.md) y no administradas si el código fuente no se compila con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). Esta advertencia es informativa.

En el ejemplo siguiente se genera C4949:

```cpp
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

Cuando se usa **#pragma no administrada** sin **/CLR**, C4949 es una advertencia de nivel 4.

En el ejemplo siguiente se genera C4949:

```cpp
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```
