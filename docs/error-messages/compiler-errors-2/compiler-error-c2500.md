---
title: Error del compilador C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: 152546fce8f3ee63f8b95595bff052f18cd4ebda
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746973"
---
# <a name="compiler-error-c2500"></a>Error del compilador C2500

' identificador1 ': ' identificador2 ' ya es una clase base directa

Una clase o estructura aparece más de una vez en una lista de clases base.

Una base directa es una mencionada en la lista base. Una base indirecta es una clase base de una de las clases de la lista base.

No se puede especificar una clase como una clase base directa más de una vez. Una clase se puede utilizar como una clase base indirecta más de una vez.

En el ejemplo siguiente se genera C2500:

```cpp
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```
