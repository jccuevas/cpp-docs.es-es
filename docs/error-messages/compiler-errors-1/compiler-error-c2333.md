---
title: Error del compilador C2333
ms.date: 11/04/2016
f1_keywords:
- C2333
helpviewer_keywords:
- C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
ms.openlocfilehash: cca7f0d3bd75cca8fdd621fb425dec42e6560f4e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747753"
---
# <a name="compiler-error-c2333"></a>Error del compilador C2333

' función ': error en la declaración de función; omitiendo el cuerpo de la función

Este error se produce después de otro error, para las funciones miembro definidas dentro de su clase.

En el ejemplo siguiente se genera C2333:

```cpp
// C2333.cpp
struct s1 {
   s1(s1) {}   // C2333
};
```
