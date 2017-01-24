---
title: "_pclose | Microsoft Docs"
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
  - "_pclose"
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
  - "_pclose"
  - "pclose"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_pclose (función)"
  - "pclose (función)"
  - "canalizaciones, cerrar"
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _pclose
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Espera un nuevo procesador de comandos y cierra el flujo en la canalización asociada.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
  
      int _pclose(  
FILE *stream   
);  
```  
  
#### Parámetros  
 `stream`  
 Valor devuelto de la llamada anterior a `_popen`.  
  
## Valor devuelto  
 Devuelve el estado de salida del procesador de comandos que cierra el flujo o – 1 si se produce un error.  El formato del valor devuelto es el mismo que el de `_cwait`, excepto que se intercambian los bytes de orden inferior y de orden superior.  Si el flujo es **NULL**, `_pclose` establece `errno` en `EINVAL` y devuelve \-1.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `_pclose` busca el identificador de proceso del procesador de comandos \(Cmd.exe\) iniciado por la llamada de `_popen` asociada, ejecuta una llamada de [\_cwait](../../c-runtime-library/reference/cwait.md) en el nuevo procesador de comandos y cierra el flujo en la canalización asociada.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_pclose`|\<stdio.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_pipe](../../c-runtime-library/reference/pipe.md)   
 [\_popen, \_wpopen](../../c-runtime-library/reference/popen-wpopen.md)