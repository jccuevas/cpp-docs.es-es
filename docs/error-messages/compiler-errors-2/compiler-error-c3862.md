---
title: Error del compilador C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 2ba130862b1debbe2991ca7cbcae50192f900cd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302319"
---
# <a name="compiler-error-c3862"></a>Error del compilador C3862

> '*función*': no se puede compilar una función no administrada con/CLR: pure o/CLR: safe

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

Una compilación con **/CLR: pure** o **/CLR: safe** generará una imagen de MSIL, una imagen sin código nativo (no administrado).  Por lo tanto, no puede usar el `unmanaged` pragma en un **/CLR: pure** o **/CLR: safe** compilación.

Para obtener más información, consulte [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) y [managed, unmanaged](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```