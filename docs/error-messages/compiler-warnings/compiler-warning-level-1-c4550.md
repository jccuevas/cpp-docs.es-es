---
title: ADVERTENCIA del compilador (nivel 1) C4550
ms.date: 11/04/2016
f1_keywords:
- C4550
helpviewer_keywords:
- C4550
ms.assetid: f902b4ed-5f17-48ea-b693-92f4fb8c8054
ms.openlocfilehash: 1c310855ee3925374de8b736cde9013d48df6482
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966374"
---
# <a name="compiler-warning-level-1-c4550"></a>ADVERTENCIA del compilador (nivel 1) C4550

la expresión se evalúa como una función a la que le falta una lista de argumentos

Falta una lista de argumentos en un puntero desreferenciado a una función.

## <a name="example"></a>Ejemplo

```cpp
// C4550.cpp
// compile with: /W1
bool f()
{
   return true;
}

typedef bool (*pf_t)();

int main()
{
   pf_t pf = f;
   if (*pf) {}  // C4550
   return 0;
}
```