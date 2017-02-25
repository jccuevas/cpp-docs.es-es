---
title: "_get_dstbias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_dstbias"
  - "__dstbias"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__dstbias"
  - "_get_dstbias"
  - "get_dstbias"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__dstbias"
  - "_get_dstbias (función)"
  - "Diferencia horaria de horario de verano"
  - "get_dstbias (función)"
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# _get_dstbias
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el desplazamiento de horario de verano en segundos.  
  
## Sintaxis  
  
```  
  
error_t _get_dstbias(      int* seconds );  
```  
  
#### Parámetros  
 `seconds`  
 Desplazamiento en segundos del horario de verano.  
  
## Valor devuelto  
 Cero si se ejecuta correctamente, o un valor `errno` si se produce un error.  
  
## Comentarios  
 La función `_get_dstbias` recupera el número de segundos en el horario de verano como un entero.  Si el horario de verano está en vigor, el desplazamiento predeterminado es de 3600 segundos, que es la cantidad de segundos que hay en una hora \(si bien en algunas regiones el desplazamiento es de dos horas\).  
  
 Si `seconds` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
 Le recomendamos usar esta función en vez de la macro `_dstbias` o la función desusada `__dstbias`.  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_dstbias`|\<time.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [\_get\_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [\_get\_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [\_get\_tzname](../../c-runtime-library/reference/get-tzname.md)