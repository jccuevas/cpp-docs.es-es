---
title: noinline
ms.date: 11/04/2016
f1_keywords:
- noinline_cpp
helpviewer_keywords:
- noinline __declspec keyword
- __declspec keyword [C++], noinline
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
ms.openlocfilehash: 3a8dce21aa707a1a52c647c9efee5ab806511ca8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454566"
---
# <a name="noinline"></a>noinline

## <a name="microsoft-specific"></a>Específicos de Microsoft

**__declspec (noinline)** indica al compilador nunca inserte una función miembro determinada (función de una clase).

Puede merecer la pena no alinear una función si es pequeña y no es crítica para el rendimiento del código. Es decir, si la función es pequeña y no se la llamará a menudo, por ejemplo, una función que controla una condición de error.

Tenga en cuenta que si una función está marcada como **noinline**, la función de llamada será más pequeña y por lo tanto, sí misma un candidato para la alineación del compilador.

```cpp
class X {
   __declspec(noinline) int mbrfunc() {
      return 0;
   }   // will not inline
};
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[__declspec](../cpp/declspec.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)

