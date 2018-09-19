---
title: Error del compilador C2079 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2079
dev_langs:
- C++
helpviewer_keywords:
- C2079
ms.assetid: ca58d6d5-eccd-40b7-ba14-c003223c5bc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ddea9a8651a62f7cbb857e1d53962142471c2cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032190"
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