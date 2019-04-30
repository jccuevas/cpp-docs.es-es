---
title: Error del compilador C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: d320f78937fc60910bbed4a5b1b89841ea674fb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303520"
---
# <a name="compiler-error-c2396"></a>Error del compilador C2396

' your_type '': CLR o WinRT conversión definida por el usuario functionnot válido. Debe convertir de o convertir en: ' T ^', ' t ^ %', ' t ^ &', donde T = 'su_tipo'

Una función de conversión en un tipo administrado o de Windows en tiempo de ejecución no tenía al menos un parámetro con un tipo igual al tipo que contiene la función de conversión.

El siguiente ejemplo genera el error C2396 y muestra cómo corregirlo:

```
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