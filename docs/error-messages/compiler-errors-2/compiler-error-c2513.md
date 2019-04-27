---
title: Error del compilador C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 13840246a5dc6a1c1bdbcb55dc47f212ee353d81
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165221"
---
# <a name="compiler-error-c2513"></a>Error del compilador C2513

'type': ninguna variable declarada antes de '='

El especificador de tipo aparece en la declaración de variable sin un identificador.

El ejemplo siguiente genera C2513:

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Este error también puede generarse como resultado de un trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: inicialización de una definición de tipo ya no se permite. La inicialización de una definición de tipo no está permitida por el estándar y genera ahora un error del compilador.

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Una alternativa sería eliminar `typedef` definir una variable con la lista de inicializadores agregado, pero esto no se recomienda porque creará una variable con el mismo nombre que el tipo y ocultar el nombre de tipo.