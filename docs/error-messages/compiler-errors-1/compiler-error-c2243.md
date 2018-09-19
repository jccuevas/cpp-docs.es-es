---
title: Error del compilador C2243 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2243
dev_langs:
- C++
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef5d3a6c20ff147ac2a4b765c7779cec9f19627e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102234"
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