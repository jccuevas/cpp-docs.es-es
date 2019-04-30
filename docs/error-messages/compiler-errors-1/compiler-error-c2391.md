---
title: Error del compilador C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 7683ad1580454bd7edb1fc08e5bd110a3e5c36c4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393628"
---
# <a name="compiler-error-c2391"></a>Error del compilador C2391

'identifier': 'friend' no se puede usar durante la definición de tipo

El `friend` declaración incluye una declaración de clase completa. Un `friend` declaración puede especificar una función miembro o un especificador de tipo elaborado, pero no es una declaración de clase completa.

El ejemplo siguiente genera la advertencia C2326:

```
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```