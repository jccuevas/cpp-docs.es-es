---
title: Advertencia del compilador (nivel 1) C4269
ms.date: 11/04/2016
f1_keywords:
- C4269
helpviewer_keywords:
- C4269
ms.assetid: 96c97bbc-068a-4b65-8cd8-4ed5dca04c15
ms.openlocfilehash: e2e1781bf4c1b9ac0ee29d0b5900daa6cfe94b45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199776"
---
# <a name="compiler-warning-level-1-c4269"></a>Advertencia del compilador (nivel 1) C4269

' Identifier ': los datos automáticos ' const ' inicializados con el constructor predeterminado generado por el compilador generan resultados no confiables

Una instancia automática **const** de una clase no trivial se inicializa con un constructor predeterminado generado por el compilador.

## <a name="example"></a>Ejemplo

```cpp
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

Puesto que esta instancia de la clase se genera en la pila, el valor inicial de `m_data` puede ser cualquier cosa. Además, como es una instancia **const** , el valor de `m_data` nunca se puede cambiar.
