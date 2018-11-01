---
title: Advertencia del compilador (nivel 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 21ea45963c7e3d2afe74ebf4aa5207629ec9c8db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594263"
---
# <a name="compiler-warning-level-1-c4393"></a>Advertencia del compilador (nivel 1) C4393

'var': const no tiene ningún efecto en el miembro de datos literal; pasa por alto

Un [literal](../../windows/literal-cpp-component-extensions.md) miembro de datos también se especificó como const.  Puesto que un miembro de datos literal implica const, no deberá agregar const a la declaración.

El ejemplo siguiente genera C4393:

```
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```