---
title: Constantes de tipo de datos | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- FLT_MIN
- SHRT_MAX
- CHAR_MIN
- MB_LEN_MAX
- DBL_EPSILON
- SHRT_MIN
- _FLT_RADIX
- FLT_DIG
- FLT_MAX_10_EXP
- FLT_MANT_DIG
- DBL_MAX_EXP
- SCHAR_MIN
- SCHAR_MAX
- DBL_MIN
- FLT_MIN_10_EXP
- _DBL_ROUNDS
- USHRT_MAX
- FLT_MAX_EXP
- LONG_MAX
- DBL_MAX
- DBL_DIG
- FLT_MIN_EXP
- INT_MIN
- DBL_MIN_10_EXP
- CHAR_BIT
- INT_MAX
- ULONG_MAX
- DBL_MIN_EXP
- LONG_MIN
- _FLT_ROUNDS
- DBL_MANT_DIG
- _DBL_RADIX
- CHAR_MAX
- FLT_MAX
- DBL_MAX_10_EXP
- UCHAR_MAX
- FLT_EPSILON
- UINT_MAX
- LLONG_MIN
- LLONG_MAX
- ULLONG_MAX
- _I8_MIN
- _I8_MAX
- _UI8_MAX
- _I16_MIN
- _I16_MAX
- _UI16_MAX
- _I32_MIN
- _I32_MAX
- _UI32_MAX
- _I64_MIN
- _I64_MAX
- _UI64_MAX
- _I128_MIN
- _I128_MAX
- _UI128_MAX
- SIZE_MAX
- RSIZE_MAX
- LDBL_DIG
- LDBL_EPSILON
- LDBL_HAS_SUBNORM
- LDBL_MANT_DIG
- LDBL_MAX
- LDBL_MAX_10_EXP
- LDBL_MAX_EXP
- LDBL_MIN
- LDBL_MIN_10_EXP
- LDBL_MIN_EXP
- _LDBL_RADIX
- LDBL_TRUE_MIN
- DECIMAL_DIG
dev_langs:
- C++
helpviewer_keywords:
- DBL_MAX_EXP constant
- _DBL_RADIX constant
- FLT_MIN_EXP constant
- DBL_EPSILON constant
- INT_MIN constant
- FLT_EPSILON constant
- DBL_MANT_DIG constant
- _FLT_RADIX constant
- DBL_MIN constant
- USHRT_MAX constant
- FLT_MAX_10_EXP constant
- _FLT_ROUNDS constant
- data type constants [C++]
- _DBL_ROUNDS constant
- CHAR_MAX constant
- FLT_MAX_EXP constant
- FLT_MIN constant
- CHAR_MIN constant
- FLT_MIN_10_EXP constant
- DBL_MIN_EXP constant
- SCHAR_MAX constant
- FLT_RADIX constant
- CHAR_BIT constant
- UCHAR_MAX constant
- DBL_RADIX constant
- FLT_ROUNDS constant
- LONG_MIN constant
- SHRT_MAX constant
- LONG_MAX constant
- DBL_MAX_10_EXP constant
- DBL_MIN_10_EXP constant
- INT_MAX constant
- constants [C++], data type
- ULONG_MAX constant
- FLT_DIG constant
- MB_LEN_MAX constant
- DBL_DIG constant
- SHRT_MIN constant
- DBL_MAX constant
- DBL_ROUNDS constant
- FLT_MAX constant
- UINT_MAX constant
- FLT_MANT_DIG constant
- SCHAR_MIN constant
- LLONG_MIN constant
- LLONG_MAX constant
- ULLONG_MAX constant
- _I8_MIN constant
- _I8_MAX constant
- _UI8_MAX constant
- _I16_MIN constant
- _I16_MAX constant
- _UI16_MAX constant
- _I32_MIN constant
- _I32_MAX constant
- _UI32_MAX constant
- _I64_MIN constant
- _I64_MAX constant
- _UI64_MAX constant
- _I128_MIN constant
- _I128_MAX constant
- _UI128_MAX constant
- SIZE_MAX constant
- RSIZE_MAX constant
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef742989b4af7a3698f6047098110ee58e29bf4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035674"
---
# <a name="data-type-constants"></a>Constantes de tipo de datos

