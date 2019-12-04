---
title: Error del compilador C3198
ms.date: 11/04/2016
f1_keywords:
- C3198
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
ms.openlocfilehash: b9e0ce4a84b312e3a9277898b3fc264ea3ae22bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739160"
---
# <a name="compiler-error-c3198"></a>Error del compilador C3198

uso no válido de pragmas de punto flotante: fenv_access pragma solo funciona en modo preciso

[fenv_access](../../preprocessor/fenv-access.md) pragma se usó en un valor de [/FP](../../build/reference/fp-specify-floating-point-behavior.md) que no sea **/FP: precise**.

En el ejemplo siguiente se genera C3198:

```cpp
// C3198.cpp
// compile with: /fp:fast
#pragma fenv_access(on)   // C3198
```
