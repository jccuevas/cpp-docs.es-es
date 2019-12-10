---
title: Advertencia del compilador (nivel 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: cc913a4f92963437347fbc708eca03c25ab9d403
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991471"
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
