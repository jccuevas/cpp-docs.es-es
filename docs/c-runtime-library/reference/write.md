---
title: _write | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _write
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
apitype: DLLExport
f1_keywords:
- _write
dev_langs:
- C++
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8bf8fcbfc0d66f89667d36baeb75252e7d92abc5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="write"></a>_write
Escribe datos en un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _write(  
   int fd,  
   const void *buffer,  
   unsigned int count   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor de archivo del archivo en el que se van a escribir datos.  
  
 `buffer`  
 Datos que se van a escribir.  
  
 `count`  
 Número de bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, `_write` devuelve el número de bytes escrito realmente. Si el espacio real que queda en el disco es inferior al tamaño del búfer que la función trata de escribir en el disco, se produce un error en `_write` y no se vuelca ningún contenido del búfer en el disco. Un valor devuelto de -1 indica un error. Si se pasan parámetros no válidos, esta función invoca al controlador de parámetros no válidos, como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve -1 y `errno` se establece en uno de tres valores: `EBADF`, que indica que el descriptor de archivo no es válido o que el archivo no está abierto para escritura; `ENOSPC`, que pone de manifiesto que no hay espacio suficiente en el dispositivo para realizar la operación; o `EINVAL`, que señala que `buffer` es un puntero nulo o que se ha pasado un `count` impar de bytes para su escritura en un archivo en modo Unicode.  
  
 Para obtener más información sobre estos y otros códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 Si el archivo se abre en modo de texto, se reemplaza cada carácter de avance de línea con un retorno de carro - par de avance de línea en la salida. Este reemplazo no tiene efecto alguno en el valor devuelto.  
  
 Cuando el archivo se abre en un modo de conversión Unicode (por ejemplo, si `fd` se abre con `_open` o `_sopen` y un parámetro de modo que incluye `_O_WTEXT`, `_O_U16TEXT` o `_O_U8TEXT`; si se abre mediante `fopen` y un parámetro de modo que incluye `ccs=UNICODE`, `ccs=UTF-16LE` o `ccs=UTF-8`; o si el modo se cambia a un modo de conversión Unicode mediante `_setmode`), `buffer` se interpreta como un puntero a una matriz de `wchar_t` que contiene datos **UTF-16**. Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.  
  
## <a name="remarks"></a>Comentarios  
 La función `_write` escribe `count` bytes desde el `buffer` al archivo asociado a `fd`. La operación de escritura se inicia en la posición actual del puntero de archivo (si existe) asociado al archivo en cuestión. Si el archivo se abre para anexarlo, la operación comenzará en el final actual del archivo. Tras la operación de escritura, el puntero de archivo se incrementará según el número de bytes escrito realmente.  
  
 Cuando se escribe en archivos abiertos en modo de texto, `_write` trata un carácter CTRL+Z como el final de archivo lógico. Si se escribe en un dispositivo, `_write` trata un carácter CTRL+Z en el búfer como un terminador de salida.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_write`|\<io.h>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt__write.c  
//   
// This program opens a file for output and uses _write to write  
// some bytes to the file.  
  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <errno.h>  
#include <share.h>  
  
char buffer[] = "This is a test of '_write' function";  
  
int main( void )  
{  
   int         fileHandle = 0;  
   unsigned    bytesWritten = 0;  
  
   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,  
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )  
      return -1;  
  
   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )  
   {  
      switch(errno)  
      {  
         case EBADF:  
            perror("Bad file descriptor!");  
            break;  
         case ENOSPC:  
            perror("No space left on device!");  
            break;  
         case EINVAL:  
            perror("Invalid parameter: buffer was NULL!");  
            break;  
         default:  
            // An unrelated error occured   
            perror("Unexpected error!");  
      }  
   }  
   else  
   {  
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );  
   }  
   _close( fileHandle );  
}  
```  
  
```Output  
Wrote 36 bytes to file.  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [fwrite](../../c-runtime-library/reference/fwrite.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_read](../../c-runtime-library/reference/read.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)