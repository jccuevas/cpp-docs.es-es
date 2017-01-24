---
title: "_execvpe, _wexecvpe | Microsoft Docs"
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
  - "_execvpe"
  - "_wexecvpe"
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
  - "wexecvpe"
  - "execvpe"
  - "_wexecvpe"
  - "_execvpe"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_execvpe (función)"
  - "_wexecvpe (función)"
  - "execvpe (función)"
  - "wexecvpe (función)"
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _execvpe, _wexecvpe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Carga y ejecuta nuevos procesos secundarios.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
intptr_t _execvpe(   
   const char *cmdname,  
   const char *const *argv,  
   const char *const *envp   
);  
intptr_t _wexecvpe(   
   const wchar_t *cmdname,  
   const wchar_t *const *argv,  
   const wchar_t *const *envp   
);  
```  
  
#### Parámetros  
 `cmdname`  
 Ruta de acceso del archivo que se va a ejecutar.  
  
 `argv`  
 Matriz de punteros a parámetros.  
  
 `envp`  
 Matriz de punteros a la configuración del entorno.  
  
## Valor devuelto  
 Si se ejecutan correctamente, estas funciones no vuelven al proceso de llamada.  Un valor devuelto de –1 indica un error, en cuyo caso se establece la variable global `errno`.  
  
|Valor de `errno`|Descripción|  
|----------------------|-----------------|  
|`E2BIG`|El espacio necesario para los argumentos y la configuración de entorno supera los 32 KB.|  
|`EACCES`|El archivo especificado tiene un bloqueo o una infracción de uso compartido.|  
|`EMFILE`|Hay demasiados archivos abiertos.  \(Se debe abrir el archivo especificado para determinar si es ejecutable\).|  
|`ENOENT`|No se encuentra el archivo o la ruta de acceso.|  
|`ENOEXEC`|El archivo especificado no es ejecutable o tiene un formato de archivo ejecutable no válido.|  
|`ENOMEM`|Memoria insuficiente para ejecutar el nuevo proceso; la memoria disponible se ha dañado o existe un bloque no válido que indica que el proceso de llamada no se asignó correctamente.|  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cada una de estas funciones carga y ejecuta un proceso nuevo, pasando una matriz de punteros a los argumentos de la línea de comandos y una matriz de punteros a la configuración del entorno.  Estas funciones usan la variable de entorno `PATH` para buscar el archivo que se va a ejecutar.  
  
 Las funciones `_execvpe` validan sus parámetros.  Si `cmdname` es un puntero nulo, o si `argv` es un puntero nulo, un puntero a una matriz vacía, o un puntero a una matriz que contiene una cadena vacía como primer argumento, estas funciones invocan el controlador de parámetros no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  No se inicia ningún proceso.  
  
## Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|-------------|--------------------------|-------------------------|  
|`_execvpe`|\<process.h\>|\<errno.h\>|  
|`_wexecvpe`|\<process.h\> o \<wchar.h\>|\<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [\_exec, \_wexec \(Funciones\)](../../c-runtime-library/exec-wexec-functions.md).  
  
## Equivalente en .NET Framework  
  
-   [Clase System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [Clase System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_exec, \_wexec \(Funciones\)](../../c-runtime-library/exec-wexec-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit, \_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn, \_wspawn \(Funciones\)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, \_wsystem](../../c-runtime-library/reference/system-wsystem.md)