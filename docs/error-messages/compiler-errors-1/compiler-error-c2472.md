---
title: Error del compilador C2472
ms.date: 11/04/2016
f1_keywords:
- C2472
helpviewer_keywords:
- C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
ms.openlocfilehash: d2f104bb61915f8d19d5fff22eea17929c0e8d74
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632744"
---
# <a name="compiler-error-c2472"></a>Error del compilador C2472

> '*función*' no se puede generar en código administrado: '*mensaje*'; compile con /clr para generar una imagen mixta

## <a name="remarks"></a>Comentarios

Este error se producirá cuando se usen tipos no admitidos por código administrado en un entorno puro de Common Language Runtime (CLR). Compile con **/clr** para resolver el error.

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C2472.

```cpp
// C2472.cpp
// compile with: /clr:pure
// C2472 expected

#include <cstdlib>

int main()
{
   int * __ptr32 p32;
   int * __ptr64 p64;

   p32 = (int * __ptr32)malloc(4);
   p64 = p32;
}
```

## <a name="see-also"></a>Vea también

- [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)
