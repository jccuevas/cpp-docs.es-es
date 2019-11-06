---
title: ADVERTENCIA del compilador (nivel 1 y nivel 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: f2876813131271ebb2561f8ea7435bb96dc2ce17
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627411"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>ADVERTENCIA del compilador (nivel 1 y nivel 4) C4949

las pragmas ' Managed ' y ' Unmanaged ' solo son significativas cuando se compilan con '/CLR [: opción] '

El compilador omite las pragmas [administradas](../../preprocessor/managed-unmanaged.md) y no administradas si el código fuente no se compila con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). La advertencia es informativa.

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