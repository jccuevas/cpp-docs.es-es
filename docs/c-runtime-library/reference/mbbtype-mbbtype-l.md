---
title: "_mbbtype, _mbbtype_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbbtype"
  - "_mbbtype_l"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbbtype_l"
  - "mbbtype"
  - "mbbtype_l"
  - "_mbbtype"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbbtype (función)"
  - "_mbbtype_l (función)"
  - "mbbtype (función)"
  - "mbbtype_l (función)"
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbbtype, _mbbtype_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el tipo de bytes, según el byte anterior.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _mbbtype(  
   unsigned char c,  
   int type   
);  
int _mbbtype_l(  
   unsigned char c,  
   int type,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a probar.  
  
 `type`  
 El tipo de byte que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_mbbtype`devuelve el tipo de byte en una cadena.  Esta decisión es contextual, según lo especificado por el valor de `type`, que proporciona la condición de prueba del control.  `type` es el tipo del byte anterior de la cadena.  Las constantes de manifiesto de la siguiente tabla se definen en Mbctype.h.  
  
|Valor de `type`|`_mbbtype` prueba para|Valor devuelto|`c`|  
|---------------------|----------------------------|--------------------|---------|  
|Cualquier valor excepto 1|Byte único o byte inicial válidos|`_MBC_SINGLE` \(0\)|Byte único \(0 x 20 – 0x7E, 0xA1 – 0xDF\)|  
|Cualquier valor excepto 1|Byte único o byte inicial válidos|`_MBC_LEAD` \(1\)|Byte inicial de un carácter multibyte \(0x81 – 0x9F, 0xE0 – 0xFC\)|  
|Cualquier valor excepto 1|Byte único o byte inicial válidos.|`_MBC_ILLEGAL`<br /><br /> \( –1\)|Carácter no válido \(cualquier valor excepto 0x20 – 0x7E, 0xA1 – 0xDF, 0x81 – 0x9F, 0xE0 – 0xFC|  
|1|Byte final válido|`_MBC_TRAIL` \(2\)|Byte final de un carácter multibyte. \(0x40 – 0x7E, 0x80 – 0xFC\)|  
|1|Byte final válido|`_MBC_ILLEGAL`<br /><br /> \( –1\)|Carácter no válido \(cualquier valor excepto 0x20 – 0x7E, 0xA1 – 0xDF, 0x81 – 0x9F, 0xE0 – 0xFC|  
  
## Comentarios  
 La función `_mbbtype` determina el tipo de un byte de un carácter multibyte.  Si el valor de `type` es cualquier valor excepto 1, `_mbbtype` prueba para un byte único o un byte inicial válidos de un carácter multibyte.  Si el valor de `type` es 1, `_mbbtype` prueba para un byte final válido de un carácter multibyte.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  La versión `_mbbtype` de esta función usa la configuración regional actual de su comportamiento dependiente de la configuración regional; la versión `_mbbtype_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, consulte [Configuración regional](../../c-runtime-library/locale.md).  
  
 En versiones anteriores, `_mbbtype` se denominaba `chkctype`.  Para el código nuevo use `_mbbtype`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_mbbtype`|\<mbstring.h\>|\<mbctype.h\>\*|  
|`_mbbtype_l`|\<mbstring.h\>|\<mbctype.h\>\*|  
  
 \* Para obtener definiciones de constantes de manifiesto que se usan como valores devueltos.  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No está disponible, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)