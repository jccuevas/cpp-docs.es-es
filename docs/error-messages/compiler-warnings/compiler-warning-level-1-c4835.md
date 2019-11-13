---
title: ADVERTENCIA del compilador (nivel 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: e59c8a7c9cdd9b892155a7d8ee8c8259324c2045
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052303"
---
# <a name="compiler-warning-level-1-c4835"></a>ADVERTENCIA del compilador (nivel 1) C4835

' variable ': el inicializador de los datos exportados no se ejecutará hasta que el código administrado se ejecute por primera vez en el ensamblado de host

Al tener acceso a datos entre componentes administrados, se recomienda no utilizar mecanismos de C++ importación y exportación nativos. En su lugar, declare los miembros de datos dentro de un tipo administrado y haga referencia a los metadatos con `#using` en el cliente. Para obtener más información, vea [#using (directiva)](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4835.

```cpp
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa el componente compilado en el ejemplo anterior, que muestra que el valor de las variables no es el esperado.

```cpp
// C4835_b.cpp
// compile with: /clr C4835.lib
#include <stdio.h>
__declspec(dllimport) int m;
__declspec(dllimport) int *p;

int main() {
   printf("%d\n", m);
   printf("%d\n", p);
}
```

```Output
0
268456008
```