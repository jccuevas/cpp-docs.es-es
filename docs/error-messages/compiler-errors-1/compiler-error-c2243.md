---
title: Error del compilador C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: f5a62b1c12b94735d0383697bf7a92d12d64b21f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757805"
---
# <a name="compiler-error-c2243"></a>Error del compilador C2243

La conversión 'tipo de conversión' de 'tipo1' a 'tipo' existe, pero es inaccesible

La protección de acceso (`protected` o `private`) ha evitado la conversión de un puntero a una clase derivada en un puntero a la clase base.

El siguiente ejemplo genera el error C2243:

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

Las clases base con acceso `protected` o `private` no son accesibles para los clientes de la clase derivada. Estos niveles de control de acceso se utilizan para indicar que la clase base es un detalle de implementación que debería ser invisible para los clientes. Utilice la derivación pública si desea que los clientes de la clase derivada tengan acceso a la conversión implícita de un puntero de clase derivada en un puntero a la clase base.
