---
title: Advertencia del compilador (nivel 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: edc09bd48614abe3ea06d4365cb55110f8b9956b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162717"
---
# <a name="compiler-warning-level-1-c4393"></a>Advertencia del compilador (nivel 1) C4393

' var ': const no tiene ningún efecto en el miembro de datos literal; tendrán

Un miembro de datos [literal](../../extensions/literal-cpp-component-extensions.md) también se especificó como const.  Dado que un miembro de datos literal implica const, no es necesario agregar const a la declaración.

En el ejemplo siguiente se genera C4393:

```cpp
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```
