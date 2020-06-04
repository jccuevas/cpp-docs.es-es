---
title: Advertencia del compilador (nivel 1) C4742
ms.date: 11/04/2016
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: af97c72f496177d2e94cf18f9685ac33c5e62404
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185664"
---
# <a name="compiler-warning-level-1-c4742"></a>Advertencia del compilador (nivel 1) C4742

' var ' tiene una alineación diferente en ' archivo1 ' y ' archivo2 ': número y número

Una variable externa a la que se hace referencia o que se define en dos archivos tiene una alineación diferente en esos archivos. Esta advertencia se genera cuando el compilador encuentra que `__alignof` para la variable en *archivo1* es diferente de `__alignof` para la variable en *archivo2*. Esto puede deberse a un uso de tipos incompatibles al declarar variables en archivos diferentes o a usar `#pragma pack` no coincidentes en archivos diferentes.

Para resolver esta advertencia, use la misma definición de tipo o use nombres diferentes para las variables.

Para obtener más información, vea operador [Pack](../../preprocessor/pack.md) y [__alignof](../../cpp/alignof-operator.md).

## <a name="example"></a>Ejemplo

Este es el primer archivo que define el tipo.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4742.

```c
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
