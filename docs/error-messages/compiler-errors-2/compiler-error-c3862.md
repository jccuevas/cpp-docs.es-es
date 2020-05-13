---
title: Error del compilador C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 0b9c1e1213949d7d700094caa6687232df881ce6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165488"
---
# <a name="compiler-error-c3862"></a>Error del compilador C3862

> '*función*': no se puede compilar una función no administrada con/CLR: Pure o/CLR: Safe

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

Una compilación con **/clr: Pure** o **/clr: Safe** producirá una imagen de solo MSIL, una imagen sin código nativo (no administrado).  Por lo tanto, no se puede utilizar el pragma `unmanaged` en una compilación **/clr: Pure** o **/clr: Safe** .

Para obtener más información, vea [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) y [Managed, Unmanaged](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```
