---
title: Error del compilador C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 093a5856fdcfa6311fcef93214672b035c91b4fc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746531"
---
# <a name="compiler-error-c2513"></a>Error del compilador C2513

' type ': no hay ninguna variable declarada antes de ' = '

El especificador de tipo aparece en la declaración sin ningún identificador de variable.

En el ejemplo siguiente se genera C2513:

```cpp
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Este error también se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: ya no se permite la inicialización de una definición de tipo. El estándar no permite la inicialización de una definición de tipo y ahora genera un error del compilador.

```cpp
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Una alternativa sería eliminar `typedef` para definir una variable con la lista de inicializadores agregada, pero esto no es recomendable porque creará una variable con el mismo nombre que el tipo y ocultará el nombre de tipo.
