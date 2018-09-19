---
title: Error del compilador C2698 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7ca3e7568640aabd2b7960d97ea94a11a1d5d59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118926"
---
# <a name="compiler-error-c2698"></a>Error del compilador C2698

la declaración using para ' declaración 1' no puede coexistir con la declaración using existente de ' declaración 2'

Una vez que tenga un [mediante declaración](../../cpp/using-declaration.md) para un miembro de datos, cualquier uso no se permite la declaración en el mismo ámbito que utiliza el mismo nombre, como funciones solo se pueden sobrecargar.

El ejemplo siguiente genera C2698:

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```