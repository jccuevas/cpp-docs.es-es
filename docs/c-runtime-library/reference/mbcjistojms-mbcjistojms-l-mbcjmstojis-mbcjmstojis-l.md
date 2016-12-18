---
title: "_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbcjistojms"
  - "_mbcjmstojis"
  - "_mbcjistojms_l"
  - "_mbcjmstojis_l"
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
  - "mbcjistojms"
  - "_mbcjistojms"
  - "_mbcjistojms_l"
  - "_mbcjmstojis_l"
  - "_mbcjmstojis"
  - "mbcjmstojis_l"
  - "mbcjistojms_l"
  - "mbcjmstojis"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbcjistojms (función)"
  - "_mbcjistojms_l (función)"
  - "_mbcjmstojis (función)"
  - "_mbcjmstojis_l (función)"
  - "mbcjistojms (función)"
  - "mbcjistojms_l (función)"
  - "mbcjmstojis (función)"
  - "mbcjmstojis_l (función)"
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte caracteres de JIS en caracteres de Japan Microsoft \(JMS\), y viceversa.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned int _mbcjistojms(  
   unsigned int c   
);  
unsigned int _mbcjistojms_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbcjmstojis(  
   unsigned int c   
);  
unsigned int _mbcjmstojis_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a convertir.  
  
 `local`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 En la configuración regional japonesa, estas funciones devuelven un carácter convertidos, o 0 si la conversión no es posible.  En una configuración regional no japonesa, estas funciones devuelven el carácter que se pasa.  
  
## Comentarios  
 La función `_mbcjistojms`  convierte un carácter de JIS en un carácter de Microsoft Kanji \(Shift JIS\).  El carácter se convierte solo si los bytes inicial y final están en el intervalo 0x21 – 0x7E.  Si el byte inicial o final está fuera de este intervalo, `errno` se establece en `EILSEQ`.  Para obtener más información sobre este y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 La función `_mbcjmstojis`convierte un carácter de Shift JIS en un carácter de JIS.  El carácter se convierte solo si el byte inicial está en el intervalo 0x81 – 0x9F o 0xE0 – 0xFC, y el byte final está en el intervalo 0x40 – 0x7E o 0x80 – 0xFC.  Observe que algunos puntos de código de ese intervalo no tienen un carácter asignado, por lo que no pueden convertirse.  
  
 El valor de `c` debe ser un valor de 16 bits cuyos 8 bits superiores representen el byte inicial del carácter que se va a convertir y cuyos 8 bits inferiores representen el byte final.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En versiones anteriores, `_mbcjistojms`  y `_mbcjmstojis`  se denominaban `jistojms`  y `jmstojis`, respectivamente.  En su lugar, se deben usar `_mbcjistojms`,`_mbcjistojms_l`,`_mbcjmstojis` y `_mbcjmstojis_l`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbcjistojms`|\<mbstring.h\>|  
|`_mbcjistojms_l`|\<mbstring.h\>|  
|`_mbcjmstojis`|\<mbstring.h\>|  
|`_mbcjmstojis_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)