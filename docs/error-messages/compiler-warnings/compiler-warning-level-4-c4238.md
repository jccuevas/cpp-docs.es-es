---
title: Advertencia del compilador (nivel 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: c5ffa07b06f010d10edc14aa7576bb614aa9dd04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471908"
---
# <a name="compiler-warning-level-4-c4238"></a>Advertencia del compilador (nivel 4) C4238

ha utilizado una extensión no estándar: valor-r de clase utilizado como valor l

Para ofrecer compatibilidad con versiones anteriores de Visual C++, las extensiones de Microsoft (**/Ze**) le permiten usar un tipo de clase como un valor r en un contexto que implícita o explícitamente tome su dirección. En algunos casos, como en el ejemplo siguiente, esto puede ser peligroso.

## <a name="example"></a>Ejemplo

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Este uso produce un error en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).