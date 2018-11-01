---
title: Límites de enteros
ms.date: 01/29/2018
helpviewer_keywords:
- integral limits
- limits, integer
- limits.h header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
ms.openlocfilehash: 0d14f6246dd2ec71c4e0b2286bb1f2b3325085b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522972"
---
# <a name="integer-limits"></a>Límites de enteros

**Específicos de Microsoft**

Los límites de los tipos enteros se muestran en la tabla siguiente. Estos límites también se definen en el archivo de encabezado estándar \<limits.h >.

## <a name="limits-on-integer-constants"></a>Límites en constantes de enteros

|Constante|Significado|Valor|
|--------------|-------------|-----------|
|CHAR_BIT|Número de bits de la variable menor que no es un campo de bits.|8|
|SCHAR_MIN|Valor mínimo de una variable de tipo **signed char**.|-128|
|SCHAR_MAX|Valor máximo de una variable de tipo **signed char**.|127|
|UCHAR_MAX|Valor máximo de una variable de tipo **unsigned char**.|255 (0xff)|
|CHAR_MIN|Valor mínimo de una variable de tipo **char**.|-128; 0 si se usa la opción /J|
|CHAR_MAX|Valor máximo de una variable de tipo **char**.|127; 255 si se usa la opción /J|
|MB_LEN_MAX|Número máximo de bytes de una constante de varios caracteres.|5|
|SHRT_MIN|Valor mínimo de una variable de tipo **short**.|-32768|
|SHRT_MAX|Valor máximo de una variable de tipo **short**.|32767|
|USHRT_MAX|Valor máximo de una variable de tipo **unsigned short**.|65535 (0xffff)|
|INT_MIN|Valor mínimo de una variable de tipo **int**.|-2147483648|
|INT_MAX|Valor máximo de una variable de tipo **int**.|2147483647|
|UINT_MAX|Valor máximo de una variable de tipo **unsigned int**.|4294967295 (0xffffffff)|
|LONG_MIN|Valor mínimo de una variable de tipo **long**.|-2147483648|
|LONG_MAX|Valor máximo de una variable de tipo **long**.|2147483647|
|ULONG_MAX|Valor máximo de una variable de tipo **unsigned long**.|4294967295 (0xffffffff)|
|LLONG_MIN|Valor mínimo de una variable de tipo **long long**|-9223372036854775808|
|LLONG_MAX|Valor máximo de una variable de tipo **long long**|9223372036854775807|
|ULLONG_MAX|Valor máximo de una variable de tipo **long long sin signo**|18446744073709551615 (0xffffffffffffffff)|

Si un valor supera la representación de entero mayor, el compilador de Microsoft genera un error.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Límites flotantes](../cpp/floating-limits.md)