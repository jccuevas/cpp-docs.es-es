---
title: Error del compilador C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 417763e8c26918d3cd83702b283244d1c13d9d1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735754"
---
# <a name="compiler-error-c2086"></a>Error del compilador C2086

' Identifier ': nueva definición

El identificador se define más de una vez, o una declaración subsiguiente difiere de la anterior.

C2086 también puede ser el resultado de la compilación incremental de un C# ensamblado al que se hace referencia. Vuelva a C# generar el ensamblado para resolver este error.

En el ejemplo siguiente se genera C2086:

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
