---
title: "_mbctombb, _mbctombb_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbctombb_l"
  - "_mbctombb"
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
  - "_mbctombb_l"
  - "_mbctombb"
  - "mbctombb_l"
  - "mbctombb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbctombb (función)"
  - "_mbctombb_l (función)"
  - "mbctombb (función)"
  - "mbctombb_l (función)"
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _mbctombb, _mbctombb_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un carácter multibyte de doble byte en el carácter multibyte de un solo byte correspondiente.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned int _mbctombb(  
   unsigned int c   
);  
unsigned int _mbctombb_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter multibyte que se va a convertir.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Si se ejecutan correctamente, `_mbctombb` y `_mbctombb_l`devuelven el carácter de un solo byte que corresponde a `c`; de lo contrario, devuelven `c`.  
  
## Comentarios  
 Las funciones `_mbctombb` y `_mbctombb_l`convierten un carácter multibyte determinado en el carácter de un solo byte correspondiente.  Los caracteres deben corresponder a los caracteres de un solo byte del intervalo 0x20 – 0x7E o 0xA1 – 0xDF para que se realice la conversión.  
  
 El valor de la categoría `LC_CTYPE`  de la configuración regional afecta al valor de salida; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  La versión de esta función sin el sufijo `_l` usa la configuración regional actual de este comportamiento dependiente de la configuración regional; la versión con el sufijo `_l`  es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En versiones anteriores, `_mbctombb`  se denominaba `zentohan`.  Use \_`mbctombb` en su lugar.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbctombb`|\<mbstring.h\>|  
|`_mbctombb_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_mbbtombc, \_mbbtombc\_l](../../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [\_mbcjistojms, \_mbcjistojms\_l, \_mbcjmstojis, \_mbcjmstojis\_l](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [\_mbctohira, \_mbctohira\_l, \_mbctokata, \_mbctokata\_l](../../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)   
 [\_mbctolower, \_mbctolower\_l, \_mbctoupper, \_mbctoupper\_l](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)