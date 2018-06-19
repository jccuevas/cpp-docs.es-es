---
title: Límites de enteros de C++ | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c95e0affa9047aa41ee5ff04b011ac0fbd8d63d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388057"
---
# <a name="c-integer-limits"></a>Límites de enteros de C++

**Específicos de Microsoft**

Los límites de los tipos enteros se muestran en la tabla siguiente. Estos límites se definen en el archivo de encabezado estándar LIMITS.H. Microsoft C también permite la declaración de variables de enteros con tamaño, que son tipos enteros con un tamaño de 8, 16 o 32 bits. Para obtener más información sobre los enteros con tamaño, vea [Tipos enteros con tamaño](../c-language/c-sized-integer-types.md).

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

Si un valor supera la representación de entero mayor, el compilador de Microsoft genera un error.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Constantes de tipo entero de C](../c-language/c-integer-constants.md)  
