---
title: Error del compilador C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: 414b6e53cf1610a55db984a1127bfc884102494f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230326"
---
# <a name="compiler-error-c2460"></a>Error del compilador C2460

'identificador1': utiliza 'identificador2', que se está definiendo

Una clase o estructura (`identifier2`) se declara como un miembro de sí mismo (`identifier1`). No se permiten definiciones recursivas de clases y estructuras.

El ejemplo siguiente genera C2460:

```
// C2460.cpp
class C {
   C aC;    // C2460
};
```

En su lugar, use una referencia de puntero en la clase.

```
// C2460.cpp
class C {
   C * aC;    // OK
};
```