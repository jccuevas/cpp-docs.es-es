---
title: Error del compilador C3891 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3891
dev_langs:
- C++
helpviewer_keywords:
- C3891
ms.assetid: 6e1a9458-97f5-4580-bc0f-aa97a1bfd20d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c85e5fa5ed5e6f202750fef05ffc96e9a0c86bc1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051703"
---
# <a name="compiler-error-c3891"></a>Error del compilador C3891

'var': un miembro de datos literal no puede usarse como un valor l

Un [literal](../../windows/literal-cpp-component-extensions.md) variable es const, y su valor no puede cambiarse una vez que se inicializa en la declaración.

El ejemplo siguiente genera C3891:

```
// C3891.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   Y1::staticConst = 0;   // C3891
}
```