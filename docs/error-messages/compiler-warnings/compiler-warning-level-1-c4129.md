---
title: Compilador advertencia (nivel 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: dc4f4c4c1feeba543ce0baa71e1ee5dfd81fdcae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310961"
---
# <a name="compiler-warning-level-1-c4129"></a>Compilador advertencia (nivel 1) C4129

'carácter': secuencia de escape de carácter no reconocida

El `character` sigue una barra diagonal inversa (\\) en un carácter o cadena de constante no se reconoce como una secuencia de escape válida. La barra diagonal inversa se omite y no se imprimen. El carácter que sigue a la barra diagonal inversa se imprime.

Para imprimir una sola barra diagonal inversa, especifique una doble barra diagonal inversa (\\\\).

El estándar de C++, en la sección 2.13.2 describe las secuencias de escape.

El ejemplo siguiente genera C4129:

```
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```