---
title: Error del compilador C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: 9c9772052b690ad87de1d408c06478d82d48e724
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464810"
---
# <a name="compiler-error-c2652"></a>Error del compilador C2652

'identifier': constructor de copias no válido: primer parámetro no debe ser un 'identifier'

El primer parámetro del constructor de copias tiene el mismo tipo que la clase, estructura o unión para el que está definido. El primer parámetro puede ser una referencia al tipo, pero no el propio tipo.

El ejemplo siguiente genera C2651:

```
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```