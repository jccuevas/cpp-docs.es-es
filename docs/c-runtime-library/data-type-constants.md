---
title: "Constantes de tipo de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FLT_MIN"
  - "SHRT_MAX"
  - "CHAR_MIN"
  - "MB_LEN_MAX"
  - "DBL_EPSILON"
  - "SHRT_MIN"
  - "_FLT_RADIX"
  - "FLT_DIG"
  - "FLT_MAX_10_EXP"
  - "FLT_MANT_DIG"
  - "DBL_MAX_EXP"
  - "SCHAR_MIN"
  - "SCHAR_MAX"
  - "DBL_MIN"
  - "FLT_MIN_10_EXP"
  - "_DBL_ROUNDS"
  - "USHRT_MAX"
  - "FLT_MAX_EXP"
  - "LONG_MAX"
  - "DBL_MAX"
  - "DBL_DIG"
  - "FLT_MIN_EXP"
  - "INT_MIN"
  - "DBL_MIN_10_EXP"
  - "CHAR_BIT"
  - "INT_MAX"
  - "ULONG_MAX"
  - "DBL_MIN_EXP"
  - "LONG_MIN"
  - "_FLT_ROUNDS"
  - "DBL_MANT_DIG"
  - "_DBL_RADIX"
  - "CHAR_MAX"
  - "FLT_MAX"
  - "DBL_MAX_10_EXP"
  - "UCHAR_MAX"
  - "FLT_EPSILON"
  - "UINT_MAX"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_DBL_RADIX (constante)"
  - "_DBL_ROUNDS (constante)"
  - "_FLT_RADIX (constante)"
  - "_FLT_ROUNDS (constante)"
  - "CHAR_BIT (constante)"
  - "CHAR_MAX (constante)"
  - "CHAR_MIN (constante)"
  - "constantes [C++], tipo de datos"
  - "constantes de tipo de datos [C++]"
  - "DBL_DIG (constante)"
  - "DBL_EPSILON (constante)"
  - "DBL_MANT_DIG (constante)"
  - "DBL_MAX (constante)"
  - "DBL_MAX_10_EXP (constante)"
  - "DBL_MAX_EXP (constante)"
  - "DBL_MIN (constante)"
  - "DBL_MIN_10_EXP (constante)"
  - "DBL_MIN_EXP (constante)"
  - "DBL_RADIX (constante)"
  - "DBL_ROUNDS (constante)"
  - "FLT_DIG (constante)"
  - "FLT_EPSILON (constante)"
  - "FLT_MANT_DIG (constante)"
  - "FLT_MAX (constante)"
  - "FLT_MAX_10_EXP (constante)"
  - "FLT_MAX_EXP (constante)"
  - "FLT_MIN (constante)"
  - "FLT_MIN_10_EXP (constante)"
  - "FLT_MIN_EXP (constante)"
  - "FLT_RADIX (constante)"
  - "FLT_ROUNDS (constante)"
  - "INT_MAX (constante)"
  - "INT_MIN (constante)"
  - "LONG_MAX (constante)"
  - "LONG_MIN (constante)"
  - "MB_LEN_MAX (constante)"
  - "SCHAR_MAX (constante)"
  - "SCHAR_MIN (constante)"
  - "SHRT_MAX (constante)"
  - "SHRT_MIN (constante)"
  - "UCHAR_MAX (constante)"
  - "UINT_MAX (constante)"
  - "ULONG_MAX (constante)"
  - "USHRT_MAX (constante)"
ms.assetid: c0f1c405-0465-41d5-b5ff-e81cdb6f1622
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes de tipo de datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las constantes de tipo de datos son intervalos de valores implementación\-dependientes permitidos para los tipos de datos enteros.  Las constantes enumeradas abajo proporcionan intervalos para los tipos de datos enteros y se definen en LIMITS.H.  
  
> [!NOTE]
>  La opción del compilador \/J cambia `char` predeterminado en `unsigned`.  
  
