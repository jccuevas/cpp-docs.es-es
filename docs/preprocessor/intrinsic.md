---
title: función intrínseca | Documentos de Microsoft
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
dev_langs:
- C++
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e908a07253e924fa3cfc0a11cdef57a9253eee00
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="intrinsic"></a>intrinsic

Especifica que las llamadas a funciones incluidas en la lista de argumentos de pragma sean intrínsecas.

## <a name="syntax"></a>Sintaxis

```cpp
#pragma intrinsic( function1 [, function2, ...] )
```

## <a name="remarks"></a>Comentarios

El **intrínseco** pragma indica al compilador que una función tiene un comportamiento conocido.  El compilador puede llamar a la función y no reemplazar la llamada a función con instrucciones alineadas si ello mejora el rendimiento.

A continuación se enumeran las funciones de biblioteca con formas intrínsecas. Una vez un **intrínseco** Vea directiva pragma, ya que surte efecto en la primera definición de función que contiene una función intrínseca especificada. El efecto continúa hasta el final del archivo de origen o a la apariencia de un **función** pragma especificando la misma función intrínseca. El **intrínseco** pragma puede utilizarse solo fuera de una definición de función, en el nivel global.

Las siguientes funciones tienen formas intrínsecas y las formas intrínsecas se utilizan cuando se especifica [/Oi](../build/reference/oi-generate-intrinsic-functions.md):

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

Los programas que usan funciones intrínsecas son más rápidos, porque carecen de la sobrecarga de las llamadas a función, pero pueden tener un mayor tamaño debido al código adicional que se genera.

**x86 específico**

El **formas intrínsecas _disable** y **_Habilitar** intrínsecos generar instrucciones en modo kernel para deshabilitar/Habilitar interrupciones y podrían ser útiles en los controladores en modo kernel.

### <a name="example"></a>Ejemplo

Compile el código siguiente en la línea de comandos con "cl -c -FAs sample.c" y consulte sample.asm para comprobar la conversión a instrucciones x86 CLI y STI:

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

**X86 fin de específicos**

Las funciones de punto flotante enumeradas a continuación no tienen formas intrínsecas auténticas. Tienen versiones que pasan argumentos directamente al chip de punto flotante en lugar de insertarlos en la pila del programa:

|||||
|-|-|-|-|
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

 Las funciones de punto flotante enumeradas a continuación tienen formas intrínsecas auténticas cuando se especifica [/Oi](../build/reference/oi-generate-intrinsic-functions.md), [/Og](../build/reference/og-global-optimizations.md), y [/fp: Fast](../build/reference/fp-specify-floating-point-behavior.md) (o cualquier otra opción que incluya/Og: [/ Ox](../build/reference/ox-full-optimization.md), [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)y/O2):

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

Puede usar [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md) o [/Za](../build/reference/za-ze-disable-language-extensions.md) para reemplazar la generación de opciones verdaderas intrínsecas de punto flotante. En este caso, las funciones se generan como rutinas de biblioteca que pasan los argumentos directamente al chip de punto flotante, en lugar de insertarlos en la pila del programa.

Vea [función #pragma](../preprocessor/function-c-cpp.md) para obtener información y un ejemplo sobre cómo habilitar/deshabilitar formas intrínsecas para un bloque de texto de origen.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)<br/>
