---
title: Compilador advertencia (nivel 1) C4461 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4461
dev_langs:
- C++
helpviewer_keywords:
- C4461
ms.assetid: 104ffecc-3dd4-4cb1-89a8-81154fbe46d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86c12208c6992b97f30bc36ea821ba26148ff751
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081408"
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