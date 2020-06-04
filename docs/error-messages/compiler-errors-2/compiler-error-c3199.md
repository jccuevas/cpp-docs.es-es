---
title: Error del compilador C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 2f0ca98dc44a78adde378a0f80078ae30c590e11
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738822"
---
# <a name="compiler-error-c3199"></a>Error del compilador C3199

uso no válido de pragmas de punto flotante: no se admiten excepciones en el modo no preciso

La [float_control](../../preprocessor/float-control.md) pragma se usó para especificar el modelo de excepción de punto flotante con un valor de [/FP](../../build/reference/fp-specify-floating-point-behavior.md) que no sea **/FP: precise**.

En el ejemplo siguiente se genera C3199:

```cpp
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```
