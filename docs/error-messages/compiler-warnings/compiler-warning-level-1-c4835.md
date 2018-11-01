---
title: Advertencia del compilador (nivel 1) C4835
ms.date: 11/04/2016
f1_keywords:
- C4835
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
ms.openlocfilehash: 0427a97a9e368a19a40a8d1a552f7713e36f831e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516316"
---
# <a name="compiler-warning-level-1-c4835"></a>Advertencia del compilador (nivel 1) C4835

'variable': el inicializador para los datos exportados no se ejecutará hasta que el código administrado se ejecuta en primer lugar en el ensamblado de host

Al obtener acceso a datos entre componentes administrados, se recomienda no usar la importación de C++ nativo y mecanismos de exportación. En su lugar, declarar sus miembros de datos dentro de un tipo administrado y hacer referencia a los metadatos con `#using` en el cliente. Para obtener más información, vea [#using (directiva)](../../preprocessor/hash-using-directive-cpp.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4835.

```
// C4835.cpp
// compile with: /W1 /clr /LD
int f() { return 1; }
int n = 9;

__declspec(dllexport) int m = f();   // C4835
__declspec(dllexport) int *p = &n;   // C4835
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente utiliza el componente que se compila en el ejemplo anterior, que muestra que el valor de las variables no según lo previsto.

```
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