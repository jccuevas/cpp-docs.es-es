---
title: Error del compilador C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: 5020732ce5186ee1c6e9d2ea13f452fe9988bdfa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744841"
---
# <a name="compiler-error-c2396"></a>Error del compilador C2396

' your_type:: operator'type ' ': la conversión definida por el usuario CLR o WinRT functionnot es válida. Debe convertir de o convertir a: ' t ^ ', ' t ^% ', ' t ^ & ', donde T = ' your_type '

Una función de conversión en un tipo administrado o de Windows en tiempo de ejecución no tenía al menos un parámetro con un tipo igual al tipo que contiene la función de conversión.

El siguiente ejemplo genera el error C2396 y muestra cómo corregirlo:

```cpp
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```
