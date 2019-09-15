---
title: perror, _wperror
ms.date: 11/04/2016
api_name:
- _wperror
- perror
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: 755b638f320fcc583faecfe6aa82269e4e1b3d8f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951029"
---
# <a name="perror-_wperror"></a>perror, _wperror

Imprime un mensaje de error.

## <a name="syntax"></a>Sintaxis

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>Parámetros

*message*<br/>
Mensaje de cadena para imprimir.

## <a name="remarks"></a>Comentarios

La función **perror** imprime un mensaje de error en **stderr**. **_wperror** es una versión con caracteres anchos de **_perror**; el argumento de *mensaje* para **_wperror** es una cadena de caracteres anchos. **_wperror** y **_perror** se comportan de manera idéntica.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

primero se imprime el *mensaje* , seguido de un signo de dos puntos y, a continuación, el mensaje de error del sistema de la última llamada de biblioteca que generó el error y, por último, un carácter de nueva línea. Si el *mensaje* es un puntero nulo o un puntero a una cadena nula, el **perror** solo imprime el mensaje de error del sistema.

El número de error se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (definida en ERRNO.H). Se obtiene acceso a los mensajes de error del sistema a través de la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), que es una matriz de mensajes ordenados por número de error. **perror** imprime el mensaje de error correspondiente usando el valor **errno** como índice de **_sys_errlist**. El valor de la variable [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se define como el número máximo de elementos de la matriz **_sys_errlist** .

Para obtener resultados precisos, llame a **perror** inmediatamente después de que una rutina de biblioteca devuelva un error. De lo contrario, las llamadas subsiguientes pueden sobrescribir el valor **errno** .

En el sistema operativo Windows, algunos valores **errno** enumerados en errno. H no se usan. Estos valores están reservados para su uso en el sistema operativo UNIX. Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener una lista de los valores **errno** utilizados por el sistema operativo Windows. **perror** imprime una cadena vacía para cualquier valor **errno** no utilizado por estas plataformas.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**perror**|\<stdio.h> o \<stdlib.h>|
|**_wperror**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
