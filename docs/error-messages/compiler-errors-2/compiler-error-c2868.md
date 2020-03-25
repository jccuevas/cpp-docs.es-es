---
title: Error del compilador C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 0cbcf7dc80aedc554594f88992059f98b7091c21
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201646"
---
# <a name="compiler-error-c2868"></a>Error del compilador C2868

> '*Identifier*': sintaxis no válida para la declaración Using; nombre completo esperado

Una [declaración Using](../../cpp/using-declaration.md) requiere un *nombre completo*, una secuencia separada por el operador de ámbito (`::`) de los nombres de espacio de nombres, clase o enumeración que termina con el nombre del identificador. Se puede usar un solo operador de resolución de ámbito para introducir un nombre del espacio de nombres global.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2868 y también se muestra el uso correcto:

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
