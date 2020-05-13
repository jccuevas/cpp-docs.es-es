---
title: ADVERTENCIA del compilador (nivel 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: 1a48fc806f3274a59c99be25ac7a0e7b03a0454b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176226"
---
# <a name="compiler-warning-level-1-c4129"></a>ADVERTENCIA del compilador (nivel 1) C4129

' carácter ': secuencia de escape de carácter no reconocida

La `character` siguiente a una barra diagonal inversa (\\) en un carácter o una constante de cadena no se reconoce como una secuencia de escape válida. La barra diagonal inversa se omite y no se imprime. Se imprime el carácter que sigue a la barra diagonal inversa.

Para imprimir una sola barra diagonal inversa, especifique una doble barra diagonal inversa (\\\\).

El C++ estándar, en la sección 2.13.2, describe las secuencias de escape.

En el ejemplo siguiente se genera C4129:

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```
