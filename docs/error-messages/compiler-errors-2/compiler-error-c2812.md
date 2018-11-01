---
title: Error del compilador C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: 88b071f38cf41db9c929d25ffd526b3f2b7ca468
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531825"
---
# <a name="compiler-error-c2812"></a>Error del compilador C2812

> \#no se admite la importación con/CLR: pure y/CLR: safe

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

[directiva #import](../../preprocessor/hash-import-directive-cpp.md) no es compatible con **/CLR: pure** y **/CLR: safe** porque `#import` requiere el uso de bibliotecas de compatibilidad de compilador nativo.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```