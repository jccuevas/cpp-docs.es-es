---
title: Error del compilador C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: f1f73e2585606e7e86213607a96ef713345419c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755413"
---
# <a name="compiler-error-c2588"></a>Error del compilador C2588

':: ~ Identifier ': destructor global no válido

El destructor está definido para un elemento que no sea una clase, estructura o Unión. Esto no está permitido.

Este error puede deberse a que falta un nombre de clase, estructura o unión en el lado izquierdo del operador de resolución de ámbito (`::`).

En el ejemplo siguiente se genera C2588:

```cpp
// C2588.cpp
~F();   // C2588
```
