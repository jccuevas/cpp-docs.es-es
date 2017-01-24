---
title: "_get_errno | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_errno"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_get_errno"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_errno (función)"
  - "errno (variable global)"
  - "get_errno (función)"
ms.assetid: b3fd5ebc-f41b-4314-a2f4-2f2d79d6e740
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_errno
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene el valor actual de la variable global de errno.  
  
## Sintaxis  
  
```  
errno_t _get_errno(   
   int * pValue   
);  
```  
  
#### Parámetros  
 \[out\] `pValue`  
 Un puntero a un entero que se rellenará con el valor actual de la variable de `errno` .  
  
## Valor devuelto  
 Devuelve cero si correctamente; un código de error del error.  Si `pValue` es `NULL`, se invoca el controlador no válido del parámetro tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
## Comentarios  
 Los valores posibles de `errno` se definen en Errno.h.  Vea también [errno \(Constantes\)](../../c-runtime-library/errno-constants.md).  
  
## Ejemplo  
  
```  
// crt_get_errno.c  
#include <stdio.h>  
#include <fcntl.h>  
#include <sys/stat.h>  
#include <share.h>  
#include <errno.h>  
  
int main()  
{  
   errno_t err;  
   int pfh;  
   _sopen_s( &pfh, "nonexistent.file", _O_WRONLY, _SH_DENYNO, _S_IWRITE );  
   _get_errno( &err );  
   printf( "errno = %d\n", err );  
   printf( "fyi, ENOENT = %d\n", ENOENT );  
}  
```  
  
  **errno \= 2**  
**FYI, ENOENT \= 2**   
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_get_errno`|\<stdlib.h\>|\<errno.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente de .NET Framework  
 No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_set\_errno](../../c-runtime-library/reference/set-errno.md)   
 [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)