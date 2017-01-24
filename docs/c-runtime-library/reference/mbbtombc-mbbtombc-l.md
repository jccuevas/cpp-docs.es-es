---
title: "_mbbtombc, _mbbtombc_l | Microsoft Docs"
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
  - "_mbbtombc_l"
  - "_mbbtombc"
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
  - "_mbbtombc_l"
  - "_mbbtombc"
  - "mbbtombc_l"
  - "mbbtombc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbbtombc (función)"
  - "_mbbtombc_l (función)"
  - "mbbtombc (función)"
  - "mbbtombc_l (función)"
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbbtombc, _mbbtombc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un carácter multibyte de byte único en el carácter multibyte de doble byte correspondiente.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned int _mbbtombc(  
   unsigned int c   
);  
unsigned int _mbbtombc_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter de byte único que se va a convertir.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Si `_mbbtombc` convierte correctamente `c`, devuelve un carácter multibyte; de lo contrario, devuelve `c`.  
  
## Comentarios  
 La función `_mbbtombc` convierte un determinado carácter multibyte de byte único en el carácter multibyte de doble byte correspondiente.  Los caracteres deben estar dentro del intervalo 0x20 – 0x7E o 0xA1 – 0xDF para que se efectúe la conversión.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de esta función son idénticas, salvo por el hecho de que `_mbbtombc` usa la configuración regional actual para este comportamiento dependiente de la configuración regional y `_mbbtombc_l` usa el parámetro de configuración regional que se pasa.  Para más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En versiones anteriores, `_mbbtombc` se denominaba `hantozen`.  Para el código nuevo use `_mbbtombc`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbbtombc`|\<mbstring.h\>|  
|`_mbbtombc_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [\_mbctombb, \_mbctombb\_l](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)