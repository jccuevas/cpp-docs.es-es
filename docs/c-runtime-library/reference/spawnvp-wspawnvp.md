---
title: _spawnvp, _wspawnvp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wspawnvp
- _spawnvp
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wspawnvp
- _spawnvp
- wspawnvp
dev_langs: C++
helpviewer_keywords:
- wspawnvp function
- processes, creating
- _wspawnvp function
- processes, executing new
- spawnvp function
- process creation
- _spawnvp function
ms.assetid: 8d8774ec-6ad4-4680-a5aa-440cde1e0249
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 49e51ca52f92d5df73d4ea5b5259cebbbf2c5380
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="spawnvp-wspawnvp"></a>_spawnvp, _wspawnvp
Crea un proceso y lo ejecuta.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
intptr_t _spawnvp(  
   int mode,  
   const char *cmdname,  
   const char *const *argv   
);  
intptr_t _wspawnvp(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *const *argv   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mode`  
 Modo de ejecución para llamar al proceso.  
  
 `cmdname`  
 Ruta de acceso del archivo que se va a ejecutar.  
  
 `argv`  
 Matriz de punteros a argumentos. El argumento `argv`[0] suele ser un puntero a una ruta de acceso en modo real o al nombre del programa en modo protegido; de `argv`[1] a `argv`[`n`] son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. El argumento `argv`[`n` +1] debe ser un puntero `NULL` para marcar el final de la lista de argumentos.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor devuelto de un `_spawnvp` o `_wspawnvp` sincrónico (`_P_WAIT` especificado para `mode`) es el estado de salida del nuevo proceso. El valor devuelto de un `_spawnvp` o `_wspawnvp` asincrónico (`_P_NOWAIT` o `_P_NOWAITO` especificado para `mode`) es el identificador de proceso. El estado de salida es 0 si el proceso finalizó normalmente. Puede establecer el estado de salida en un valor distinto de cero si el proceso generado usa específicamente un argumento distinto de cero para llamar a la rutina `exit` . Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal con una anulación o una interrupción. Un valor devuelto de -1 indica un error (el nuevo proceso no se inicia). En este caso, `errno` se establece en uno de los valores siguientes:  
  
 `E2BIG`  
 La lista de argumentos supera los 1024 bytes.  
  
 `EINVAL`  
 El argumento `mode` no es válido.  
  
 `ENOENT`  
 El archivo o la ruta de acceso no se encuentra.  
  
 `ENOEXEC`  
 El archivo especificado no es ejecutable o no tiene un formato de archivo ejecutable válido.  
  
 `ENOMEM`  
 Memoria insuficiente para ejecutar el nuevo proceso.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas funciones crea un proceso nuevo y lo ejecuta. Además, pasa una matriz de punteros a argumentos de la línea de comandos y usa la variable de entorno `PATH` para buscar el archivo que se va a ejecutar.  
  
 Estas funciones validan sus parámetros. Si `cmdname` o `argv` es un puntero nulo, `argv` señala a un puntero nulo o `argv[0]` es una cadena vacía, se invoca el controlador de parámetro no válido, como se describe en [Parameter Validation](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL`y devuelven -1. No se genera ningún proceso nuevo.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_spawnvp`|\<stdio.h> o \<process.h>|  
|`_wspawnvp`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [Funciones _spawn y _wspawn](../../c-runtime-library/spawn-wspawn-functions.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)   
 [_spawn, _wspawn (Funciones)](../../c-runtime-library/spawn-wspawn-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec, _wexec (Funciones)](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)