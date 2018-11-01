---
title: Advertencia del compilador (nivel 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: 9a7f42b2dd65644d3f2abec58236a0b93cc6f635
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653848"
---
# <a name="compiler-warning-level-1-c4269"></a>Advertencia del compilador (nivel 1) C4269

'identifier': 'const' automática de datos inicializada con el constructor de predeterminado generado por el compilador produce resultados no confiables

Un **const** automática de instancias de una clase no trivial se inicializa con un constructor predeterminado generado por el compilador.

## <a name="example"></a>Ejemplo

```
// C4269.cpp
// compile with: /c /LD /W1
class X {
public:
   int m_data;
};

void g() {
   const X x1;   // C4269
};
```

Dado que esta instancia de la clase se genera en la pila, el valor inicial de `m_data` puede ser cualquier cosa. Además, dado que es un **const** de instancia, el valor de `m_data` nunca se puede cambiar.