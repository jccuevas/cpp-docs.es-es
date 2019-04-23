---
title: _ReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: e5013b20f9e7ed0349d940d9be61cc1b4afc95d4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041142"
---
# <a name="returnaddress"></a>_ReturnAddress

## <a name="microsoft-specific"></a>Específicos de Microsoft

El `_ReturnAddress` intrínseco proporciona la dirección de la instrucción en la función de llamada que se va a ejecutar después de que el control vuelve al llamador.

Cree el siguiente programa y paso a través de él en el depurador. Paso a paso a través del programa, tenga en cuenta la dirección que se devuelve desde `_ReturnAddress`. A continuación, inmediatamente después de volver de la función donde `_ReturnAddress` se ha usado, abra el [Cómo: Utilice la ventana Desensamblado](/visualstudio/debugger/how-to-use-the-disassembly-window) y tenga en cuenta que la dirección de la siguiente instrucción que se ejecutará coincide con la dirección devuelta de `_ReturnAddress`.

Optimizaciones, como la inclusión entre líneas puede afectar a la dirección de retorno. Por ejemplo, si el programa de ejemplo siguiente se compila con [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` se inserten en la función de llamada, `main`. Por lo tanto, las llamadas a `_ReturnAddress` desde `inline_func` y `main` cada uno, se producirá el mismo valor.

Cuando `_ReturnAddress` se utiliza en un programa compilado con [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la función que contiene el `_ReturnAddress` llamada se compilarán como una función nativa. Cuando se compila una función como administrado llama a la función que contiene `_ReturnAddress`, `_ReturnAddress` pueden no comportarse según lo previsto.

## <a name="requirements"></a>Requisitos

**Archivo de encabezado** \<intrin.h >

## <a name="example"></a>Ejemplo

```
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

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)