---
title: Error del compilador C2929
ms.date: 11/04/2016
f1_keywords:
- C2929
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
ms.openlocfilehash: fe2a56f7722c70c11e980fb6ee59230ffd056c5f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658814"
---
# <a name="compiler-error-c2929"></a>Error del compilador C2929

'identifier': creación de instancias explícita; no se puede forzar y suprimir de forma explícita la creación de instancias de miembros de clase de plantilla

No se puede usar con instancias explícitamente un identificador mientras se evita que este se use con instancias.

El ejemplo siguiente genera la advertencia C2929:

```
// C2929.cpp
// compile with: /c
template<typename T>
class A {
public:
   A() {}
};

template A<int>::A();

extern template A<int>::A();   // C2929
```