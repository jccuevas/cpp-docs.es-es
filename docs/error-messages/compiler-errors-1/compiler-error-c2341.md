---
title: Error del compilador C2341
ms.date: 11/04/2016
f1_keywords:
- C2341
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
ms.openlocfilehash: 4356182758398fa7ed1ec6a069affa4bb99ace1a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631691"
---
# <a name="compiler-error-c2341"></a>Error del compilador C2341

'section name': se debe definir el segmento utilizando #pragma data_seg, code_seg o la sección anterior para usar

Un [asignar](../../cpp/allocate.md) instrucción hace referencia a un segmento aún no se han definido por [code_seg](../../preprocessor/code-seg.md), [data_seg](../../preprocessor/data-seg.md), o [sección](../../preprocessor/section.md) pragmas.

El ejemplo siguiente genera C2341:

```
// C2341.cpp
// compile with: /c
__declspec(allocate(".test"))   // C2341
int j = 1;
```

Posible resolución:

```
// C2341b.cpp
// compile with: /c
#pragma data_seg(".test")
__declspec(allocate(".test"))
int j = 1;
```