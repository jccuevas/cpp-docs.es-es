---
title: Compilador advertencia (nivel 3) C4101
ms.date: 11/04/2016
f1_keywords:
- C4101
helpviewer_keywords:
- C4101
ms.assetid: d98563cd-9dce-4aae-8f12-bd552a4ea677
ms.openlocfilehash: d1109a32e754a6055e5e1d90632ad85332d832f1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402325"
---
# <a name="compiler-warning-level-3-c4101"></a>Compilador advertencia (nivel 3) C4101

'identificador': variable local sin referencia

La variable local nunca se utiliza. Esta advertencia se produce en la siguiente situación:

```
// C4101a.cpp
// compile with: /W3
int main() {
int i;   // C4101
}
```

Sin embargo, esta advertencia también se produce cuando se llama a un **estático** función miembro a través de una instancia de la clase:

```
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

En esta situación, el compilador utiliza información acerca de `si` para tener acceso a la **estático** función, pero la instancia de la clase no es necesaria para llamar a la **estático** función; por lo tanto, la advertencia. Para resolver esta advertencia, puede:

- Agregue un constructor, en el que el compilador utilizará la instancia de `si` en la llamada a `func`.

- Quitar el **estático** palabra clave de la definición de `func`.

- Llame a la **estático** explícitamente la función: `int y = S::func();`.