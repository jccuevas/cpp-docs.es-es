---
title: Advertencia del compilador (nivel 1) C4461
ms.date: 11/04/2016
f1_keywords:
- C4461
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
ms.openlocfilehash: 5cc9b08f0f25e9c92b4185f060ab123684c5d9e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591027"
---
# <a name="compiler-warning-level-1-c4461"></a>Advertencia del compilador (nivel 1) C4461

'tipo' : esta clase tiene un finalizador 'finalizador' pero no un destructor 'destructor'

La presencia de un finalizador en un tipo implica que hay recursos que eliminar. Salvo que se llame explícitamente a un finalizador desde el destructor del tipo, Common Language Runtime determinará cuándo ejecutar el finalizador, después de que el objeto haya salido del ámbito.

Si se define un destructor en el tipo y se llama explícitamente al finalizador desde el destructor, el finalizador podrá ejecutarse de forma determinista.

Para obtener más información, consulte [destructores y finalizadores](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4461.

```
// C4461.cpp
// compile with: /W1 /clr /c
ref class A {
protected:
   !A() {}   // C4461
};

// OK
ref struct B {
   ~B() {
      B::!B();
   }

   !B() {}
};
```