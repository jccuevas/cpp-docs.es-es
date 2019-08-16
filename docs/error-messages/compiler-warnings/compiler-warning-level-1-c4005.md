---
title: Compilador advertencia (nivel 1) C4005
ms.date: 11/04/2016
f1_keywords:
- C4005
helpviewer_keywords:
- C4005
ms.assetid: 7f2dc79a-9fcb-4d5b-be61-120d9cb487ad
ms.openlocfilehash: 76aab2160bd5f7918771dcf63b7297a869da751e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187344"
---
# <a name="compiler-warning-level-1-c4005"></a>Compilador advertencia (nivel 1) C4005

'identifier': redefinición de macro

El identificador de la macro se define dos veces. El compilador usa la segunda definición de macro.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Definir una macro en la línea de comandos y en el código con un `#define` directiva.

1. Macros importadas desde los archivos de inclusión.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. Quite una de las definiciones.

1. Use un [#undef](../../preprocessor/hash-undef-directive-c-cpp.md) la directiva antes de la segunda definición.

El ejemplo siguiente genera C4005:

```
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