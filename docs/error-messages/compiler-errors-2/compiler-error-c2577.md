---
title: Error del compilador C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 4406aa90b26bc517308132ae9cccd003d44a9aad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530551"
---
# <a name="compiler-error-c2577"></a>Error del compilador C2577

'member': un destructor/finalizador no puede tener un tipo de valor devuelto

Un destructor o finalizador no puede devolver un valor de `void` o cualquier otro tipo. Quitar el `return` instrucción de la definición del destructor.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2577.

```
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```