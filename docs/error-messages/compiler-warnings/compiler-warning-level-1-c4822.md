---
title: Del compilador (nivel 1) de la advertencia C4822 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4822
dev_langs:
- C++
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33748a39eae4b6f2a84cadb818570f9a311b1fe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078327"
---
# <a name="compiler-warning-level-1-c4822"></a>Advertencia del compilador (nivel 1) C4822

'member': la función miembro de clase local no tiene cuerpo

Una función de miembro de clase local se ha declarado, pero no se ha definido en la clase. Para usar una función de miembro de clase local, debe definirla en la clase. No se puede declarar en la clase y definirla fuera de ella.

Cualquier definición de la clase de una función miembro de clase local será un error.

El ejemplo siguiente genera la advertencia C4822:

```
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```