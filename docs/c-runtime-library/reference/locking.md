---
title: _locking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _locking
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
- _locking
dev_langs:
- C++
helpviewer_keywords:
- locking function
- bytes [C++], locking file
- files [C++], locking bytes
- files [C++], locking
- _locking function
ms.assetid: 099aaac1-d4ca-4827-aed6-24dff9844150
caps.latest.revision: 19
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
ms.openlocfilehash: 7789a1634f5ee87d54d6b9f2aadbc720819f31ef
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="locking"></a>_locking
Bloquea o desbloquea los bytes de un archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      int _locking(  
   int fd,  
   int mode,  
   long nbytes   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fd`  
 Descriptor del archivo.  
  
 *mode*  
 Acción de bloqueo que se va a realizar.  
  
 *nbytes*  
 Número de bytes que se van a bloquear.  
  
## <a name="return-value"></a>Valor devuelto  
 `_locking` devuelve 0 si es correcto. Un valor devuelto de -1 indica un error, en cuyo caso [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se establece en uno de los siguientes valores.  
  
 `EACCES`  
 Infracción de bloqueo (archivo ya bloqueado o desbloqueado).  
  
 `EBADF`  
 Descriptor de archivo no válido.  
  
 `EDEADLOCK`  
 Infracción de bloqueo. Se devuelve cuando se especifica la marca `_LK_LOCK` o `_LK_RLCK` y el archivo no se puede bloquear después de 10 intentos.  
  
 `EINVAL`  
 Se pasó un argumento no válido a `_locking`.  
  
 Si el error se debe a un parámetro incorrecto, como un descriptor de archivo no válido, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_locking` bloquea o desbloquea *nbytes* bytes del archivo especificado por `fd`. El bloqueo de bytes en un archivo impide que otros procesos obtengan acceso a dichos bytes. Todos los bloqueos o desbloqueos comienzan en la posición actual del puntero de archivo y continúan durante los próximos *nbytes* bytes. Se pueden bloquear bytes después del final del archivo.  
  
 *mode* debe ser una de las siguientes constantes de manifiesto, que se definen en Locking.h.  
  
 `_LK_LOCK`  
 Bloquea los bytes especificados. Si no se pueden bloquear los bytes, el programa lo vuelve a intentar inmediatamente después de 1 segundo. Si después de 10 intentos no se pueden bloquear los bytes, la constante devuelve un error.  
  
 `_LK_NBLCK`  
 Bloquea los bytes especificados. Si no se pueden bloquear los bytes, la constante devuelve un error.  
  
 `_LK_NBRLCK`  
 Igual a `_LK_NBLCK`.  
  
 `_LK_RLCK`  
 Igual a `_LK_LOCK`.  
  
 `_LK_UNLCK`  
 Desbloquea los bytes especificados, que deben haberse bloqueado anteriormente.  
  
 Se pueden bloquear varias regiones de un archivo que no se superponen. Para desbloquear una región, primero debe haberse bloqueado. `_locking` no combina regiones adyacentes; si dos regiones bloqueadas son adyacentes, cada una de ellas debe desbloquearse por separado. Las regiones deberían bloquearse solo brevemente y deberían desbloquearse antes de cerrar un archivo o de salir del programa.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_locking`|\<io.h> y \<sys/locking.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_locking.c  
/* This program opens a file with sharing. It locks  
 * some bytes before reading them, then unlocks them. Note that the  
 * program works correctly only if the file exists.  
 */  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <sys/locking.h>  
#include <share.h>  
#include <fcntl.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <io.h>  
  
int main( void )  
{  
   int  fh, numread;  
   char buffer[40];  
  
   /* Quit if can't open file or system doesn't   
    * support sharing.   
    */  
   errno_t err = _sopen_s( &fh, "crt_locking.txt", _O_RDONLY, _SH_DENYNO,   
                          _S_IREAD | _S_IWRITE );  
   printf( "%d %d\n", err, fh );  
   if( err != 0 )  
      exit( 1 );  
  
   /* Lock some bytes and read them. Then unlock. */  
   if( _locking( fh, LK_NBLCK, 30L ) != -1 )  
   {  
      long lseek_ret;  
      printf( "No one can change these bytes while I'm reading them\n" );  
      numread = _read( fh, buffer, 30 );  
      buffer[30] = '\0';  
      printf( "%d bytes read: %.30s\n", numread, buffer );  
      lseek_ret = _lseek( fh, 0L, SEEK_SET );  
      _locking( fh, LK_UNLCK, 30L );  
      printf( "Now I'm done. Do what you will with them\n" );  
   }  
   else  
      perror( "Locking failed\n" );  
  
   _close( fh );  
}  
```  
  
## <a name="input-crtlockingtxt"></a>Entrada: crt_locking.txt  
  
```  
The first thirty bytes of this file will be locked.  
```  
  
## <a name="sample-output"></a>Resultados del ejemplo  
  
```  
No one can change these bytes while I'm reading them  
30 bytes read: The first thirty bytes of this  
Now I'm done. Do what you will with them  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)
