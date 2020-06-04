---
title: Error del compilador C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: a7d20a7658a75a492e19b9e81acaa3b6fce5cae7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743944"
---
# <a name="compiler-error-c2460"></a>Error del compilador C2460

' identificador1 ': utiliza ' identificador2 ', que se está definiendo

Una clase o estructura (`identifier2`) se declara como un miembro de sí mismo (`identifier1`). No se permiten definiciones recursivas de clases y estructuras.

En el ejemplo siguiente se genera C2460:

```cpp
// C2460.cpp
class C {
   C aC;    // C2460
};
```

En su lugar, use una referencia de puntero en la clase.

```cpp
// C2460.cpp
class C {
   C * aC;    // OK
};
```
