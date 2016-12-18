---
title: "_spawnvpe, _wspawnvpe | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_spawnvpe"
  - "_wspawnvpe"
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
  - "_spawnvpe"
  - "wspawnvpe"
  - "spawnvpe"
  - "_wspawnvpe"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_spawnvpe (función)"
  - "_wspawnvpe (función)"
  - "creación de proceso"
  - "procesos, crear"
  - "procesos, ejecutar nuevos"
  - "spawnvpe (función)"
  - "wspawnvpe (función)"
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _spawnvpe, _wspawnvpe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea y ejecuta un nuevo proceso.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
intptr_t _spawnvpe(  
   int mode,  
   const char *cmdname,  
   const char *const *argv,  
   const char *const *envp   
);  
intptr_t _wspawnvpe(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *const *argv,  
   const wchar_t *const *envp   
);  
```  
  
#### Parámetros  
 `mode`  
 Modo de ejecución para el proceso de llamada  
  
 `cmdname`  
 Ruta de acceso del archivo que se va a ejecutar  
  
 `argv`  
 Matriz de punteros a argumentos.  El argumento `argv`\[0\] suele ser un puntero a una ruta de acceso en modo real o al nombre del programa en modo protegido; de `argv`\[1\] a `argv`\[`n`\] son punteros a las cadenas de caracteres que forman la nueva lista de argumentos.  El argumento `argv`\[`n` \+1\] debe ser un puntero `NULL` para marcar el final de la lista de argumentos.  
  
 `envp`  
 Matriz de punteros a la configuración del entorno  
  
## Valor devuelto  
 El valor devuelto de un `_spawnvpe` o `_wspawnvpe` sincrónico \(`_P_WAIT` especificado para `mode`\) es el estado de salida del nuevo proceso.  El valor devuelto de un `_spawnvpe` o `_wspawnvpe` asincrónico \(`_P_NOWAIT` o `_P_NOWAITO` especificado para `mode`\) es el identificador de proceso.  El estado de salida es 0 si el proceso finalizó normalmente.  Puede establecer el estado de salida en un valor distinto de cero si el proceso generado llama específicamente a la rutina `exit` con un argumento distinto de cero.  Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal con una anulación o una interrupción.  Un valor devuelto de –1 indica un error \(el nuevo proceso no se ha iniciado\).  En este caso, `errno` se establece en uno de los valores siguientes:  
  
 `E2BIG`  
 La lista de argumentos supera los 1024 bytes  
  
 `EINVAL`  
 El argumento `mode` no es válido  
  
 `ENOENT`  
 El archivo o la ruta de acceso no se encuentra  
  
 `ENOEXEC`  
 El archivo especificado no es ejecutable o no tiene un formato de archivo ejecutable válido  
  
 `ENOMEM`  
 Memoria insuficiente para ejecutar el nuevo proceso  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## Comentarios  
 Cada una de estas funciones crea y ejecuta un proceso nuevo, pasando una matriz de punteros a los argumentos de la línea de comandos y una matriz de punteros a la configuración del entorno.  Estas funciones usan la variable de entorno `PATH` para buscar el archivo que se va a ejecutar.  
  
 Estas funciones validan sus parámetros.  Si `cmdname` o `argv` es un puntero nulo, o si `argv` señala a un puntero nulo, o `argv[0]` es una cadena vacía, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  No se genera ningún proceso nuevo.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_spawnvpe`|\<stdio.h\> o \<process.h\>|  
|`_wspawnvpe`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [Funciones \_spawn y \_wspawn](../../c-runtime-library/spawn-wspawn-functions.md).  
  
## Equivalente en .NET Framework  
  
-   [Clase System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [Clase System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## Vea también  
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec, \_wexec \(Funciones\)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_onexit, \_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system, \_wsystem](../../c-runtime-library/reference/system-wsystem.md)