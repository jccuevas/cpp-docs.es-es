---
title: ADVERTENCIA del compilador (nivel 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 4e95f8deeb61c5a4d56e0643beb6a746f848e33e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164734"
---
# <a name="compiler-warning-level-1-c4005"></a>ADVERTENCIA del compilador (nivel 1) C4005

' Identifier ': nueva definición de macro

El identificador de macro se define dos veces. El compilador usa la segunda definición de macro.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Definir una macro en la línea de comandos y en el código con una directiva de `#define`.

1. Macros importadas de archivos de inclusión.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. Quite una de las definiciones.

1. Use una directiva de [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) antes de la segunda definición.

En el ejemplo siguiente se genera C4005:

```cpp
// C4005.cpp
// compile with: /W1 /EHsc
#include <iostream>
using namespace std;

#define TEST "test1"
#define TEST "test2"   // C4005 delete or rename to resolve the warning

int main() {
   cout << TEST << endl;
}
```
