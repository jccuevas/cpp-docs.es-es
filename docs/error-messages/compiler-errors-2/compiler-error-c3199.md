---
title: Error del compilador C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 934e980149ad893e6799b0ab119a148fc5652fdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402793"
---
# <a name="compiler-error-c3199"></a>Error del compilador C3199

uso no válido de pragmas de punto flotante: no se admiten excepciones en el modo no preciso

El [float_control](../../preprocessor/float-control.md) pragma se utiliza para especificar el modelo de excepción de punto flotante en una [/FP](../../build/reference/fp-specify-floating-point-behavior.md) valor distinto **/fp: precisa**.

El ejemplo siguiente genera C3199:

```
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```