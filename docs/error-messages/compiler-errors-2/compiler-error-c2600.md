---
title: Error del compilador C2600
ms.date: 11/04/2016
f1_keywords:
- C2600
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
ms.openlocfilehash: b2d95460cadf03f9152599ef47ae703030326dd1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740746"
---
# <a name="compiler-error-c2600"></a>Error del compilador C2600

'función': no se puede definir una función miembro especial generada por el compilador (se debe declarar primero en la clase)

Antes de que se puedan definir funciones miembro, como constructores o destructores, para una clase, se deben declarar en la clase. Si no se declaran en la clase, el compilador puede generar constructores y destructores predeterminados (lo que se conoce como funciones miembro especiales). Sin embargo, si define una de estas funciones sin una declaración coincidente en la clase, el compilador detecta un conflicto.

Para corregir este error, en la declaración de clase, declare cada función miembro que defina fuera de la declaración de clase.

El código siguiente genera el error C2600:

```cpp
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```
