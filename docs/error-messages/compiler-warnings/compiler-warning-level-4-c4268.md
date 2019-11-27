---
title: Advertencia del compilador (nivel 4) C4268
ms.date: 11/04/2016
f1_keywords:
- C4268
helpviewer_keywords:
- C4268
ms.assetid: d0511e80-904f-4ee1-b4d7-39b5c0bd8234
ms.openlocfilehash: 1d0531b79ef29d2aa9528cc29046fa9e9514c379
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541982"
---
# <a name="compiler-warning-level-4-c4268"></a>Advertencia del compilador (nivel 4) C4268

' Identifier ': los datos estáticos/globales ' const ' inicializados con el constructor predeterminado generado por el compilador llenan el objeto con ceros

Una instancia global o estática **const** de una clase no trivial se inicializa con un constructor predeterminado generado por el compilador.

## <a name="example"></a>Ejemplo

```cpp
// C4268.cpp
// compile with: /c /LD /W4
class X {
public:
   int m_data;
};

const X x1;   // C4268
```

Como esta instancia de la clase es **const**, no se puede cambiar el valor de `m_data`.