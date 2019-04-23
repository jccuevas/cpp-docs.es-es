---
title: Error del compilador C3282
ms.date: 11/04/2016
f1_keywords:
- C3282
helpviewer_keywords:
- C3282
ms.assetid: bac2ac89-c360-4c24-bb81-c20c62ece9ba
ms.openlocfilehash: 46be1f5250c1ca787909c48646d59180d62bd899
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778103"
---
# <a name="compiler-error-c3282"></a>Error del compilador C3282

parámetro genérico listas solo pueden aparecer en managed o WinRTclasses, structs o funciones

Se ha utilizado incorrectamente una lista de parámetros genéricos.  Para más información, vea [Genéricos](../../extensions/generics-cpp-component-extensions.md).

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