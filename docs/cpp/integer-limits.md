---
title: "Límites de enteros | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- integral limits
- limits, integer
- LIMITS.H header file
- integer limits
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 67240b24df0c741a2441e17ebe9908c05bfca9f3
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="integer-limits"></a>Límites de enteros
**Específicos de Microsoft**  
  
 Los límites de los tipos enteros se muestran en la tabla siguiente. Estos límites también se definen en el archivo de encabezado estándar LIMITS.H.  
  
### <a name="limits-on-integer-constants"></a>Límites en constantes de enteros  
  
|Constante|Significado|Valor|  
|--------------|-------------|-----------|  
|**CHAR_BIT**|Número de bits de la variable menor que no es un campo de bits.|8|  
|**SCHAR_MIN**|Valor mínimo de una variable de tipo **signed char**.|-128|  
|**SCHAR_MAX**|Valor máximo de una variable de tipo **signed char**.|127|  
|**UCHAR_MAX**|Valor máximo de una variable de tipo `unsigned char`.|255 (0xff)|  
|**CHAR_MIN**|Valor mínimo de una variable de tipo `char`.|-128; 0 si se usa la opción /J|  
|**CHAR_MAX**|Valor máximo de una variable de tipo `char`.|127; 255 si se usa la opción /J|  
|**MB_LEN_MAX**|Número máximo de bytes de una constante de varios caracteres.|5|  
|**SHRT_MIN**|Valor mínimo de una variable de tipo **short**.|-32768|  
|**SHRT_MAX**|Valor máximo de una variable de tipo **short**.|32767|  
|**USHRT_MAX**|Valor máximo de una variable de tipo **unsigned short**.|65535 (0xffff)|  
|**INT_MIN**|Valor mínimo de una variable de tipo `int`.|-2147483648|  
|**INT_MAX**|Valor máximo de una variable de tipo `int`.|2147483647|  
|**UINT_MAX**|Valor máximo de una variable de tipo `unsigned int`.|4294967295 (0xffffffff)|  
|**LONG_MIN**|Valor mínimo de una variable de tipo **long**.|-2147483648|  
|**LONG_MAX**|Valor máximo de una variable de tipo **long**.|2147483647|  
|**ULONG_MAX**|Valor máximo de una variable de tipo `unsigned long`.|4294967295 (0xffffffff)|  
|**_I64_MIN**|Valor mínimo de una variable de tipo `__int64`|-9223372036854775808|  
|**_I64_MAX**|Valor máximo de una variable de tipo `__int64`|9223372036854775807|  
|**_UI64_MAX**|Valor máximo de una variable de tipo **__int64 sin signo**|18446744073709551615 (0xffffffffffffffff)|  
  
 Si un valor supera la representación de entero mayor, el compilador de Microsoft genera un error.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Límites flotantes](../cpp/floating-limits.md)
