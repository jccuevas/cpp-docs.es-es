---
title: "_execlp, _wexeclp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wexeclp"
  - "_execlp"
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
  - "_wexeclp"
  - "wexeclp"
  - "_execlp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_execlp (función)"
  - "_wexeclp (función)"
  - "execlp (función)"
  - "wexeclp (función)"
ms.assetid: 7b179163-4bcd-4d6a-8baf-68f886791928
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _execlp, _wexeclp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Carga y ejecuta nuevos procesos secundarios.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
intptr_t _execlp(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL   
);  
intptr_t _wexeclp(   
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL   
);  
```  
  
#### Parámetros  
 `cmdname`  
 Ruta de acceso del archivo que se va a ejecutar.  
  
 `arg0`, `...``argn`  
 Lista de punteros a parámetros.  
  
## Valor devuelto  
 Si se ejecutan correctamente, estas funciones no vuelven al proceso de llamada.  Un valor devuelto de –1 indica un error, en cuyo caso se establece la variable global `errno`.  
  
|Valor de `errno`|Descripción|  
|----------------------|-----------------|  
|`E2BIG`|El espacio necesario para los argumentos y la configuración de entorno supera los 32 kB.|  
|`EACCES`|El archivo especificado tiene un bloqueo o una infracción de uso compartido.|  
|`EINVAL`|Parámetro no válido.|  
|`EMFILE`|Hay demasiados archivos abiertos \(se debe abrir el archivo especificado para determinar si es ejecutable\).|  
|`ENOENT`|No se encuentra el archivo o la ruta de acceso.|  
|`ENOEXEC`|El archivo especificado no es ejecutable o tiene un formato de archivo ejecutable no válido.|  
|`ENOMEM`|Memoria insuficiente para ejecutar el nuevo proceso; la memoria disponible se ha dañado; o existe un bloque no válido, lo que indica que el proceso de llamada no se asignó correctamente.|  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cada una de estas funciones carga y ejecuta un proceso nuevo, pasando cada argumento de la línea de comandos como parámetro independiente y usando la variable de entorno `PATH` para buscar el archivo que se va a ejecutar.  
  
 Las funciones `_execlp` validan sus parámetros.  Si `cmdname` o `arg0` es un puntero nulo o una cadena vacía, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  No se inicia ningún proceso nuevo.  
  
## Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|-------------|--------------------------|-------------------------|  
|`_execlp`|\<process.h\>|\<errno.h\>|  
|`_wexeclp`|\<process.h\> o \<wchar.h\>|\<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [Funciones \_exec y \_wexec](../../c-runtime-library/exec-wexec-functions.md).  
  
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