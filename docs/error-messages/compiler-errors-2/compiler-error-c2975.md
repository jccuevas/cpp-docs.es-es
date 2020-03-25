---
title: Error del compilador C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 70fc648de8bcf4f1e85edf3a12cc0b7d3d70625f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201570"
---
# <a name="compiler-error-c2975"></a>Error del compilador C2975

> '*argument*': argumento de plantilla no válido para '*Type*'; se esperaba una expresión constante en tiempo de compilación

El argumento de plantilla no coincide con la declaración de plantilla; una expresión constante debe aparecer dentro de los corchetes angulares. No se permiten variables como argumentos reales de plantilla. Compruebe la definición de plantilla para encontrar los tipos correctos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2975 y también se muestra el uso correcto:

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 también se produce cuando se &#95; &#95;usa&#95; &#95; la línea como una constante de tiempo de compilación con [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md). Una solución sería compilar con [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) en lugar de **/Zi**.

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```
