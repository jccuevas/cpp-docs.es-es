---
title: Error del compilador C2079
ms.date: 11/04/2016
f1_keywords:
- C2079
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
ms.openlocfilehash: 68435610680e3b21415a1d9439a8133fd1e2557f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391964"
---
# <a name="compiler-error-c2079"></a>Error del compilador C2079

'identificador' utiliza la clase/struct/union sin definir 'name'

El identificador especificado es una clase no definida, estructura o unión.

Este error puede deberse al inicializar una unión anónima.

El ejemplo siguiente genera C2079:

```
// C2079.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   std::ifstream g;   // C2079
}
```

Posible resolución:

```
// C2079b.cpp
// compile with: /EHsc
#include <fstream>
int main( ) {
   std::ifstream g;
}
```

C2079 también puede producirse si intenta declarar un objeto en la pila de un tipo cuya declaración adelantada está solo en el ámbito.

```
// C2079c.cpp
class A;

class B {
   A a;   // C2079
};

class A {};
```

Posible resolución:

```
// C2079d.cpp
// compile with: /c
class A;
class C {};

class B {
   A * a;
   C c;
};

class A {};
```