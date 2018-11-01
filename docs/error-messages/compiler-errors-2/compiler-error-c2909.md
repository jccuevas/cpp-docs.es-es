---
title: Error del compilador C2909
ms.date: 11/04/2016
f1_keywords:
- C2909
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
ms.openlocfilehash: 7a777e87d8110ac16740346a8494f9501ce93b37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668850"
---
# <a name="compiler-error-c2909"></a>Error del compilador C2909

'identifier': la creación de instancias explícita de la plantilla de función requiere un tipo de valor devuelto

La creación de instancias explícita de una plantilla de función requiere la especificación explícita de su tipo de valor devuelto. La especificación de tipo de valor devuelto implícita no funciona.

El ejemplo siguiente genera la advertencia C2909:

```
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```