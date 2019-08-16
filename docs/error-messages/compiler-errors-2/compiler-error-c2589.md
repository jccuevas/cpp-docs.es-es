---
title: Error del compilador C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 18d8f7130c34f5e1e33bc7aa9b9463f50c243045
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386946"
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