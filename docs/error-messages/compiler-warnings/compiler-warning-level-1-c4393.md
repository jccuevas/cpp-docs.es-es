---
title: Advertencia del compilador (nivel 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 4226c8ecd41e890d70fa5741decae605d45b620f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777047"
---
# <a name="compiler-warning-level-1-c4393"></a>Advertencia del compilador (nivel 1) C4393

'var': const no tiene ningún efecto en el miembro de datos literal; pasa por alto

Un [literal](../../extensions/literal-cpp-component-extensions.md) miembro de datos también se especificó como const.  Puesto que un miembro de datos literal implica const, no deberá agregar const a la declaración.

El ejemplo siguiente genera C4393:

```
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```