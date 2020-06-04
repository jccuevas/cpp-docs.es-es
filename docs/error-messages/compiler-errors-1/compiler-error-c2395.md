---
title: Error del compilador C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: 2ac59856770b04dd3c4ea14360e0a83dd99f2150
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744945"
---
# <a name="compiler-error-c2395"></a>Error del compilador C2395

'your_type::operator'op'': el operador CLR o WinRT no es válido. Al menos un parámetro debe ser de los tipos siguientes: ' t ', ' t% ', ' t & ', ' t ^ ', ' t ^% ', ' t ^ & ', donde T = ' your_type '

Un operador en un tipo administrado o en Windows Runtime no tenía al menos un parámetro con un tipo igual al del valor devuelto del operador.

El ejemplo siguiente genera C2395 y muestra cómo corregirlo:

```cpp
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```
