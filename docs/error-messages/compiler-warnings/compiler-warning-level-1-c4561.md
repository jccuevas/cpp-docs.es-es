---
title: Advertencia del compilador (nivel 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 24a3ca8b35266e93f298314f45015b7a480e2af0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563792"
---
# <a name="compiler-warning-level-1-c4561"></a>Advertencia del compilador (nivel 1) C4561

'__fastcall' es incompatible con el ' / clr' opción: convertir en '\__stdcall'

El [__fastcall](../../cpp/fastcall.md) convención de llamada de función no se puede usar con el [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) opción del compilador. El compilador omite las llamadas a `__fastcall`. Para corregir esta advertencia, quite las llamadas a **__fastcall** o compile sin **/CLR**.

El ejemplo siguiente genera C4561:

```
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```