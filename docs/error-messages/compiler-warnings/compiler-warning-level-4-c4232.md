---
title: Advertencia del compilador (nivel 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: c0e79dfa4564960a5660f0932b142b436370ac05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173925"
---
# <a name="compiler-warning-level-4-c4232"></a>Advertencia del compilador (nivel 4) C4232

se usó una extensión no estándar: ' Identifier ': la dirección de DllImport ' DllImport ' no es estática, no se garantiza la identidad

En las extensiones de Microsoft (/ZE), puede asignar un valor no estático como dirección de una función declarada con el modificador **DllImport** . En compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)), se produce un error.

En el ejemplo siguiente se genera C4232:

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```
