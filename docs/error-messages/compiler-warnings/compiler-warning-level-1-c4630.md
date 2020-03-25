---
title: Advertencia del compilador (nivel 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 414388fc1b9c6a7425d45e2ba92546960cadf404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199620"
---
# <a name="compiler-warning-level-1-c4630"></a>Advertencia del compilador (nivel 1) C4630

' Symbol ': el especificador de clase de almacenamiento ' extern ' no es válido en la definición de miembro

Un miembro de datos o una función miembro se define como `extern`. Los miembros no pueden ser externos, aunque todos los objetos pueden. El compilador omite la palabra clave `extern`. En el ejemplo siguiente se genera C4630:

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```
