---
title: Constantes de tipo de datos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cf9a64b81ae90c517e9cd15e796dfb1333c7b08c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-constants"></a>Constantes de tipo de datos
Las constantes de tipo de datos son intervalos de valores dependientes de la implementación permitidos para los tipos de datos enteros. Las constantes que se muestran a continuación proporcionan los intervalos para los tipos de datos enteros y se definen en LIMITS.H.  
  
> [!NOTE]
>  La opción del compilador /J cambia el tipo predeterminado de `char` a `unsigned`.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|**SCHAR_MAX**|127|Máximo valor `char` con signo|  
|**SCHAR_MIN**|-128|Mínimo valor `char` con signo|  
|**UCHAR_MAX**|255 (0xff)|Máximo valor `unsigned char`|  
|**CHAR_BIT**|8|Número de bits en `char`|  
|**USHRT_MAX**|65535 (0xffff)|Máximo valor **unsigned short**|  
|**SHRT_MAX**|32767|Máximo valor **short** (con signo)|  
|**SHRT_MIN**|-32768|Mínimo valor **short** (con signo)|  
|**UINT_MAX**|4294967295 (0xffffffff)|Máximo valor `unsigned int`|  
|**ULONG_MAX**|4294967295 (0xffffffff)|Máximo valor `unsigned long`|  
|**INT_MAX**|2147483647|Máximo valor `int` (con signo)|  
|**INT_MIN**|-2147483647-1|Mínimo valor `int` (con signo)|  
|**LONG_MAX**|2147483647|Máximo valor **long** (con signo)|  
|**LONG_MIN**|-2147483647-1|Mínimo valor **long** (con signo)|  
|**CHAR_MAX**|127 (255 si se usa la opción /J)|Máximo valor `char`|  
|**CHAR_MIN**|-128 (0 si se usa la opción /J)|Mínimo valor `char`|  
|**MB_LEN_MAX**|2|Número máximo de bytes en un `char` multibyte|  
|**_I64_MAX**|9223372036854775807|Máximo valor __**int64** (con signo)|  
|**_I64_MIN**|-9223372036854775807-1|Mínimo valor __**int64** (con signo)|  
|**_UI64_MAX**|0xffffffffffffffff|Máximo valor __**int64** (sin signo)|  
  
 Las siguientes constantes proporcionan el intervalo y otras características de los tipos de datos **double** y **float**, y se definen en FLOAT.H:  
  
|Constante|Valor|Description|  
|--------------|-----------|-----------------|  
|**DBL_DIG**|15|Número de dígitos decimales de precisión|  
|**DBL_EPSILON**|2.2204460492503131e-016|Menor que 1,0+**DBL_EPSILON** !=1,0|  
|**DBL_MANT_DIG**|53|Número de bits en mantisa|  
|**DBL_MAX**|1.7976931348623158e+308|Valor máximo|  
|**DBL_MAX_10_EXP**|308|Máximo exponente decimal|  
|**DBL_MAX_EXP**|1024|Máximo exponente binario|  
|**DBL_MIN**|2.2250738585072014e-308|Valor positivo mínimo|  
|**DBL_MIN_10_EXP**|(-307)|Mínimo exponente decimal|  
|**DBL_MIN_EXP**|(-1021)|Mínimo exponente binario|  
|**_DBL_RADIX**|2|Base de exponente|  
|**_DBL_ROUNDS**|1|Adición de redondeo: cerca|  
|**FLT_DIG**|6|Número de dígitos decimales de precisión|  
|**FLT_EPSILON**|1.192092896e-07F|Menor que 1,0+**FLT_EPSILON** !=1,0|  
|**FLT_MANT_DIG**|24|Número de bits en mantisa|  
|**FLT_MAX**|3.402823466e+38F|Valor máximo|  
|**FLT_MAX_10_EXP**|38|Máximo exponente decimal|  
|**FLT_MAX_EXP**|128|Máximo exponente binario|  
|**FLT_MIN**|1.175494351e-38F|Valor positivo mínimo|  
|**FLT_MIN_10_EXP**|(-37)|Mínimo exponente decimal|  
|**FLT_MIN_EXP**|(-125)|Mínimo exponente binario|  
|**FLT_RADIX**|2|Base de exponente|  
|**FLT_ROUNDS**|1|Adición de redondeo: cerca|  
  
## <a name="see-also"></a>Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)