Las constantes de tipo de datos son intervalos de valores dependientes de la implementación permitidos para los tipos de datos enteros y de punto flotante.

## <a name="integral-type-constants"></a>Constantes de tipo de datos entero

Estas constantes proporcionan los rangos de los tipos de datos enteros. Para usarlas, debe incluir el encabezado limits.h en el archivo de origen:

```C
#include <limits.h>
```

> [!NOTE]
> La opción del compilador [/J](../build/reference/j-default-char-type-is-unsigned.md) cambia el tipo **char** predeterminado a **unsigned**.

|Constante|Valor|Descripción|
|--------------|-----------|-------------|
|**CHAR_BIT**|8|Número de bits en un tipo **char**|
|**SCHAR_MIN**|(-128)|Valor mínimo de **signed char**|
|**SCHAR_MAX**|127|Valor máximo de **signed char**|
|**UCHAR_MAX**|255 (0xff)|Valor máximo de **unsigned** **char**|
|**CHAR_MIN**|(-128) (0 si se usa la opción **/J**)|Valor mínimo de **char**|
|**CHAR_MAX**|127 (255 si se usa la opción **/J**)|Valor máximo de **char**|
|**MB_LEN_MAX**|5|Máximo número de bytes en un multibyte **char**|
|**SHRT_MIN**|-32768|Valor mínimo de **signed short**|
|**SHRT_MAX**|32767|Valor máximo de **signed short**|
|**USHRT_MAX**|65535 (0xffff)|Valor máximo de **unsigned** **short**|
|**INT_MIN**|(-2147483647 - 1)|Valor mínimo de **signed int**|
|**INT_MAX**|2147483647|Valor máximo de **signed int**|
|**UINT_MAX**|4294967295 (0xffffffff)|Valor mínimo de **unsigned** **int**|
|**LONG_MIN**|(-2147483647L - 1)|Valor mínimo de **signed long**|
|**LONG_MAX**|2147483647L|Valor máximo de **signed long**|
|**ULONG_MAX**|4294967295UL (0xfffffffful)|Valor máximo de **unsigned** **long**|
|**LLONG_MIN**|(-9223372036854775807LL - 1)|Valor mínimo de **signed long** **long** o **__int64**|
|**LLONG_MAX**|9223372036854775807LL|Valor máximo de **signed long** **long** o **__int64**|
|**ULLONG_MAX**|0xffffffffffffffffull|Valor máximo de **unsigned** **long** **long**|
|**_I8_MIN**|(-127i8 - 1)|Valor mínimo de 8 bits con signo|
|**_I8_MAX**|127i8|Valor máximo de 8 bits con signo|
|**_UI8_MAX**|0xffui8|Valor máximo de 8 bits sin signo|
|**_I16_MIN**|(-32767i16 - 1)|Valor mínimo de 16 bits con signo|
|**_I16_MAX**|32767i16|Valor máximo de 16 bits con signo|
|**_UI16_MAX**|0xffffui16|Valor máximo de 16 bits sin signo|
|**_I32_MIN**|(-2147483647i32 - 1)|Valor mínimo de 32 bits con signo|
|**_I32_MAX**|2147483647i32|Valor máximo de 32 bits con signo|
|**_UI32_MAX**|0xffffffffui32|Valor máximo de 32 bits sin signo|
|**_I64_MIN**|(-9223372036854775807 - 1)|Valor mínimo de 64 bits con signo|
|**_I64_MAX**|9223372036854775807|Valor máximo de 64 bits con signo|
|**_UI64_MAX**|0xffffffffffffffffui64|Valor máximo de 64 bits sin signo|
|**_I128_MIN**|(-170141183460469231731687303715884105727i128 - 1)|Valor mínimo de 128 bits con signo|
|**_I128_MAX**|170141183460469231731687303715884105727i128|Valor máximo de 128 bits con signo|
|**_UI128_MAX**|0xffffffffffffffffffffffffffffffffui128|Valor máximo de 128 bits sin signo|
|**SIZE_MAX**|Igual que **_UI64_MAX** si se define **_WIN64**, o bien **UINT_MAX**|Tamaño máximo de entero nativo|
|**RSIZE_MAX**|Igual que (**SIZE_MAX** >> 1)|Tamaño máximo de biblioteca segura de enteros|

