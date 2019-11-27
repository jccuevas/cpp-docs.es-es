---
title: Advertencia del compilador (nivel 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: 982457ded987f6aee4f2891bbb7d9103b830cc99
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541790"
---
# <a name="compiler-warning-level-4-c4238"></a>Advertencia del compilador (nivel 4) C4238

se ha utilizado una extensión no estándar: rvalue de clase usado como lvalue

Por compatibilidad con versiones anteriores de Visual C++, las extensiones de Microsoft ( **/ze**) le permiten usar un tipo de clase como un valor r en un contexto que toma implícita o explícitamente su dirección. En algunos casos, como en el ejemplo siguiente, esto puede ser peligroso.

## <a name="example"></a>Ejemplo

```cpp
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Este uso provoca un error en la compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).