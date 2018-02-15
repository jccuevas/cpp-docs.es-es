---
title: _eof | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _eof
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
- _eof
dev_langs:
- C++
helpviewer_keywords:
- eof function
- end of file, testing for
- _eof function
- files [C++], end of
- testing, for end-of-file
- end of file
ms.assetid: 265703f4-d07e-4005-abf3-b1d0cdd9e0b0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 106f673f5058043dfe0443970e9d946315c91d6d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="eof"></a>_eof
Pruebas de fin de archivo (EOF).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _eof(   
   int fd   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia al archivo abierto.  
  
## <a name="return-value"></a>Valor devuelto  
 `_eof` devuelve 1 si la posición actual es el final del archivo, o 0 si no lo es. Un valor devuelto de -1 indica un error; en este caso, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EBADF`, que indica un descriptor de archivo no válido.  
  
## <a name="remarks"></a>Comentarios  
 La función `_eof` determina si se ha llegado al final del archivo asociado a `fd`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|--------------|---------------------|---------------------|  
|`_eof`|\<io.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_eof.c  
// This program reads data from a file  
// ten bytes at a time until the end of the  
// file is reached or an error is encountered.  
//  
#include <io.h>  
#include <fcntl.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <share.h>  
  
int main( void )  
{  
   int  fh, count, total = 0;  
   char buf[10];  
   if( _sopen_s( &fh, "crt_eof.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
        perror( "Open failed");  
        exit( 1 );  
   }  
   // Cycle until end of file reached:   
   while( !_eof( fh ) )  
   {  
      // Attempt to read in 10 bytes:   
      if( (count = _read( fh, buf, 10 )) == -1 )  
      {  
         perror( "Read error" );  
         break;  
      }  
      // Total actual bytes read   
      total += count;  
   }  
   printf( "Number of bytes read = %d\n", total );  
   _close( fh );  
}  
```  
  
## <a name="input-crteoftxt"></a>Entrada: crt_eof.txt  
  
```  
This file contains some text.  
```  
  
### <a name="output"></a>Salida  
  
```  
Number of bytes read = 29  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de errores](../../c-runtime-library/error-handling-crt.md)   
 [E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [feof](../../c-runtime-library/reference/feof.md)   
 [ferror](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror](../../c-runtime-library/reference/perror-wperror.md)