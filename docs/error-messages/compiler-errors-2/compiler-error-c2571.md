---
title: Error del compilador C2571 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2571
dev_langs:
- C++
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30cc078251d0511da77e08690db275a788973ffb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067940"
---
# <a name="compiler-error-c2571"></a>Error del compilador C2571

'function': función virtual no puede estar en la unión "union"

Se declara una unión con una función virtual. Puede declarar una función virtual solo en una clase o estructura.  Soluciones posibles:

1. Cambie la unión a una clase o estructura.

1. Hacer que la función no virtual.

El ejemplo siguiente genera C2571:

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```