---
title: Error del compilador C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 76cc35e57c1577ed23c043740f37c602600da542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748507"
---
# <a name="compiler-error-c2589"></a>Error del compilador C2589

' Identifier ': token no válido en el lado derecho de ':: '

Si un nombre de clase, estructura o unión aparece a la izquierda del operador de resolución de ámbito (dos puntos dobles), el token de la derecha debe ser una clase, una estructura o un miembro de Unión. De lo contrario, cualquier identificador global puede aparecer a la derecha.

No se puede sobrecargar el operador de resolución de ámbito.

En el ejemplo siguiente se genera C2589:

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
