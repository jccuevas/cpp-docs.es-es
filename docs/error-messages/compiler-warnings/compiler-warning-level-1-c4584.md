---
title: ADVERTENCIA del compilador (nivel 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 831789f5295fcf91e83de3bd0bba12c8429e9fa3
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966236"
---
# <a name="compiler-warning-level-1-c4584"></a>ADVERTENCIA del compilador (nivel 1) C4584

' Class1 ': la clase base ' clase2 ' ya es una clase base de ' class3 '

La clase que ha definido hereda de dos clases, una de las cuales hereda de la otra. Por ejemplo:

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

En este caso, se emitirá una advertencia en la clase C porque hereda tanto de la clase A como de la clase B, que también hereda de la clase A. Esta advertencia sirve como recordatorio de que debe calificar totalmente el uso de los miembros de estas clases base, o bien se generará un error del compilador debido a la ambigüedad en cuanto al miembro de clase al que se hace referencia.