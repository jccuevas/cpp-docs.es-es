---
title: _fileno | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fileno
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
- _fileno
dev_langs:
- C++
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d0ce17b75ea74154121549209aed94b0a3affea
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="fileno"></a>_fileno
Obtener el descriptor de archivo asociado a un flujo  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _fileno(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
## <a name="return-value"></a>Valor devuelto  
 `_fileno` devuelve el descriptor de archivo. No se devuelve ningún error. El resultado es indefinido si `stream` no especifica un archivo abierto. Si la secuencia es `NULL`, `_fileno` invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece `errno` en `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
> [!NOTE]
>  Si `stdout` o `stderr` no están asociados a un flujo de salida (por ejemplo, en una aplicación Windows sin ventana de consola), el descriptor de archivo que se devuelve es -2. En versiones anteriores, el descriptor de archivo devuelto era -1. Este cambio permite que las aplicaciones distingan esta condición de un error.  
  
## <a name="remarks"></a>Comentarios  
 La rutina `_fileno` devuelve el descriptor de archivo asociado actualmente a `stream`. Esta rutina se implementa como función y como macro. Para obtener información sobre cómo elegir una implementación, consulte [Elegir entre funciones y macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_fileno`|\<stdio.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_fileno.c  
// This program uses _fileno to obtain  
// the file descriptor for some standard C streams.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );  
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );  
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );  
}  
```  
  
```Output  
The file descriptor for stdin is 0  
The file descriptor for stdout is 1  
The file descriptor for stderr is 2  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [_fdopen, _wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [_filelength, _filelengthi64](../../c-runtime-library/reference/filelength-filelengthi64.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)