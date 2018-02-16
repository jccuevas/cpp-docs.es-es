---
title: system, _wsystem | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- system
- _wsystem
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tsystem
- _wsystem
dev_langs:
- C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3d46fd4b4df463bfce940360744a0a548652e2b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="system-wsystem"></a>system, _wsystem
Ejecuta un comando.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, consulte [funciones de CRT no admitidas en aplicaciones de la plataforma Universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int system(  
   const char *command   
);  
int _wsystem(  
   const wchar_t *command   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `command`  
 Comando que se va a ejecutar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si `command` es `NULL` y se encuentra el intérprete de comandos, devuelve un valor distinto de cero. Si no se encuentra el intérprete de comandos, devuelve 0 y establece `errno` en `ENOENT`. Si `command` no es `NULL`, `system` devuelve el valor devuelto por el intérprete de comandos. Devuelve el valor 0 únicamente si el intérprete de comandos devuelve el valor 0. Un valor devuelto de - 1 indica un error, y `errno` se establece en uno de los siguientes valores:  
  
 `E2BIG`  
 La lista de argumentos (que es dependiente del sistema) es demasiado grande.  
  
 `ENOENT`  
 No se encuentra el intérprete de comandos.  
  
 `ENOEXEC`  
 El archivo de intérprete de comandos no se puede ejecutar porque el formato no es válido.  
  
 `ENOMEM`  
 No hay suficiente memoria disponible para ejecutar el comando, la memoria disponible se ha dañado o existe un bloque no válido que indica que el proceso que realiza la llamada no se asignó correctamente.  
  
 Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos códigos de retorno.  
  
## <a name="remarks"></a>Comentarios  
 La función `system` pasa `command` al intérprete de comandos, que ejecuta la cadena como un comando del sistema operativo. `system` usa las variables de entorno `COMSPEC` y `PATH` para buscar el archivo de intérprete de comandos CMD.exe. Si `command` es `NULL`, la función comprueba si el intérprete de comandos existe.  
  
 Debe vaciar explícitamente (mediante `fflush` o `_flushall`) o cerrar todos los flujos antes de llamar a `system`.  
  
 `_wsystem` es una versión con caracteres anchos de `system`; el argumento `command` para `_wsystem` es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsystem`|`system`|`system`|`_wsystem`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`system`|\<process.h> o \<stdlib.h>|  
|`_wsystem`|\<process.h> o \<stdlib.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo usa `system` para escribir un archivo de texto.  
  
```  
// crt_system.c  
  
#include <process.h>  
  
int main( void )  
{  
   system( "type crt_system.txt" );  
}  
```  
  
## <a name="input-crtsystemtxt"></a>Entrada: crt_system.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>Salida  
  
```  
Line one.  
Line two.  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [_exec, _wexec (Funciones)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)