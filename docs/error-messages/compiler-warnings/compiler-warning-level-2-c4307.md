---
title: Advertencia del compilador (nivel 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: e9ad30f60260893130beed921aab811c894868cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402507"
---
# <a name="compiler-warning-level-2-c4307"></a>Advertencia del compilador (nivel 2) C4307

'operador': desbordamiento de constante integral

El operador se usa en una expresión que da como resultado una constante de enteros que desborda el espacio asignado para él. Es posible que deba usar un tipo mayor para la constante. Un **firmado int** contiene un valor menor que un `unsigned int` porque el **firmado int** utiliza un bit para representar el inicio de sesión.

El ejemplo siguiente genera C4307:

```
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```