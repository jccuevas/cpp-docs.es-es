---
title: _ReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: 2a830ff1e8a2c9551dec52cf10a3d5cf126bde3b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218057"
---
# <a name="_returnaddress"></a>_ReturnAddress

**Específicos de Microsoft**

El `_ReturnAddress` intrínseco proporciona la dirección de la instrucción de la función de llamada que se ejecutará después de que el control vuelva al autor de la llamada.

Compile el programa siguiente y recorra el código en el depurador. A medida que recorre el programa, tenga en cuenta la dirección que `_ReturnAddress`se devuelve de. Después, inmediatamente después de volver de la función `_ReturnAddress` en la que se usó [, abra el procedimiento: Utilice la ventana](/visualstudio/debugger/how-to-use-the-disassembly-window) desensamblado y observe que la dirección de la siguiente instrucción que se va a ejecutar coincide con `_ReturnAddress`la dirección devuelta por.

Las optimizaciones como la inclusión pueden afectar a la dirección de devolución. Por ejemplo, si el programa de ejemplo siguiente se compila con [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` se insertará en la función de llamada, `main`. Por lo tanto, las `_ReturnAddress` llamadas `inline_func` a `main` desde y producirán el mismo valor.

Cuando `_ReturnAddress` se usa en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la función que contiene `_ReturnAddress` la llamada se compilará como una función nativa. Cuando una función compilada como llamadas administradas en `_ReturnAddress`la `_ReturnAddress` función que contiene, puede no tener el comportamiento esperado.

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<INTRIN. h >

## <a name="example"></a>Ejemplo

```cpp
// compiler_intrinsics__ReturnAddress.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_ReturnAddress)

__declspec(noinline)
void noinline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

__forceinline
void inline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

int main(void)
{
   noinline_func();
   inline_func();
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());

   return 0;
}
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)\
[Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md)\
[Palabras clave](../cpp/keywords-cpp.md)
