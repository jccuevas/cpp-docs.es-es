---
title: Error del compilador C2600
ms.date: 11/04/2016
f1_keywords:
- C2600
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
ms.openlocfilehash: 4d9e94790c3f4b2fa0aaf36894f0b12c7134a9ed
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62215671"
---
# <a name="compiler-error-c2600"></a>Error del compilador C2600

'función': no se puede definir una función miembro especial generada por el compilador (se debe declarar primero en la clase)

Antes de que se puedan definir funciones miembro, como constructores o destructores, para una clase, se deben declarar en la clase. Si no se declaran en la clase, el compilador puede generar constructores y destructores predeterminados (lo que se conoce como funciones miembro especiales). Sin embargo, si define una de estas funciones sin una declaración coincidente en la clase, el compilador detecta un conflicto.

Para corregir este error, en la declaración de clase, declare cada función miembro que defina fuera de la declaración de clase.

El código siguiente genera el error C2600:

```
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```