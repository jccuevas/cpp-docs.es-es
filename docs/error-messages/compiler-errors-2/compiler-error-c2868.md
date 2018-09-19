---
title: Error del compilador C2868 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2868
dev_langs:
- C++
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2de22b34f9dc564ef89d7776af86718af70d51eb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037871"
---
# <a name="compiler-error-c2868"></a>Error del compilador C2868

> '*identificador*': sintaxis no válida para la declaración using; esperado nombre completo

Un [mediante declaración](../../cpp/using-declaration.md) requiere un *nombre completo*, un operador de ámbito (`::`) separados por la secuencia de nombres de espacio de nombres, clase o enumeración que termina con el nombre del identificador. Un operador de resolución de ámbito solo puede utilizarse para introducir un nombre de espacio de nombres global.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2868 y también muestra el uso correcto:

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```