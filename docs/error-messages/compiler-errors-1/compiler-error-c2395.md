---
title: Error del compilador C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: dd3bd922e2bfa61da2da87d368bb4b28237161f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303668"
---
# <a name="compiler-error-c2395"></a>Error del compilador C2395

' your_type '': Operador CLR o WinRT no es válido. Debe ser al menos un parámetro de los siguientes tipos: ' T ', ' t %', ' t &', ' t ^', ' t ^ %', ' t ^ &', donde T = 'su_tipo'

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