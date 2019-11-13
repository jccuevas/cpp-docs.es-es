---
title: ADVERTENCIA del compilador (nivel 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 8e514f4f3cf0cc3ee95ff709eda307b143ab3b1c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965689"
---
# <a name="compiler-warning-level-1-c4540"></a>ADVERTENCIA del compilador (nivel 1) C4540

dynamic_cast usa para convertir a base inaccesible o ambigua; se producirá un error en la prueba en tiempo de ejecución (' tipo1 ' a ' tipo2 ')

Usó `dynamic_cast` para convertir de un tipo a otro. El compilador determinó que la conversión siempre produciría un error (devuelve **null**) porque una clase base es inaccesible (`private`, por ejemplo) o ambigua (aparece más de una vez en la jerarquía de clases, por ejemplo).

A continuación se muestra un ejemplo de esta advertencia. La clase **B** se deriva de **la clase A**. El programa usa `dynamic_cast` para convertir de la clase **b** (la clase derivada) a la clase **a, lo**que siempre producirá un error porque la clase **b** se `private` y, por tanto, no se puede obtener acceso a ella. Al cambiar el acceso de **un** a **público** se resolverá la advertencia.

```cpp
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```