---
title: Error del compilador C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 6a9568f3c3be88438eae1f28e12dc780301ead0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402585"
---
# <a name="compiler-error-c3389"></a>Error del compilador C3389

> __declspec (*palabra clave*) no se puede usar con/CLR: pure o/CLR: safe

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Un [__declspec](../../cpp/declspec.md) modificador utilizado implica un estado por proceso.  [/ CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md) implica un por [appdomain](../../cpp/appdomain.md) estado.  Por lo tanto, declarar una variable con el `keyword` **__declspec** modificador y compilar con **/CLR: pure** no está permitido.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```