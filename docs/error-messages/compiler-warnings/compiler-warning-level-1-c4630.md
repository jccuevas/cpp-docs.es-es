---
title: ADVERTENCIA del compilador (nivel 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 893364183594782b825377f57fa4e525338d62d8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052557"
---
# <a name="compiler-warning-level-1-c4630"></a>ADVERTENCIA del compilador (nivel 1) C4630

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