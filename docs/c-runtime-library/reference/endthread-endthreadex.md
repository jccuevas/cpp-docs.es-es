---
title: "_endthread, _endthreadex | Microsoft Docs"
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
  - "_endthread"
  - "_endthreadex"
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
  - "_endthread"
  - "endthreadex"
  - "_endthreadex"
  - "endthread"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_endthread (función)"
  - "endthread (función)"
  - "terminar subprocesos"
  - "endthreadex (función)"
  - "_endthreadex (función)"
  - "subprocesamiento [C++], terminar subprocesos"
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _endthread, _endthreadex
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Termina un subproceso; `_endthread` termina un subproceso creado por `_beginthread` y `_endthreadex` termina un subproceso creado por `_beginthreadex`.  
  
## Sintaxis  
  
```  
void _endthread( void );  
void _endthreadex(   
   unsigned retval   
);  
```  
  
#### Parámetros  
 `retval`  
 Código de salida del subproceso.  
  
## Comentarios  
 Puede llamar a `_endthread` o `_endthreadex` explícitamente para terminar un subproceso; sin embargo, se llama a `_endthread` o `_endthreadex` automáticamente cuando el subproceso vuelve de la rutina que se pasa como parámetro a `_beginthread` o `_beginthreadex`. Si se finaliza un subproceso con una llamada a `endthread` o las ayudas de `_endthreadex`, se garantiza la recuperación correcta de los recursos que se asignan para el subproceso.  
  
> [!NOTE]
>  En el caso de un archivo ejecutable vinculado a Libcmt.lib, no llame a la API [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659.aspx) de Win32 porque esto impide que el sistema en tiempo de ejecución reclame los recursos asignados.`_endthread` y `_endthreadex` recuperan los recursos de subprocesos asignados y después llaman a `ExitThread`.  
  
 `_endthread` cierra automáticamente el identificador del subproceso. Este comportamiento es distinto que el de la API `ExitThread` de Win32. Por consiguiente, cuando use `_beginthread` y `_endthread`, no cierre el identificador de subproceso de forma explícita llamando a la API [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211.aspx) de Win32.  
  
 Al igual que la API `ExitThread` de Win32, `_endthreadex` no cierra el identificador del subproceso. Por consiguiente, al usar `_beginthreadex` y `_endthreadex`, debe cerrar el identificador de subproceso llamando a la API `CloseHandle` de Win32.  
  
> [!NOTE]
>  `_endthread` y `_endthreadex` hacen que no se llame a los destructores de C\+\+ pendientes en el subproceso.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_endthread`|\<process.h\>|  
|`_endthreadex`|\<process.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Solo las versiones de multiproceso de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Consulte el ejemplo de [\_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_beginthread, \_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)