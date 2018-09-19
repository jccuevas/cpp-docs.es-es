---
title: Error del compilador C2561 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2561
dev_langs:
- C++
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8611af23ab884a853fc751ae82c636753993495b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070709"
---
# <a name="compiler-error-c2561"></a>Error del compilador C2561

'identifier': función debe devolver un valor

La función se declaró que devuelva un valor, pero la definición de función no contiene un `return` instrucción.

Este error puede deberse a un prototipo de función incorrecto:

1. Si la función no devuelve un valor, declare la función con el tipo de valor devuelto [void](../../cpp/void-cpp.md).

1. Compruebe que todas las ramas posibles de la función devuelven un valor del tipo declarado en el prototipo.

1. Las funciones de C++ que contiene rutinas de ensamblado en línea que almacenan el valor devuelto en el `AX` register que necesite una instrucción return. Copie el valor en `AX` a una variable temporal y devolver esa variable de la función.

El ejemplo siguiente genera C2561:

```
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```