---
title: _dup, _dup2
ms.date: 4/2/2020
api_name:
- _dup
- _dup2
- _o__dup
- _o__dup2
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _dup2
- _dup
helpviewer_keywords:
- _dup2 function
- dup function
- file handles [C++], duplicating
- file handles [C++], reassigning
- dup2 function
- _dup function
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
ms.openlocfilehash: 239f857bb40c9609cb6f7ff373295a7a1f8523a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348111"
---
# <a name="_dup-_dup2"></a>_dup, _dup2

Crea un segundo descriptor de archivo para un archivo abierto (**_dup**), o reasigna un descriptor de archivo (**_dup2**).

## <a name="syntax"></a>Sintaxis

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parámetros

*fd*, *fd1*<br/>
Descriptores de archivo que hacen referencia al archivo abierto.

*fd2*<br/>
Cualquier descriptor de archivo.

## <a name="return-value"></a>Valor devuelto

**_dup** devuelve un nuevo descriptor de archivo. **_dup2** devuelve 0 para indicar que se ha realizado correctamente. Si se produce un error, cada función devuelve -1 y establece **errno** en **EBADF** si el descriptor de archivo no es válido o en **EMFILE** si no hay más descriptores de archivo disponibles. En el caso de un descriptor de archivo no válido, la función invoca también al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Las funciones **_dup** y **_dup2** asocian un segundo descriptor de archivo con un archivo abierto actualmente. Estas funciones se pueden utilizar para asociar un descriptor de archivo predefinido, como el de **stdout**, con un archivo diferente. Las operaciones en el archivo se pueden realizar con cualquiera de los dos descriptores de archivo. El tipo de acceso permitido al archivo no se ve afectado por la creación de un nuevo descriptor. **_dup** devuelve el siguiente descriptor de archivo disponible para el archivo especificado. **_dup2** fuerza *fd2* para hacer referencia al mismo archivo que *fd1*. Si *fd2* está asociado a un archivo abierto en el momento de la llamada, ese archivo se cierra.

Tanto **_dup** como **_dup2** aceptan descriptores de archivo como parámetros. Para pasar una`FILE *`secuencia ( ) a cualquiera de estas funciones, utilice [_fileno](fileno.md). La rutina **fileno** devuelve el descriptor de archivo asociado actualmente a la secuencia dada. En el ejemplo siguiente se muestra cómo `FILE *` asociar **stderr** (definido como en Stdio.h) con un descriptor de archivo:

```C
int cstderr = _dup( _fileno( stderr ));
```

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

La consola no se admite en aplicaciones de la Plataforma universal de Windows (UWP). Los identificadores de secuencia estándar asociados a la consola, **stdin,** **stdout**y **stderr**, deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_dup.c
// This program uses the variable old to save
// the original stdout. It then opens a new file named
// DataFile and forces stdout to refer to it. Finally, it
// restores stdout to its original state.

#include <io.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int old;
   FILE *DataFile;

   old = _dup( 1 );   // "old" now refers to "stdout"
                      // Note:  file descriptor 1 == "stdout"
   if( old == -1 )
   {
      perror( "_dup( 1 ) failure" );
      exit( 1 );
   }
   _write( old, "This goes to stdout first\n", 26 );
   if( fopen_s( &DataFile, "data", "w" ) != 0 )
   {
      puts( "Can't open file 'data'\n" );
      exit( 1 );
   }

   // stdout now refers to file "data"
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )
   {
      perror( "Can't _dup2 stdout" );
      exit( 1 );
   }
   puts( "This goes to file 'data'\n" );

   // Flush stdout stream buffer so it goes to correct file
   fflush( stdout );
   fclose( DataFile );

   // Restore original stdout
   _dup2( old, 1 );
   puts( "This goes to stdout\n" );
   puts( "The file 'data' contains:" );
   _flushall();
   system( "type data" );
}
```

```Output
This goes to stdout first
This goes to stdout

The file 'data' contains:
This goes to file 'data'
```

## <a name="see-also"></a>Consulte también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
