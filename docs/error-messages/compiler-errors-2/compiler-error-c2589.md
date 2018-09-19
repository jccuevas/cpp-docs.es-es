---
title: Error del compilador C2589 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2db5dde898a3e5918eed62b2b32231b5d7ed014f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046061"
---
# <a name="compiler-error-c2589"></a>Error del compilador C2589

'identifier': símbolo (token) en el lado derecho de '::'

Si una clase, estructura o unión nombre aparece a la izquierda del operador de resolución de ámbito (dos puntos dobles), el token de la derecha debe ser una clase, estructura o miembro de unión. En caso contrario, puede aparecer cualquier identificador global de la derecha.

No se puede sobrecargar el operador de resolución de ámbito.

El ejemplo siguiente genera C2589:

```
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```