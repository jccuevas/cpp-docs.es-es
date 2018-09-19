---
title: Compilador advertencia (nivel 2) C4307 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4307
dev_langs:
- C++
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed18c213b35e79aaae98efa5932ac404a8d84bff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079198"
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