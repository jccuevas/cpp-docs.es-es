---
title: Error del compilador C2500
ms.date: 11/04/2016
f1_keywords:
- C2500
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
ms.openlocfilehash: a5753fc99efcdb1064a21981c62faaba84d44189
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165591"
---
# <a name="compiler-error-c2500"></a>Error del compilador C2500

'identificador1': 'identificador2' ya es una clase base directa

Una clase o estructura aparece más de una vez en una lista de clases bases.

Una base directa es una mencionadas en la lista base. Una base indirecta es una clase base de una de las clases en la lista base.

Una clase no puede especificarse más de una vez como una clase base directa. Una clase puede utilizarse como una clase base indirecta más de una vez.

El ejemplo siguiente genera C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```