---
title: Error del compilador C2374
ms.date: 11/04/2016
f1_keywords:
- C2374
helpviewer_keywords:
- C2374
ms.assetid: 73b51965-e91c-4e21-9732-f71c1449d22e
ms.openlocfilehash: 7b3dbcd4f19d594082d8b961c8dbc92c393699a0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745543"
---
# <a name="compiler-error-c2374"></a>Error del compilador C2374

'identifier': nueva definición; inicialización múltiple

El identificador se inicializó más de una vez.

El ejemplo siguiente genera la advertencia C2374:

```cpp
// C2374.cpp
// compile with: /c
int i = 0;
int i = 1;   // C2374
int j = 1;   // OK
```
