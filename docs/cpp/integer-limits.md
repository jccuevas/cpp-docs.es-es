---
title: "L&#237;mites de enteros | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "límites de enteros"
  - "límites para enteros"
  - "límites, enteros"
  - "LIMITS.H (archivo de encabezado)"
ms.assetid: 6922bdbf-0f49-443b-bc03-ee182e4cbd57
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# L&#237;mites de enteros
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Los límites de los tipos enteros se muestran en la tabla siguiente.  Estos límites también se definen en el archivo de encabezado estándar LIMITS.H.  
  
### Límites en constantes de enteros  
  
|Constante|Significado|Valor|  
|---------------|-----------------|-----------|  
|**CHAR\_BIT**|Número de bits de la variable menor que no es un campo de bits.|8|  
|**SCHAR\_MIN**|Valor mínimo de una variable de tipo **signed char**.|–128|  
|**SCHAR\_MAX**|Valor máximo de una variable de tipo **signed char**.|127|  
|**UCHAR\_MAX**|Valor máximo de una variable de tipo `unsigned char`.|255 \(0xff\)|  
|**CHAR\_MIN**|Valor mínimo de una variable de tipo `char`.|–128; 0 si se usa la opción \/J|  
|**CHAR\_MAX**|Valor máximo de una variable de tipo `char`.|127; 255 si se usa la opción \/J|  
|**MB\_LEN\_MAX**|Número máximo de bytes de una constante de varios caracteres.|5|  
|**SHRT\_MIN**|Valor mínimo de una variable de tipo **short**.|–32768|  
|**SHRT\_MAX**|Valor máximo de una variable de tipo **short**.|32767|  
|**USHRT\_MAX**|Valor máximo de una variable de tipo **unsigned short**.|65535 \(0xffff\)|  
|**INT\_MIN**|Valor mínimo de una variable de tipo `int`.|–2147483648|  
|**INT\_MAX**|Valor máximo de una variable de tipo `int`.|2147483647|  
|**UINT\_MAX**|Valor máximo de una variable de tipo `unsigned int`.|4294967295 \(0xffffffff\)|  
|**LONG\_MIN**|Valor mínimo de una variable de tipo **long**.|–2147483648|  
|**LONG\_MAX**|Valor máximo de una variable de tipo **long**.|2147483647|  
|**ULONG\_MAX**|Valor máximo de una variable de tipo `unsigned long`.|4294967295 \(0xffffffff\)|  
|**\_I64\_MIN**|Valor mínimo de una variable de tipo `__int64`|\-9223372036854775808|  
|**\_I64\_MAX**|Valor máximo de una variable de tipo `__int64`|9223372036854775807|  
|**\_UI64\_MAX**|Valor máximo de una variable de tipo **\_\_int64 sin signo**|18446744073709551615 \(0xffffffffffffffff\)|  
  
 Si un valor supera la representación de entero mayor, el compilador de Microsoft genera un error.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Límites flotantes](../cpp/floating-limits.md)