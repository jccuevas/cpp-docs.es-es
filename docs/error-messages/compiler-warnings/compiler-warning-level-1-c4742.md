---
title: Advertencia del compilador (nivel 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 00ac67fec3aafa5a259b5222bd6bb8654210fa61
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436367"
---
# <a name="compiler-warning-level-1-c4742"></a>Advertencia del compilador (nivel 1) C4742

'var' tiene una alineación diferente en 'archivo1' y 'archivo2': número y número

Una variable externa que se hace referencia o definida en dos archivos tiene una alineación diferente en esos archivos. Esta advertencia se genera cuando el compilador encuentra que `__alignof` para la variable en *file1* difiere `__alignof` para la variable en *file2*. Esto puede deberse mediante el uso de tipos no compatibles cuando se declara la variable en distintos archivos, o mediante el uso de no coincidentes `#pragma pack` en distintos archivos.

Para resolver esta advertencia, utilice la misma definición de tipo o use nombres diferentes para las variables.

Para obtener más información, consulte [pack](../../preprocessor/pack.md) y [operador __alignof](../../cpp/alignof-operator.md).

## <a name="example"></a>Ejemplo

Este es el primer archivo que define el tipo.

```
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4742.

```
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```