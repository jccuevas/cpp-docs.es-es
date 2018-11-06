---
title: Error del compilador C3161
ms.date: 11/04/2016
f1_keywords:
- C3161
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
ms.openlocfilehash: 22ecc176036308699c3ad7bd8c015836be910073
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501665"
---
# <a name="compiler-error-c3161"></a>Error del compilador C3161

'interface': anidamiento de una clase, estructura, unión o interfaz en una interfaz no es válido; anidamiento de una interfaz en una clase, struct o union no es válido

Un [__interface](../../cpp/interface.md) solo puede aparecer en el ámbito global o dentro de un espacio de nombres. Una clase, struct o unión no puede aparecer en una interfaz.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3161.

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```