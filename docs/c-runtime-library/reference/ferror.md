---
title: "ferror | Microsoft Docs"
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
  - "ferror"
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
  - "ferror"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "errores [C++], comprobar para secuencia"
  - "ferror (función)"
  - "secuencias, comprobar errores"
ms.assetid: 528a34bc-f2aa-4c3f-b89a-5b148e6864f7
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ferror
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Pruebas de un error en una secuencia.  
  
## Sintaxis  
  
```  
int ferror(   
   FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 Si se ha producido ningún error en `stream`, `ferror` devuelve 0.  De lo contrario, devuelve un valor distinto de cero.  Si la secuencia está `NULL`, `ferror` invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, conjuntos `errno` de esta función a `EINVAL` y devuelven 0.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
## Comentarios  
 Las pruebas rutinarias de `ferror` \(se implementa como una función como macro\) para un error de lectura o escritura en el archivo asociado a `stream`.  Si se produce un error, el mensaje de error para la secuencia sigue siendo conjunto hasta que la secuencia cerrada o rebobinada, o hasta que `clearerr` se denomina con ella.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`ferror`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [feof](../../c-runtime-library/reference/feof.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de errores](../../c-runtime-library/error-handling-crt.md)   
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [\_eof](../../c-runtime-library/reference/eof.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [perror, \_wperror](../../c-runtime-library/reference/perror-wperror.md)