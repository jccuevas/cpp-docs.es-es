---
title: Error del compilador C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: c73a8d4fcde945ddf2495cc2d0d7dc47216f2db3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166339"
---
# <a name="compiler-error-c2434"></a>Error del compilador C2434

> '*símbolo*': un símbolo declarado con __declspec (proceso) no se puede inicializar dinámicamente en/CLR: modo puro

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

No es posible inicializar dinámicamente una variable por proceso bajo **/CLR: pure**. Para obtener más información, consulte [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) y [proceso](../../cpp/process.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2434. Para corregir este problema, utilice las constantes para inicializar `process` variables.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```