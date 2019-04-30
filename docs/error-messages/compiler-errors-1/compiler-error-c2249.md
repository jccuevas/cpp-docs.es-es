---
title: Error del compilador C2249
ms.date: 11/04/2016
f1_keywords:
- C2249
helpviewer_keywords:
- C2249
ms.assetid: bdd6697c-e04b-49b9-8e40-d9eb6d74f2b6
ms.openlocfilehash: f3f82549cf5d9230adfee7e83248e92f8e93e769
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301349"
---
# <a name="compiler-error-c2249"></a>Error del compilador C2249

'member': ninguna ruta accesible para obtener acceso al miembro declarado en la base virtual 'class'

El `member` se hereda un nonpublic `virtual` estructura o clase base.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C2249.

```
// C2249.cpp
class A {
private:
   void privFunc( void ) {};
public:
   void pubFunc( void ) {};
};

class B : virtual public A {} b;

int main() {
   b.privFunc();    // C2249, private member of A
   b.pubFunc();    // OK
}
```

## <a name="example"></a>Ejemplo

C2249 también puede producirse si intenta asignar una secuencia de la biblioteca estándar de C++ en otra secuencia.  El ejemplo siguiente genera el error C2249.

```
// C2249_2.cpp
#include <iostream>
using namespace std;
int main() {
   cout = cerr;   // C2249
   #define cout cerr;   // OK
}
```