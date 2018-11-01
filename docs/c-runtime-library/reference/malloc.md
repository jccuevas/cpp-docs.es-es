---
title: malloc
ms.date: 11/04/2016
apiname:
- malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: e6a007fb6f089ebf1c9f5fc9ce59cbcbf0b13888
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520372"
---
# <a name="malloc"></a>malloc

Asigna bloques de memoria.

## <a name="syntax"></a>Sintaxis

```C
void *malloc(
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Bytes para asignar.

## <a name="return-value"></a>Valor devuelto

**malloc** devuelve un puntero void al espacio asignado, o **NULL** si hay suficiente memoria disponible. Para devolver un puntero a un tipo distinto **void**, use un conversión de tipo en el valor devuelto. Se garantiza que el espacio de almacenamiento que apunta el valor devuelto está correctamente alineado para almacenar cualquier tipo de objeto que tenga un requisito de alineación inferior o igual al de la alineación básica. (En Visual C++, la alineación básica es la alineación necesaria para un **doble**, u 8 bytes. En el código destinado a las plataformas de 64 bits, son 16 bytes). Use [_aligned_malloc](aligned-malloc.md) para asignar el almacenamiento para los objetos que tienen un requisito de alineación mayor, por ejemplo, los tipos SSE [__m128](../../cpp/m128.md) y **__m256**y tipos declaradas mediante `__declspec(align( n ))` donde **n** es mayor que 8. Si *tamaño* es 0, **malloc** asigna un elemento de longitud cero en el montón y devuelve un puntero válido para ese elemento. Compruebe siempre el valor devuelto de **malloc**, incluso si la cantidad de memoria solicitada es pequeña.

## <a name="remarks"></a>Comentarios

El **malloc** función asigna un bloque de memoria de al menos *tamaño* bytes. El bloque puede ser mayor que *tamaño* bytes debido al espacio necesario para obtener información de alineación y el mantenimiento.

**malloc** establece **errno** a **ENOMEM** si se produce un error en una asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

El código de inicio usa **malloc** para asignar el almacenamiento para el **_environ**, *envp*, y *argv* variables. Las siguientes funciones y sus homólogos de caracteres anchos también llaman **malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec (funciones)](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[system](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[gets](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

La función [_set_new_mode](set-new-mode.md) de C++ establece el nuevo modo de controlador para **malloc**. El nuevo modo de controlador indica si, en caso de error, **malloc** consiste en llamar a la rutina del nuevo controlador según lo establecido por [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error para asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **malloc** no puede asignar memoria, **malloc** llame a la rutina del nuevo controlador de la misma forma en que el **nuevo** operador Cuando se produce un error por la misma razón. Para invalidar el valor predeterminado, llame a `_set_new_mode(1)` temprano en el programa o vincúlelo con NEWMODE. OBJ (consulte [opciones de vínculo](../../c-runtime-library/link-options.md)).

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas de tiempo de ejecución de C, **malloc** se resuelve como [_malloc_dbg](malloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** está marcado como `__declspec(noalias)` y `__declspec(restrict)`; Esto significa que se garantiza que la función no se puede modificar las variables globales y que el puntero devuelto no es un alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**malloc**|\<stdlib.h> y \<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_malloc.c
// This program allocates memory with
// malloc, then frees the memory with free.

#include <stdlib.h>   // For _MAX_PATH definition
#include <stdio.h>
#include <malloc.h>

int main( void )
{
   char *string;

   // Allocate space for a path name
   string = malloc( _MAX_PATH );

   // In a C++ file, explicitly cast malloc's return.  For example,
   // string = (char *)malloc( _MAX_PATH );

   if( string == NULL )
      printf( "Insufficient memory available\n" );
   else
   {
      printf( "Memory space allocated for path name\n" );
      free( string );
      printf( "Memory freed\n" );
   }
}
```

```Output
Memory space allocated for path name
Memory freed
```

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
