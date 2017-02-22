---
title: "_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbctohira"
  - "_mbctohira_l"
  - "_mbctokata"
  - "_mbctokata_l"
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
  - "_mbctokata"
  - "mbctohira"
  - "_mbctohira"
  - "_mbctohira_l"
  - "mbctokata"
  - "mbctokata_l"
  - "mbctohira_l"
  - "_mbctokata_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbctohira (función)"
  - "_mbctohira_l (función)"
  - "_mbctokata (función)"
  - "_mbctokata_l (función)"
  - "mbctohira (función)"
  - "mbctohira_l (función)"
  - "mbctokata (función)"
  - "mbctokata_l (función)"
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte caracteres Hiragana y Katakana entre sí.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned int _mbctohira(  
   unsigned int c   
);  
unsigned int _mbctohira_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbctokata(  
   unsigned int c   
);  
unsigned int _mbctokata_l(  
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
 Cada una de estas funciones devuelve el carácter convertido `c`, si es posible.  De lo contrario, devuelve el carácter `c` sin cambios.  
  
## Comentarios  
 Las funciones `_mbctohira` y `_mbctokata` prueban un carácter `c` y, si es posible, aplican una de las conversiones siguientes.  
  
|Rutinas|Convierte|  
|-------------|---------------|  
|`_mbctohira,_mbctohira_l`|Katakana multibyte a Hiragana multibyte.|  
|`_mbctokata,_mbctokata_l`|Hiragana multibyte a Katakana multibyte.|  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones son idénticas, salvo por el hecho de que las que no tienen el sufijo `_l` usan la configuración regional actual cuando el comportamiento depende de la configuración regional, y las que sí tienen el sufijo `_l` usan en su lugar el parámetro de configuración regional que se ha pasado.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En versiones anteriores, `_mbctohira` se denominaba `jtohira` y `_mbctokata` se denominaba `jtokata`.  Para código nuevo, use los nuevos nombres.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbctohira`|\<mbstring.h\>|  
|`_mbctohira_l`|\<mbstring.h\>|  
|`_mbctokata`|\<mbstring.h\>|  
|`_mbctokata_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_mbcjistojms, \_mbcjistojms\_l, \_mbcjmstojis, \_mbcjmstojis\_l](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [\_mbctolower, \_mbctolower\_l, \_mbctoupper, \_mbctoupper\_l](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)   
 [\_mbctombb, \_mbctombb\_l](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)