---
title: Error del compilador C2441
ms.date: 11/04/2016
f1_keywords:
- C2441
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
ms.openlocfilehash: 7fcf333f62253eb676c0f0ada1c927ab962ae1ca
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338927"
---
# <a name="compiler-error-c2441"></a>Error del compilador C2441

> '*variable*': un símbolo declarado con __declspec (proceso) debe ser constante en/CLR: modo puro

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

De forma predeterminada, las variables son por dominio de aplicación bajo **/CLR: pure**. Marcado de una variable `__declspec(process)` en **/CLR: pure** propenso a errores si se modifica en un dominio de aplicación y leer en otro.

Por lo tanto, el compilador exige por proceso de ser variables `const` en **/CLR: pure**, realizar ellos leer sólo en todos los dominios de aplicación.

Para obtener más información, consulte [proceso](../../cpp/process.md) y [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```