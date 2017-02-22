---
title: "_ungetc_nolock, _ungetwc_nolock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ungetwc_nolock"
  - "_ungetc_nolock"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ungettc_nolock"
  - "ungetwc_nolock"
  - "ungetc_nolock"
  - "_ungetc_nolock"
  - "_ungetwc_nolock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ungetc_nolock (función)"
  - "_ungettc_nolock (función)"
  - "_ungetwc_nolock (función)"
  - "caracteres, volver a insertar en secuencia"
  - "ungetc_nolock (función)"
  - "ungettc_nolock (función)"
  - "ungetwc_nolock (función)"
ms.assetid: aa02d5c2-1be1-46d2-a8c4-b61269e9d465
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# _ungetc_nolock, _ungetwc_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Vuelve a insertar un carácter en el flujo.  
  
## Sintaxis  
  
```  
int _ungetc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _ungetwc_nolock(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a devolver.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 Si la operación se realiza correctamente, cada una de estas funciones devuelve el argumento `c` *de carácter.* Si `c` no se puede volver a insertar o si no se ha leído ningún carácter, el flujo de entrada no cambia y `_ungetc_nolock` devuelve `EOF`; `_ungetwc_nolock` devuelve `WEOF`.  Si `stream` es `NULL`, se devuelve `EOF` o `WEOF` y `errno` se establece en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Estas funciones son versiones de no bloqueo de `ungetc` y de `ungetwc`.  Las versiones con el sufijo `_nolock` son idénticas, salvo que no están protegidas contra interferencias de otros subprocesos.  Pueden ser más rápidas, porque no incurren en la sobrecarga de bloquear otros subprocesos.  Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ungettc_nolock`|`_ungetc_nolock`|`_ungetc_nolock`|`_ungetwc_nolock`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ungetc_nolock`|\<stdio.h\>|  
|`_ungetwc_nolock`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)