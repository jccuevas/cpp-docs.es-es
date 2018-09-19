---
title: Error del compilador C3736 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3736
dev_langs:
- C++
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0a98d1e34a7dbf9e951649d88cd5a96d9f12a8a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069032"
---
# <a name="compiler-error-c3736"></a>Error del compilador C3736

'evento': debe ser un método o, en el caso de eventos administrados, opcionalmente, un miembro de datos

Nativos y eventos COM deben ser métodos. Los eventos de .NET también pueden ser miembros de datos.

El ejemplo siguiente genera C3736:

```
// C3736.cpp
struct A {
   __event int e();
};

struct B {
   int f;   // C3736
   // The following line resolves the error.
   // int f();
   B(A* a) {
      __hook(&A::e, a, &B::f);
   }
};

int main() {
}
```