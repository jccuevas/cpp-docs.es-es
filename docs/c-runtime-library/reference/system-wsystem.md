---
title: "system, _wsystem | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "system"
  - "_wsystem"
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
  - "_tsystem"
  - "_wsystem"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tsystem (función)"
  - "_wsystem (función)"
  - "intérprete de comandos"
  - "comandos, ejecutar"
  - "función de sistema"
  - "tsystem (función)"
  - "wsystem (función)"
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# system, _wsystem
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ejecuta un comando.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int system(  
   const char *command   
);  
int _wsystem(  
   const wchar_t *command   
);  
```  
  
#### Parámetros  
 `command`  
 Comando que se va a ejecutar.  
  
## Valor devuelto  
 Si `command` es `NULL` y se encuentra el intérprete de comandos, devuelve un valor distinto de cero.  Si no se encuentra el intérprete de comandos, devuelve 0 y establece `errno` en `ENOENT`.  Si `command` no es `NULL`, `system` devuelve el valor devuelto por el intérprete de comandos.  Devuelve el valor 0 únicamente si el intérprete de comandos devuelve el valor 0.  Un valor devuelto de – 1 indica un error y se establece `errno` en uno de los siguientes valores:  
  
 `E2BIG`  
 La lista de argumentos \(que es dependiente del sistema\) es demasiado grande.  
  
 `ENOENT`  
 No se encuentra el intérprete de comandos.  
  
 `ENOEXEC`  
 El archivo de intérprete de comandos no se puede ejecutar porque el formato no es válido.  
  
 `ENOMEM`  
 No hay suficiente memoria disponible para ejecutar el comando, la memoria disponible se ha dañado o existe un bloque no válido que indica que el proceso que realiza la llamada no se asignó correctamente.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para más información sobre estos códigos de retorno.  
  
## Comentarios  
 La función `system` pasa `command` al intérprete de comandos, que ejecuta la cadena como un comando del sistema operativo.  `system` usa las variables de entorno `COMSPEC` y `PATH` para buscar el archivo de intérprete de comandos CMD.exe.  Si `command` es `NULL`, la función comprueba si el intérprete de comandos existe.  
  
 Debe vaciar explícitamente \(mediante `fflush` o `_flushall`\) o cerrar todos los flujos antes de llamar a `system`.  
  
 `_wsystem` es una versión con caracteres anchos de `system`; el argumento `command` para `_wsystem` es una cadena de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tsystem`|`system`|`system`|`_wsystem`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`system`|\<process.h\> o \<stdlib.h\>|  
|`_wsystem`|\<process.h\> o \<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Este ejemplo usa `system` para escribir un archivo de texto.  
  
```  
// crt_system.c  
  
#include <process.h>  
  
int main( void )  
{  
   system( "type crt_system.txt" );  
}  
```  
  
## Entrada: crt\_system.txt  
  
```  
Line one.  
Line two.  
```  
  
### Salida  
  
```  
Line one.  
Line two.  
```  
  
## Equivalente en .NET Framework  
  
-   [Clase System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
-   [Clase System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
## Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [\_exec, \_wexec \(Funciones\)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../../c-runtime-library/reference/flushall.md)   
 [\_spawn, \_wspawn \(Funciones\)](../../c-runtime-library/spawn-wspawn-functions.md)