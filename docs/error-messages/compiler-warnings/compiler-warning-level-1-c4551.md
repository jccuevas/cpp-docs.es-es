---
title: Compilador advertencia (nivel 1) C4551 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4551
dev_langs:
- C++
helpviewer_keywords:
- C4551
ms.assetid: 458b59bd-e2d7-425f-9ba6-268ff200424f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dc8852ccaee1d2b07fbf35e57885b863afef921
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075571"
---
# <a name="compiler-warning-level-1-c4551"></a>Advertencia del compilador (nivel 1) C4551

lista de argumentos de función llamada que faltan

Una llamada de función debe incluir los paréntesis de apertura y cierre después del nombre de función, incluso si la función no toma ningún parámetro.

El ejemplo siguiente genera C4551:

```
// C4551.cpp
// compile with: /W1
void function1() {
}

int main() {
   function1;   // C4551
   function1();   // OK
}
```