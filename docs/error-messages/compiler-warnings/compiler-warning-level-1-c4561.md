---
title: Advertencia del compilador (nivel 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: 24a3ca8b35266e93f298314f45015b7a480e2af0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397294"
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