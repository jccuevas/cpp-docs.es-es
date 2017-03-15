---
title: "_mbsbtype, _mbsbtype_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsbtype_l"
  - "_mbsbtype"
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
  - "mbsbtype"
  - "mbsbtype_l"
  - "_mbsbtype_l"
  - "_mbsbtype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsbtype (función)"
  - "_mbsbtype_l (función)"
  - "mbsbtype (función)"
  - "mbsbtype_l (función)"
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _mbsbtype, _mbsbtype_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el tipo de byte en una cadena.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _mbsbtype(  
   const unsigned char *mbstr,  
   size_t count   
);  
int _mbsbtype_l(  
   const unsigned char *mbstr,  
   size_t count,  
   _locale_t locale   
);  
```  
  
#### Parámetros  
 `mbstr`  
 Dirección de una secuencia de caracteres multibyte.  
  
 `count`  
 Desplazamiento de bytes desde el encabezado de la cadena.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_mbsbtype` y `_mbsbtype_l` devuelven un valor entero que indica el resultado de la prueba en el byte especificado.  Las constantes de manifiesto de la siguiente tabla se definen en Mbctype.h.  
  
|Valor devuelto|Tipo de byte|  
|--------------------|------------------|  
|`_MBC_SINGLE` \(0\)|Carácter de un solo byte.  Por ejemplo, en la página de códigos 932, `_mbsbtype` devuelve 0 si el byte especificado está dentro del intervalo 0x20 – 0x7E o 0xA1 – 0xDF.|  
|`_MBC_LEAD` \(1\)|Byte inicial de un carácter multibyte.  Por ejemplo, en la página de códigos 932, `_mbsbtype` devuelve 1 si el byte especificado está dentro del intervalo 0x81 – 0x9F o 0xE0 – 0xFC.|  
|`_MBC_TRAIL` \(2\)|Byte final de un carácter multibyte.  Por ejemplo, en la página de códigos 932, `_mbsbtype` devuelve 2 si el byte especificado está dentro del intervalo 0x40 – 0x7E o 0x80 – 0xFC.|  
|`_MBC_ILLEGAL` \(–1\)|Cadena `NULL`, carácter no válido o byte `NULL` encontrado antes del byte en el `count` de desplazamiento de `mbstr`.|  
  
## Comentarios  
 La función `_mbsbtype` determina el tipo de un byte de una cadena de caracteres multibyte.  La función solo examina el byte de `count` de desplazamiento en `mbstr`, omitiendo los caracteres no válidos anteriores al byte especificado.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  La versión de esta función sin el sufijo `_l` usa la configuración regional actual de su comportamiento dependiente de la configuración regional; la versión con el sufijo `_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si la cadena de entrada es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `_MBC_ILLEGAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_mbsbtype`|\<mbstring.h\>|\<mbctype.h\>\*|  
|`_mbsbtype_l`|\<mbstring.h\>|\<mbctype.h\>\*|  
  
 \* En el caso de las constantes de manifiesto usadas como valores devueltos.  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No está disponible, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx).  
  
## Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)