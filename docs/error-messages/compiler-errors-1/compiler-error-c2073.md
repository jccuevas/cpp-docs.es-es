---
title: Error del compilador C2073
ms.date: 11/04/2016
f1_keywords:
- C2073
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
ms.openlocfilehash: 2b45d512224ec32459e6da040a6abb0211278e78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523293"
---
# <a name="compiler-error-c2073"></a>Error del compilador C2073

'identifier': elementos de la matriz inicializada parcialmente deben tener un constructor predeterminado

Se especificaron muy pocos inicializadores para una matriz de tipos definidos por el usuario o constantes. Si no se especifican un inicializador explícito y su constructor correspondiente para un miembro de la matriz, se debe proporcionar un constructor predeterminado.

El ejemplo siguiente genera C2073:

```
// C2073.cpp
class A {
public:
   A( int );   // constructor for ints only
};
A a[3] = { A(1), A(2) };   // C2073, no default constructor
```

```
// C2073b.cpp
// compile with: /c
class B {
public:
   B();   // default constructor declared
   B( int );
};
B b[3] = { B(1), B(2) };   // OK
```