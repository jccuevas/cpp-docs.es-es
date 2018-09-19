---
title: Compilador advertencia (nivel 1) C4742 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4742
dev_langs:
- C++
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 622a1b1cd62024da58191ce1312c391dd39e0d28
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088597"
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