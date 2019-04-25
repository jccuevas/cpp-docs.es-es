---
title: Error del compilador C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: ded5a3d459e4b5d1412998aadbaa385864f505a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388880"
---
# <a name="compiler-error-c2243"></a>Error del compilador C2243

La conversión 'tipo de conversión' de 'tipo1' a 'tipo' existe, pero es inaccesible

La protección de acceso (`protected` o `private`) ha evitado la conversión de un puntero a una clase derivada en un puntero a la clase base.

El siguiente ejemplo genera el error C2243:

```
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