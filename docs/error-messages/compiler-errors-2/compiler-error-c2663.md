---
title: Error del compilador C2663 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fed35dcce056eb3d2a660c154e94b8058563dba7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083696"
---
# <a name="compiler-error-c2663"></a>Error del compilador C2663

'function': número sobrecargas no tienen ninguna conversión válida para el puntero 'this'

No se pudo convertir el compilador `this` a cualquiera de las versiones sobrecargadas de la función miembro.

Este error puede deberse a invocar no`const` función miembro en un `const` objeto.  Soluciones posibles:

1. Quitar el `const` de la declaración del objeto.

1. Agregar `const` a una de las sobrecargas de función miembro.

El ejemplo siguiente genera C2663:

```
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```