---
title: Error del compilador C3217 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3217
dev_langs:
- C++
helpviewer_keywords:
- C3217
ms.assetid: 99070417-c23a-4d82-bdd2-04be1a07adea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c407e8f77990bdbeea143c252a27292ac282497e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063494"
---
# <a name="compiler-error-c3217"></a>Error del compilador C3217

'param': el parámetro genérico no se puede restringir en esta declaración

Hay una restricción con formato incorrecto. El parámetro genérico de restricción debe coincidir con el parámetro de plantilla de clase genérica.

El ejemplo siguiente genera la advertencia C3217:

```
// C3217.cpp
// compile with: /clr
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T : A   // C3217
   void f();
};
```

En el ejemplo siguiente se muestra una posible resolución:

```
// C3217b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T1 : A
   void f();
};
```