## <a name="floating-point-type-constants"></a>Constantes de tipo de punto flotante

Las siguientes constantes proporcionan el intervalo y otras características de los tipos de datos **long** **double**, **double** y **float**. Para usarlas, debe incluir el encabezado float.h en el archivo de origen:

```C
#include <float.h>
```

|Constante|Valor|Descripción|
|--------------|-----------|-----------------|
|**DBL_DECIMAL_DIG**|17|Número de dígitos decimales de precisión de redondeo|
|**DBL_DIG**|15|Número de dígitos decimales de precisión|
|**DBL_EPSILON**|2.2204460492503131e-016|Valor más pequeño de modo que 1.0 + **DBL_EPSILON** != 1.0|
|**DBL_HAS_SUBNORM**|1|El tipo admite números no normales (denormales)|
|**DBL_MANT_DIG**|53|Número de bits en la mantisa|
|**DBL_MAX**|1.7976931348623158e+308|Valor máximo|
|**DBL_MAX_10_EXP**|308|Máximo exponente decimal|
|**DBL_MAX_EXP**|1024|Máximo exponente binario|
|**DBL_MIN**|2.2250738585072014e-308|Valor positivo normalizado mínimo|
|**DBL_MIN_10_EXP**|(-307)|Mínimo exponente decimal|
|**DBL_MIN_EXP**|(-1021)|Mínimo exponente binario|
|**_DBL_RADIX**|2|Base de exponente|
|**DBL_TRUE_MIN**|4.9406564584124654e-324|Valor no normal positivo mínimo|
|**FLT_DECIMAL_DIG**|9|Número de dígitos decimales de precisión de redondeo|
|**FLT_DIG**|6|Número de dígitos decimales de precisión|
|**FLT_EPSILON**|1.192092896e-07F|Valor más pequeño de modo que 1.0 + **FLT_EPSILON** != 1.0|
|**FLT_HAS_SUBNORM**|1|El tipo admite números no normales (denormales)|
|**FLT_MANT_DIG**|24|Número de bits en la mantisa|
|**FLT_MAX**|3.402823466e+38F|Valor máximo|
|**FLT_MAX_10_EXP**|38|Máximo exponente decimal|
|**FLT_MAX_EXP**|128|Máximo exponente binario|
|**FLT_MIN**|1.175494351e-38F|Valor positivo normalizado mínimo|
|**FLT_MIN_10_EXP**|(-37)|Mínimo exponente decimal|
|**FLT_MIN_EXP**|(-125)|Mínimo exponente binario|
|**FLT_RADIX**|2|Base de exponente|
|**FLT_TRUE_MIN**|1.401298464e-45F|Valor no normal positivo mínimo|
|**LDBL_DIG**|15|Número de dígitos decimales de precisión|
|**LDBL_EPSILON**|2.2204460492503131e-016|Valor más pequeño de modo que 1.0 + **LDBL_EPSILON** != 1.0|
|**LDBL_HAS_SUBNORM**|1|El tipo admite números no normales (denormales)|
|**LDBL_MANT_DIG**|53|Número de bits en la mantisa|
|**LDBL_MAX**|1.7976931348623158e+308|Valor máximo|
|**LDBL_MAX_10_EXP**|308|Máximo exponente decimal|
|**LDBL_MAX_EXP**|1024|Máximo exponente binario|
|**LDBL_MIN**|2.2250738585072014e-308|Valor positivo normalizado mínimo|
|**LDBL_MIN_10_EXP**|(-307)|Mínimo exponente decimal|
|**LDBL_MIN_EXP**|(-1021)|Mínimo exponente binario|
|**_LDBL_RADIX**|2|Base de exponente|
|**LDBL_TRUE_MIN**|4.9406564584124654e-324|Valor no normal positivo mínimo|
|**DECIMAL_DIG**|Igual que **DBL_DECIMAL_DIG**|Dígitos decimales predeterminados (dobles) de precisión de redondeo|

## <a name="see-also"></a>Vea también

[Constantes globales](../c-runtime-library/global-constants.md)
