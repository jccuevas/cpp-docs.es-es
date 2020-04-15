---
title: perror, _wperror
ms.date: 4/2/2020
api_name:
- _wperror
- perror
- _o__wperror
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 0c50e77863b4b136ac59b6f79d8e529691032609
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338533"
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

*Mensaje*<br/>
Mensaje de cadena para imprimir.

## <a name="remarks"></a>Observaciones

La función **perror** imprime un mensaje de error en **stderr**. **_wperror** es una versión de caracteres anchos de **_perror;** el argumento *de mensaje* que se va a **_wperror** es una cadena de caracteres anchos. **_wperror** y **_perror** comportarse de forma idéntica de lo contrario.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**perror**|**perror**|**_wperror**|

*mensaje* se imprime primero, seguido de dos puntos, luego por el mensaje de error del sistema para la última llamada de biblioteca que produjo el error y, finalmente, por un carácter de nueva línea. Si *message* es un puntero nulo o un puntero a una cadena nula, **perror** imprime solo el mensaje de error del sistema.

El número de error se almacena en la variable [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (definida en ERRNO.H). Se obtiene acceso a los mensajes de error del sistema a través de la variable [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), que es una matriz de mensajes ordenados por número de error. **perror** imprime el mensaje de error adecuado utilizando el valor **errno** como índice para **_sys_errlist**. El valor de la variable [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) se define como el número máximo de elementos de la matriz **_sys_errlist.**

Para obtener resultados precisos, llame a **perror** inmediatamente después de que una rutina de biblioteca vuelva con un error. De lo contrario, las llamadas posteriores pueden sobrescribir el valor **errno.**

En el sistema operativo Windows, algunos valores **errno** enumerados en ERRNO. H no se utilizan. Estos valores están reservados para su uso en el sistema operativo UNIX. Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener una lista de los valores **errno** utilizados por el sistema operativo Windows. **perror** imprime una cadena vacía para cualquier valor **errno** no utilizado por estas plataformas.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**perror**|\<stdio.h> o \<stdlib.h>|
|**_wperror**|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
