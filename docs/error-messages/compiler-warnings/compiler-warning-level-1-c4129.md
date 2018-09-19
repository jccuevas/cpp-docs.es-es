---
title: Compilador advertencia (nivel 1) C4129 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4129
dev_langs:
- C++
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e02f38044180c45e221099d2874b7f8ff48d62f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098451"
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