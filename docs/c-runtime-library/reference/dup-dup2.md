---
title: _dup, _dup2
ms.date: 11/04/2016
api_name:
- _dup
- _dup2
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
ms.openlocfilehash: da47d6f040b62906d30107f9036ffa2a3ea05a1c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937789"
---
# <a name="_dup-_dup2"></a>_dup, _dup2

Crea un segundo descriptor de archivo para un archivo abierto ( **_dup**) o reasigna un descriptor de archivo ( **_dup2**).

## <a name="syntax"></a>Sintaxis

```C
int _dup( int fd );
int _dup2( int fd1, int fd2 );
```

### <a name="parameters"></a>Parámetros

*FD*, *FD1*<br/>
Descriptores de archivo que hacen referencia al archivo abierto.

*fd2*<br/>
Cualquier descriptor de archivo.

## <a name="return-value"></a>Valor devuelto

**_dup** devuelve un nuevo descriptor de archivo. **_dup2** devuelve 0 para indicar que la operación se ha realizado correctamente. Si se produce un error, cada función devuelve-1 y establece **errno** en **EBADF** si el descriptor de archivo no es válido o en **EMFILE** si no hay más descriptores de archivo disponibles. En el caso de un descriptor de archivo no válido, la función invoca también al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Las funciones **_dup** y **_dup2** asocian un segundo descriptor de archivo a un archivo abierto actualmente. Estas funciones se pueden usar para asociar un descriptor de archivo predefinido, como el de **stdout**, con un archivo diferente. Las operaciones en el archivo se pueden realizar con cualquiera de los dos descriptores de archivo. El tipo de acceso permitido al archivo no se ve afectado por la creación de un nuevo descriptor. **_dup** devuelve el siguiente descriptor de archivo disponible para el archivo especificado. **_dup2** fuerza a *FD2* a hacer referencia al mismo archivo como *FD1*. Si *FD2* está asociado a un archivo abierto en el momento de la llamada, dicho archivo se cierra.

Tanto **_dup** como **_dup2** aceptan descriptores de archivo como parámetros. Para pasar una secuencia (`FILE *`) a cualquiera de estas funciones, use [_fileno](fileno.md). La rutina **fileno** devuelve el descriptor de archivo asociado actualmente a la secuencia especificada. En el ejemplo siguiente se muestra cómo asociar **stderr** ( `FILE *` definido como en stdio. h) con un descriptor de archivo:

```C
int cstderr = _dup( _fileno( stderr ));
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_dup**|\<io.h>|
|**_dup2**|\<io.h>|

La consola no se admite en aplicaciones de Plataforma universal de Windows (UWP). Los identificadores de flujo estándar que están asociados a la consola, **stdin**, **stdout**y **stderr**deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
