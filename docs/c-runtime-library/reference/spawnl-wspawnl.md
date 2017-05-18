---
title: _spawnl, _wspawnl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wspawnl
- _spawnl
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
- spawnl
- wspawnl
- _wspawnl
- _spawnl
dev_langs:
- C++
helpviewer_keywords:
- spawnl function
- processes, creating
- _spawnl function
- processes, executing new
- _wspawnl function
- wspawnl function
- process creation
ms.assetid: dd4584c9-7173-4fc5-b93a-6e7d3c2316d7
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 91000dba7d7fe1ff505eee30d60bc60936ef4971
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="spawnl-wspawnl"></a>_spawnl, _wspawnl
Crea y ejecuta un nuevo proceso.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
intptr_t _spawnl(  
   int mode,  
   const char *cmdname,  
   const char *arg0,  
   const char *arg1,  
   ... const char *argn,  
   NULL   
);  
intptr_t _wspawnl(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   const wchar_t *arg1,  
   ... const wchar_t *argn,  
   NULL   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mode`  
 Modo de ejecución para el proceso de llamada.  
  
 `cmdname`  
 Ruta de acceso del archivo que se va a ejecutar.  
  
 `arg0, arg1, ... argn`  
 Lista de punteros a argumentos. El argumento `arg0` suele ser un puntero a `cmdname`. Los argumentos `arg1` a `argn` son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. Después de `argn`, debe haber un puntero `NULL` para marcar el final de la lista de argumentos.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor devuelto de un `_spawnl` o `_wspawnl` sincrónico (`_P_WAIT` especificado para `mode`) es el estado de salida del nuevo proceso. El valor devuelto de un `_spawnl` o `_wspawnl` asincrónico (`_P_NOWAIT` o `_P_NOWAITO` especificado para `mode`) es el identificador de proceso. El estado de salida es 0 si el proceso finalizó normalmente. Puede establecer el estado de salida en un valor distinto de cero si el proceso generado llama específicamente a la rutina `exit` con un argumento distinto de cero. Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal con una anulación o una interrupción. Un valor devuelto de -1 indica un error (el nuevo proceso no se inicia). En este caso, `errno` se establece en uno de los valores siguientes.  
  
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
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Estas funciones validan sus parámetros. Si `cmdname` o `arg0` es una cadena vacía o un puntero nulo, se invoca el controlador de parámetro no válido, como se describe en [Parameter Validation](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL`y devuelven -1. No se genera ningún proceso nuevo.  
  
## <a name="remarks"></a>Comentarios  
 Cada una de estas funciones crea y ejecuta un proceso nuevo, pasando cada argumento de la línea de comandos como parámetro independiente.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_spawnl`|\<process.h>|  
|`_wspawnl`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
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
