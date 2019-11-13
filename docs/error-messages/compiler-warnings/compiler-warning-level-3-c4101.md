---
title: ADVERTENCIA del compilador (nivel 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: 5effdbb4c7e83999655641a248c389c7c4d260d0
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051902"
---
# <a name="compiler-warning-level-3-c4101"></a>ADVERTENCIA del compilador (nivel 3) C4101

' Identifier ': variable local sin referencia

La variable local nunca se usa. Esta advertencia se producirá en la situación obvia:

```cpp
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

Sin embargo, esta advertencia también se produce cuando se llama a una función miembro **estática** a través de una instancia de la clase:

```cpp
// C4101b.cpp
// compile with:  /W3
struct S {
   static int func()
   {
      return 1;
   }
};

int main() {
   S si;   // C4101, si is never used
   int y = si.func();
   return y;
}
```

En esta situación, el compilador usa información sobre `si` para tener acceso a la función **estática** , pero la instancia de la clase no es necesaria para llamar a la función **estática** ; por lo tanto, la advertencia. Para resolver esta advertencia, puede:

- Agregue un constructor, en el que el compilador usaría la instancia de `si` en la llamada a `func`.

- Quite la palabra clave **static** de la definición de `func`.

- Llame a la función **estática** explícitamente: `int y = S::func();`.