---
title: Error del compilador C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: cec92982646c64e6c5b669df328e4836d4f44df8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202110"
---
# <a name="compiler-error-c2812"></a>Error del compilador C2812

> \#Import no se admite con/CLR: Pure y/CLR: Safe

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

[la directiva #import](../../preprocessor/hash-import-directive-cpp.md) no se admite con **/clr: Pure** y **/clr: Safe** porque `#import` requiere el uso de bibliotecas nativas de compatibilidad del compilador.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```
