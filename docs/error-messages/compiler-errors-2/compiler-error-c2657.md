---
title: Error del compilador C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: e060c2b9a38866a898a3c5ada9e595464050877e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756102"
---
# <a name="compiler-error-c2657"></a>Error del compilador C2657

' Class::* ' se encuentra al principio de una instrucción (¿olvidó especificar un tipo?)

La línea comenzó con un identificador de puntero a miembro.

Este error puede deberse a que falta un especificador de tipo en la declaración de un puntero a un miembro.

En el ejemplo siguiente se genera C2657:

```cpp
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```
