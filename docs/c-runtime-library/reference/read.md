---
title: _read | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _read
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
- _read
dev_langs:
- C++
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
caps.latest.revision: 15
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
ms.openlocfilehash: 6387edb05977f90fe9fb2419a1eccb47ac0b7b43
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="read"></a>_read
Lee datos desde un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int _read(  
   int fd,  
   void *buffer,  
   unsigned int count   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor de archivo que hace referencia al archivo abierto.  
  
 *buffer*  
 Ubicación de almacenamiento de los datos.  
  
 *count*  
 Número máximo de bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 _**leer** devuelve el número de bytes leídos, que puede ser menor que *recuento* si hay menos de *recuento* bytes restante en el archivo o si el archivo se abre en modo de texto, en cuyo caso cada línea de retorno de carro fuente par (CR-LF) se reemplaza con un carácter de avance de línea única. Solo se cuenta el carácter de avance de línea en el valor devuelto. El reemplazo no afecta al puntero de archivo.  
  
 Si la función intenta leer al final del archivo, devuelve 0. Si `fd` no es válido, el archivo no se abre para su lectura o está bloqueado, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve -1 y establece `errno` en `EBADF`.  
  
 Si *buffer* es **NULL**, se invoca al controlador de parámetros no válidos. Si la ejecución puede continuar, la función devuelve -1 y `errno` se establece en `EINVAL`.  
  
 Para más información sobre este y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_read` lee un máximo de *count* bytes en *buffer* desde el archivo asociado a `fd`. La operación de lectura se inicia en la posición actual del puntero de archivo asociado al archivo en cuestión. Después de la operación de lectura, el puntero de archivo señala al siguiente carácter no leído.  
  
 Si el archivo se abrió en modo de texto, la lectura finaliza cuando `_read` encuentra un carácter CTRL+Z, que se trata como un indicador de fin de archivo. Use [_lseek](../../c-runtime-library/reference/lseek-lseeki64.md) para borrar el indicador de fin de archivo.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_read`|\<io.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_read.c  
/* This program opens a file named crt_read.txt  
 * and tries to read 60,000 bytes from  
 * that file using _read. It then displays the  
 * actual number of bytes read.  
 */  
  
#include <fcntl.h>      /* Needed only for _O_RDWR definition */  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
char buffer[60000];  
  
int main( void )  
{  
   int fh;  
   unsigned int nbytes = 60000, bytesread;  
  
   /* Open file for input: */  
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
      perror( "open failed on input file" );  
      exit( 1 );  
   }  
  
   /* Read in input: */  
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )  
      perror( "Problem reading file" );  
   else  
      printf( "Read %u bytes from file\n", bytesread );  
  
   _close( fh );  
}  
```  
  
## <a name="input-crtreadtxt"></a>Entrada: crt_read.txt  
  
```  
Line one.  
Line two.  
```  
  
## <a name="output"></a>Salida  
  
```  
Read 19 bytes from file  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_write](../../c-runtime-library/reference/write.md)
