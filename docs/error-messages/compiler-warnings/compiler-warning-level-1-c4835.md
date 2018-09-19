---
title: Compilador advertencia (nivel 1) C4835 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4835
dev_langs:
- C++
helpviewer_keywords:
- C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70492be13d312c5d167990cfa0b6c0d741e1055f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080108"
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