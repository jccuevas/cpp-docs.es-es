---
title: Compilador advertencia (nivel 4) C4459 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4459
dev_langs:
- C++
helpviewer_keywords:
- C4459
ms.assetid: ee9f6287-9c70-4b10-82a0-add82a13997f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0fc86be746bafdf4987a7492c59d9686535cef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040900"
---
# <a name="compiler-warning-level-4-c4459"></a>Compilador advertencia (nivel 4) C4459

> declaración de '*identificador*' oculta la declaración global

La declaración de *identificador* en el ámbito local oculta la declaración de idéntico nombre *identificador* en el ámbito global. Esta advertencia le permite saber que las referencias a *identificador* en este ámbito, resolver la versión declarada localmente, no la versión global, que puede ser o no su intención. Por lo general, se recomienda que minimizar el uso de variables globales como una buena práctica de ingeniería. Para minimizar la contaminación del espacio de nombres global, se recomienda el uso de un espacio de nombres de variables globales.

Esta advertencia era nueva en Visual Studio 2015, en Visual C++ versión del compilador 18.00. Para suprimir las advertencias de esa versión del compilador o posterior al migrar el código, utilice el [/wv: 18](../../build/reference/compiler-option-warning-level.md) opción del compilador.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4459:

```cpp
// C4459_hide.cpp
// compile with: cl /W4 /EHsc C4459_hide.cpp
int global_or_local = 1;

int main() {
    int global_or_local; // warning C4459
    global_or_local = 2;
}
```

Una manera de corregir este problema es crear un espacio de nombres para las campos globales, pero no use un `using` nombres completos de directiva para poner ese espacio de nombres en el ámbito, por lo que todas las referencias deben usar el ambiguo:

```cpp
// C4459_namespace.cpp
// compile with: cl /W4 /EHsc C4459_namespace.cpp
namespace globals {
    int global_or_local = 1;
}

int main() {
    int global_or_local; // OK
    global_or_local = 2;
    globals::global_or_local = 3;
}
```
