---
title: "_spawnlpe, _wspawnlpe | Microsoft Docs"
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
  - "_spawnlpe"
  - "_wspawnlpe"
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
  - "api-ms-win-crt-process-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "spawnlpe"
  - "_wspawnlpe"
  - "_spawnlpe"
  - "wspawnlpe"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_spawnlpe (función)"
  - "_wspawnlpe (función)"
  - "creación de proceso"
  - "procesos, crear"
  - "procesos, ejecutar nuevos"
  - "spawnlpe (función)"
  - "wspawnlpe (función)"
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _spawnlpe, _wspawnlpe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea y ejecuta un nuevo proceso.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
intptr_t _spawnlpe(  
   int mode,  
   const char *cmdname,  
   const char *arg0,  
   const char *arg1,  
   ... const char *argn,  
   NULL,  
   const char *const *envp   
);  
intptr_t _wspawnlpe(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   const wchar_t *arg1,  
   ... const wchar_t *argn,  
   NULL,  
   const wchar_t *const *envp   
);  
```  
  
#### Parámetros  
 `mode`  
 Modo de ejecución para el proceso de llamada.  
  
 `cmdname`  
 Ruta de acceso del archivo que se va a ejecutar.  
  
 `arg0, arg1, ... argn`  
 Lista de punteros a argumentos.  El argumento `arg0` suele ser un puntero a `cmdname`.  Los argumentos `arg1` a `argn` son punteros a las cadenas de caracteres que forman la nueva lista de argumentos.  Después de `argn`, debe haber un puntero `NULL` para marcar el final de la lista de argumentos.  
  
 `envp`  
 Matriz de punteros a la configuración del entorno.  
  
## Valor devuelto  
 El valor devuelto de un `_spawnlpe` o `_wspawnlpe` sincrónico \(`_P_WAIT` especificado para `mode`\) es el estado de salida del nuevo proceso.  El valor devuelto de un `_spawnlpe` o `_wspawnlpe` asincrónico \(`_P_NOWAIT` o `_P_NOWAITO` especificado para `mode`\) es el identificador de proceso.  El estado de salida es 0 si el proceso finalizó normalmente.  Puede establecer el estado de salida en un valor distinto de cero si el proceso generado usa específicamente un argumento distinto de cero para llamar a la rutina `exit`.  Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal causado por una anulación o una interrupción.  Un valor devuelto de –1 indica un error \(el nuevo proceso no se ha iniciado\).  En este caso, `errno` se establece en uno de los valores siguientes.  
  
 `E2BIG`  
 La lista de argumentos supera los 1024 bytes.  
  
 `EINVAL`  
 El argumento `mode` no es válido.  
  
 `ENOENT`  
 El archivo o la ruta de acceso no se encuentra.  
  
 `ENOEXEC`  
 El archivo especificado no es ejecutable o tiene un formato de archivo ejecutable no válido.  
  
 `ENOMEM`  
 Memoria insuficiente para ejecutar el nuevo proceso.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cada una de estas funciones crea y ejecuta un proceso nuevo, pasa cada argumento de la línea de comandos como parámetro independiente y pasa una matriz de punteros a la configuración del entorno.  Estas funciones usan la variable de entorno `PATH` para buscar el archivo que se va a ejecutar.  
  
 Estas funciones validan sus parámetros.  Si `cmdname` o `arg0` es una cadena vacía o un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  No se genera ningún proceso nuevo.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_spawnlpe`|\<process.h\>|  
|`_wspawnlpe`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [\_spawn, \_wspawn \(Funciones\)](../../c-runtime-library/spawn-wspawn-functions.md).  
  
## Equivalente en .NET Framework  
  
-   [Clase System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [Clase System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_spawn, \_wspawn \(Funciones\)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec, \_wexec \(Funciones\)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_onexit, \_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system, \_wsystem](../../c-runtime-library/reference/system-wsystem.md)