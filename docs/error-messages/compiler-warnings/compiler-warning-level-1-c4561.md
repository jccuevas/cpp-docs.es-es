---
title: ADVERTENCIA del compilador (nivel 1) C4561
ms.date: 11/04/2016
f1_keywords:
- C4561
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
ms.openlocfilehash: b0fd27142f0404a53fa2fee87fb2309e2f54d2c2
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965972"
---
# <a name="compiler-warning-level-1-c4561"></a>ADVERTENCIA del compilador (nivel 1) C4561

' __fastcall ' no es compatible con la opción '/CLR ': se convierte en '\__stdcall '

La Convención de llamada de función [__fastcall](../../cpp/fastcall.md) no se puede usar con la opción del compilador [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) . El compilador omite las llamadas a `__fastcall`. Para corregir esta advertencia, quite las llamadas a **__fastcall** o compile sin **/CLR**.

En el ejemplo siguiente se genera C4561:

```cpp
// C4561.cpp
// compile with: /clr /W1 /c
// processor: x86
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve
```