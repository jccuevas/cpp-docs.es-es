---
title: Error del compilador C2537
ms.date: 11/04/2016
f1_keywords:
- C2537
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
ms.openlocfilehash: 0dfe9f88fcdfda1325150d480670777a4d42d896
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758637"
---
# <a name="compiler-error-c2537"></a>Error del compilador C2537

' Specifier ': especificación de vinculación no válida

Posibles causas:

1. No se admite el especificador de vinculación. Solo se admite el especificador de vinculación "C".

1. La vinculación "C" se especifica para más de una función en un conjunto de funciones sobrecargadas. Esto no está permitido.

En el ejemplo siguiente se genera C2537:

```cpp
// C2537.cpp
// compile with: /c
extern "c" void func();   // C2537
extern "C" void func2();   // OK
```
