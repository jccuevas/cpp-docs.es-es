---
title: Error del compilador C3282
ms.date: 11/04/2016
f1_keywords:
- C3282
helpviewer_keywords:
- C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
ms.openlocfilehash: 7092ddc3bf6859212cbb143572de1ef3604a13d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491512"
---
# <a name="compiler-error-c3282"></a>Error del compilador C3282

parámetro genérico listas solo pueden aparecer en managed o WinRTclasses, structs o funciones

Se ha utilizado incorrectamente una lista de parámetros genéricos.  Para más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se genera el error C3282 y se muestra cómo corregirlo.

```
// C3282.cpp
// compile with: /clr /c
generic <typename T> int x;   // C3282

ref struct GC0 {
   generic <typename T> int x;   // C3282
};

// OK
generic <typename T>
ref class M {};
```