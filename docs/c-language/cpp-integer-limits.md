---
title: Límites de enteros de C y C++
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 6940f36e37ec58ca8fe23c9062928cbf90b125bd
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778376"
---
# <a name="c-and-c-integer-limits"></a>Límites de enteros de C y C++

**Específicos de Microsoft**

Los límites de los tipos enteros de C y C++ se muestran en la tabla siguiente. Estos límites se definen en el archivo de encabezado estándar de C `<limits.h>`. El encabezado de la biblioteca estándar de C++ `<limits>` incluye `<climits>`, que a su vez incluye `<limits.h>`.

Microsoft C también permite la declaración de variables de enteros con tamaño, que son tipos enteros con un tamaño de 8, 16, 32 o 64 bits. Para obtener más información sobre los enteros con tamaño en C, vea [Tipos enteros con tamaño](../c-language/c-sized-integer-types.md).

## <a name="limits-on-integer-constants"></a>Límites en constantes de enteros

|**Constante**|Significado|Valor|
|------------------|-------------|-----------|
|**CHAR_BIT**|Número de bits de la variable menor que no es un campo de bits.|8|
|**SCHAR_MIN**|Valor mínimo de una variable de tipo **signed char**.|-128|
|**SCHAR_MAX**|Valor máximo de una variable de tipo **signed char**.|127|
|**UCHAR_MAX**|Valor máximo de una variable de tipo **unsigned char**.|255 (0xff)|
|**CHAR_MIN**|Valor mínimo de una variable de tipo **char**.|-128; 0 si se usa la opción /J|
|**CHAR_MAX**|Valor máximo de una variable de tipo **char**.|127; 255 si se usa la opción /J|
|**MB_LEN_MAX**|Número máximo de bytes de una constante de varios caracteres.|5|
|**SHRT_MIN**|Valor mínimo de una variable de tipo **short**.|-32768|
|**SHRT_MAX**|Valor máximo de una variable de tipo **short**.|32767|
|**USHRT_MAX**|Valor máximo de una variable de tipo **unsigned short**.|65535 (0xffff)|
|**INT_MIN**|Valor mínimo de una variable de tipo **int**.|-2147483647 - 1|
|**INT_MAX**|Valor máximo de una variable de tipo **int**.|2147483647|
|**UINT_MAX**|Valor máximo de una variable de tipo **unsigned int**.|4294967295 (0xffffffff)|
|**LONG_MIN**|Valor mínimo de una variable de tipo **long**.|-2147483647 - 1|
|**LONG_MAX**|Valor máximo de una variable de tipo **long**.|2147483647|
|**ULONG_MAX**|Valor máximo de una variable de tipo **unsigned long**.|4294967295 (0xffffffff)|
|**LLONG_MIN**|Valor mínimo de una variable de tipo **long long**.|-9,223,372,036,854,775,807 - 1|
|**LLONG_MAX**|Valor máximo de una variable de tipo **long long**.|9\.223.372.036.854.775.807|
|**ULLONG_MAX**|Valor máximo de una variable de tipo **unsigned long long**.|18,446,744,073,709,551,615 (0xffffffffffffffff)|

Si un valor supera la representación de entero mayor, el compilador de Microsoft genera un error.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Constantes de tipo entero de C](../c-language/c-integer-constants.md)
