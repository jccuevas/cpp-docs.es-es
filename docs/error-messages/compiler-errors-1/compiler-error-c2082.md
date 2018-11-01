---
title: Error del compilador C2082
ms.date: 11/04/2016
f1_keywords:
- C2082
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
ms.openlocfilehash: 8bfb54dc91ef9132e3930e2c0799070f80f5cd0f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577260"
---
# <a name="compiler-error-c2082"></a>Error del compilador C2082

Nueva definición del parámetro formal 'identifier'

Un parámetro formal para una función volvió a declararse dentro del cuerpo de función. Para resolver el error, quite la redefinición.

El ejemplo siguiente genera la advertencia C2082:

```
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```