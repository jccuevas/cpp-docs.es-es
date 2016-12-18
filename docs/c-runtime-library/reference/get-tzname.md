---
title: "_get_tzname | Microsoft Docs"
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
  - "_get_tzname"
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
  - "_get_tzname"
  - "get_tzname"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_tzname (función)"
  - "get_tzname (función)"
  - "zonas horarias"
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_tzname
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera la representación de cadena de caracteres del nombre o el nombre estándar de la zona horaria de la hora luz \(DST\) de la zona horaria.  
  
## Sintaxis  
  
```  
errno_t _get_tzname(  
    size_t* pReturnValue,  
    char* timeZoneName,  
    size_t sizeInBytes,  
    int index      
);  
```  
  
#### Parámetros  
 \[out\] `pReturnValue`  
 La longitud de la cadena de `timeZoneName` incluido un terminador NULL.  
  
 \[out\] `timeZoneName`  
 La dirección de una cadena de caracteres para la representación del nombre o el nombre estándar de la zona horaria de la hora luz \(DST\) de la zona horaria, dependiendo de `index`.  
  
 \[in\] `sizeInBytes`  
 El tamaño de la cadena de caracteres de `timeZoneName` en bytes.  
  
 \[in\] `index`  
 El índice de uno de los dos nombres de zona horaria a recuperar.  
  
## Valor devuelto  
 Cero si es correcto, si no es un valor de tipo de `errno` .  
  
 Si o `timeZoneName` es `NULL`, o `sizeInBytes` es cero o menor que cero \(pero no ambos\), se invoca un controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
### Condiciones de error  
  
|`pReturnValue`|`timeZoneName`|`sizeInBytes`|`index`|Valor devuelto|Contenido de `timeZoneName`|  
|--------------------|--------------------|-------------------|-------------|--------------------|---------------------------------|  
|tamaño del nombre de t\-z|`NULL`|0|0 ó 1|0|no modificado|  
|tamaño del nombre de t\-z|any|\> 0|0 ó 1|0|T\-z llama|  
|no modificado|`NULL`|\> 0|any|`EINVAL`|no modificado|  
|no modificado|any|cero|any|`EINVAL`|no modificado|  
|no modificado|any|\> 0|\> 1|`EINVAL`|no modificado|  
  
## Comentarios  
 La función de `_get_tzname` recupera la representación de cadena de caracteres del nombre o el nombre estándar de la zona horaria de la hora luz \(DST\) de la zona horaria en la dirección de `timeZoneName` según el valor de índice, junto con el tamaño de la cadena en `pReturnValue`.  Si `timeZoneName` es `NULL` y `sizeInBytes` es cero, del tamaño de la cadena de cualquier zona horaria de bytes se devuelve en `pReturnValue`.  Los valores de índice deben ser 0 para la zona horaria estándar o 1 para la zona horaria estándar de hora de luz; cualquier otro valor de índice tiene resultados indeterminados.  
  
### Valores de índice  
  
|`index`|Contenido de `timeZoneName`|valor predeterminado de`timeZoneName`|  
|-------------|---------------------------------|-------------------------------------------|  
|0|Nombre de la zona horaria|“PST”|  
|1|Nombre estándar de la zona horaria de la hora luz|“PDT”|  
|\> 1 o \< 0|`errno` establecido en `EINVAL`|no modificado|  
  
 A menos que los valores explícitamente se cambien durante el tiempo de ejecución, los valores predeterminados son “PST” y “PDT” respectivamente.  Los tamaños de estas matrices de caracteres rige el valor de `TZNAME_MAX` .  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_tzname`|\<time.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [\_get\_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [TZNAME\_MAX](../../c-runtime-library/tzname-max.md)