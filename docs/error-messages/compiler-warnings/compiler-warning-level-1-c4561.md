---
title: Compilador advertencia (nivel 1) C4561 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4561
dev_langs:
- C++
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba0770a8b8b42c8174d421f55dd45ff7f335d06
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46115793"
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