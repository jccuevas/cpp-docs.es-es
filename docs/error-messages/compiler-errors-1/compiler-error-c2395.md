---
title: Error del compilador C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: dd3bd922e2bfa61da2da87d368bb4b28237161f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599848"
---
# <a name="compiler-error-c2395"></a>Error del compilador C2395

'your_type::operator'op'': el operador CLR o WinRT no es válido. Al menos un parámetro debe ser de los tipos siguientes: 'T', 'T%', 'T&', 'T^', 'T^%', 'T^&', donde T = 'su_tipo'

Un operador en un tipo administrado o en Windows Runtime no tenía al menos un parámetro con un tipo igual al del valor devuelto del operador.

El ejemplo siguiente genera C2395 y muestra cómo corregirlo:

```
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