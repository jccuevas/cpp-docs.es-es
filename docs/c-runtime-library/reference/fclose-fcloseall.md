---
title: fclose, _fcloseall | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fclose
- _fcloseall
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fclose
- _fcloseall
dev_langs:
- C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 46b9086e4c75a699acec47e3b6b68ba7bcc231cf
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="fclose-fcloseall"></a>fclose, _fcloseall
Cierra una secuencia (`fclose`) o cierra todas las secuencias abiertas (`_fcloseall`).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fclose(   
   FILE *stream   
);  
int _fcloseall( void );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura `FILE` .  
  
## <a name="return-value"></a>Valor devuelto  
 `fclose` devuelve 0 si la secuencia se cierra correctamente. `_fcloseall` devuelve el número total de secuencias cerradas. Ambas funciones devuelven `EOF` para indicar un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `fclose` cierra `stream`. Si `stream` es `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `fclose` establece `errno` en `EINVAL` y devuelve `EOF`. Se recomienda comprobar siempre el puntero `stream` antes de llamar a esta función.  
  
 Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.  
  
 La función `_fcloseall` cierra todas las secuencias excepto `stdin`, `stdout`, `stderr` (y en MS-DOS, `_stdaux` y `_stdprn`). También cierra y elimina los archivos temporales creados con `tmpfile`. En ambas funciones, se vacían todos los búferes asociados a la secuencia antes de cerrarla. Los búferes asignados por el sistema se liberan cuando se cierra la secuencia. Los búferes asignados por el usuario con `setbuf` y `setvbuf` no se liberan automáticamente.  
  
 **Nota:** Cuando estas funciones se usan para cerrar una secuencia, se cierran el descriptor de archivo subyacente y el identificador de archivos del SO (o socket), además de la secuencia. Por consiguiente, si el archivo se ha abierto originalmente como identificador de archivos o descriptor de archivo y se cierra con `fclose`, no llame también a `_close` para cerrar el descriptor de archivo; no llame a la función `CloseHandle` de Win32 para cerrar el identificador de archivos.  
  
 `fclose` y `_fcloseall` incluyen código como protección ante interferencias de otros subprocesos. Para versiones de `fclose` sin bloqueo, consulte `_fclose_nolock`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`fclose`|\<stdio.h>|  
|`_fcloseall`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [fopen](../../c-runtime-library/reference/fopen-wfopen.md).  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_fdopen, _wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)