|Constante|Valor|Significado|  
|---------------|-----------|-----------------|  
|**SCHAR\_MAX**|127|Valor con signo de `char` de máximo|  
|**SCHAR\_MIN**|–128|Valor con signo de `char` el mínimo|  
|**UCHAR\_MAX**|255 \(0xff\)|Valor máximo de `unsigned char`|  
|**CHAR\_BIT**|8|Número de bits de `char`|  
|**USHRT\_MAX**|65535 \(0xffff\)|Valor máximo de **unsigned short**|  
|**SHRT\_MAX**|32767|Valor \(con signo\) máximo de **corto**|  
|**SHRT\_MIN**|–32768|Valor \(con signo\) mínimo de **corto**|  
|**UINT\_MAX**|4294967295 \(0xffffffff\)|Valor máximo de `unsigned int`|  
|**ULONG\_MAX**|4294967295 \(0xffffffff\)|Valor máximo de `unsigned long`|  
|**INT\_MAX**|2147483647|Valor \(con signo\) máximo de `int`|  
|**INT\_MIN**|–2147483647–1|Valor \(con signo\) mínimo de `int`|  
|**LONG\_MAX**|2147483647|Valor \(con signo\) máximo de **long**|  
|**LONG\_MIN**|–2147483647–1|Valor \(con signo\) mínimo de **long**|  
|**CHAR\_MAX**|127 \(255 si opción \/J utilizada\)|Valor máximo de `char`|  
|**CHAR\_MIN**|– 128 \(0 si opción \/J utilizada\)|Valor mínimo de `char`|  
|**MB\_LEN\_MAX**|2|Número de bytes máximo en multibyte `char`|  
|**\_I64\_MAX**|9223372036854775807|Valor \(con signo\) máximo de**int64** de|  
|**\_I64\_MIN**|\-9223372036854775807\-1|Valor \(con signo\) mínimo de**int64** de|  
|**\_UI64\_MAX**|0xffffffffffffffff|Valor \(sin signo\) máximo de**int64** de|  
  
 Las constantes siguientes proporcionan el intervalo y otras características de los tipos de datos de **double** y de **flotante** , y se definen en FLOAT.H:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|**DBL\_DIG**|15|\# de dígitos decimales de precisión|  
|**DBL\_EPSILON**|2.2204460492503131e\-016|En el menor tales que**DBL\_EPSILON** 1,0\+\! \=1.0|  
|**DBL\_MANT\_DIG**|53|\# de bits en mantisa|  
|**DBL\_MAX**|1.7976931348623158e\+308|Valor máximo|  
|**DBL\_MAX\_10\_EXP**|308|Exponente decimal máximo|  
|**DBL\_MAX\_EXP**|1024|Exponente binario máximo|  
|**DBL\_MIN**|2.2250738585072014e\-308|Valor positivo mínimo|  
|**DBL\_MIN\_10\_EXP**|\(\-307\)|Exponente decimal mínimo|  
|**DBL\_MIN\_EXP**|\(–1021\)|Exponente binario mínimo|  
|**\_DBL\_RADIX**|2|Base de exponente|  
|**\_DBL\_ROUNDS**|1|Redondeo de suma: por|  
|**FLT\_DIG**|6|Número de dígitos decimales de precisión|  
|**FLT\_EPSILON**|1.192092896e\-07F|En el menor tales que**FLT\_EPSILON** 1,0\+\! \=1.0|  
|**FLT\_MANT\_DIG**|24|Número de bits de mantisa|  
|**FLT\_MAX**|3.402823466e\+38F|Valor máximo|  
|**FLT\_MAX\_10\_EXP**|38|Exponente decimal máximo|  
|**FLT\_MAX\_EXP**|128|Exponente binario máximo|  
|**FLT\_MIN**|1.175494351e\-38F|Valor positivo mínimo|  
|**FLT\_MIN\_10\_EXP**|\(–37\)|Exponente decimal mínimo|  
|**FLT\_MIN\_EXP**|\(–125\)|Exponente binario mínimo|  
|**FLT\_RADIX**|2|Base de exponente|  
|**FLT\_ROUNDS**|1|Redondeo de suma: por|  
  
## Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)