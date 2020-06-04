---
title: malloc
ms.date: 4/2/2020
api_name:
- malloc
- _o_malloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- malloc
helpviewer_keywords:
- malloc function
- memory allocation
ms.assetid: 144fcee2-be34-4a03-bb7e-ed6d4b99eea0
ms.openlocfilehash: 4e699920f37139be40542ba91b3740cd9edef148
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917508"
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

**malloc** devuelve un puntero void al espacio asignado, o **null** si no hay suficiente memoria disponible. Para devolver un puntero a un tipo distinto de **void**, use una conversión de tipo en el valor devuelto. Se garantiza que el espacio de almacenamiento que apunta el valor devuelto está correctamente alineado para almacenar cualquier tipo de objeto que tenga un requisito de alineación inferior o igual al de la alineación básica. (En Visual C++, la alineación fundamental es la alineación necesaria para un **doble**u 8 bytes. En el código que tiene como destino las plataformas de 64 bits, es de 16 bytes). Use [_aligned_malloc](aligned-malloc.md) para asignar almacenamiento para los objetos que tienen un requisito de alineación mayor; por ejemplo, los tipos SSE [__m128](../../cpp/m128.md) y **__m256**, y los tipos que se `__declspec(align( n ))` declaran con, donde **n** es mayor que 8. Si *el tamaño* es 0, **malloc** asigna un elemento de longitud cero en el montón y devuelve un puntero válido a ese elemento. Compruebe siempre el valor devuelto de **malloc**, incluso si la cantidad de memoria solicitada es pequeña.

## <a name="remarks"></a>Observaciones

La función **malloc** asigna un bloque de memoria de al menos *el tamaño* de los bytes. El bloque puede ser mayor que el *tamaño* de los bytes debido al espacio necesario para la información de alineación y mantenimiento.

**malloc** establece **errno** en **ENOMEM** si se produce un error de asignación de memoria o si la cantidad de memoria solicitada supera **_HEAP_MAXREQ**. Para obtener información sobre este y otros códigos de error, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

El código de inicio usa **malloc** para asignar almacenamiento para las variables **_environ**, *envp*y *argv* . Las siguientes funciones y sus homólogos de caracteres anchos también llaman a **malloc**.

|||||
|-|-|-|-|
|[calloc](calloc.md)|[fscanf](fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[_getw](getw.md)|[setvbuf](setvbuf.md)|
|[_exec (funciones)](../../c-runtime-library/exec-wexec-functions.md)|[fseek](fseek-fseeki64.md)|[_popen](popen-wpopen.md)|[_spawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)|
|[fgetc](fgetc-fgetwc.md)|[fsetpos](fsetpos.md)|[printf](printf-printf-l-wprintf-wprintf-l.md)|[_strdup](strdup-wcsdup-mbsdup.md)|
|[_fgetchar](fgetc-fgetwc.md)|[_fullpath](fullpath-wfullpath.md)|[putc](putc-putwc.md)|[sistema](system-wsystem.md)|
|[fgets](fgets-fgetws.md)|[fwrite](fwrite.md)|[putchar](putc-putwc.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[getc](getc-getwc.md)|[_putenv](putenv-wputenv.md)|[ungetc](ungetc-ungetwc.md)|
|[fputc](fputc-fputwc.md)|[getchar](getc-getwc.md)|[puts](puts-putws.md)|[vfprintf](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|
|[_fputchar](fputc-fputwc.md)|[_getcwd](getcwd-wgetcwd.md)|[_putw](putw.md)|[vprintf](vprintf-vprintf-l-vwprintf-vwprintf-l.md)|
|[fputs](fputs-fputws.md)|[_getdcwd](getcwd-wgetcwd.md)|[scanf](scanf-scanf-l-wscanf-wscanf-l.md)||
|[fread](fread.md)|[Obtenga](../../c-runtime-library/gets-getws.md)|[_searchenv](searchenv-wsearchenv.md)||

La función [_set_new_mode](set-new-mode.md) de C++ establece el nuevo modo de controlador para **malloc**. El nuevo modo de controlador indica si, en caso de error, **malloc** es llamar a la rutina del nuevo controlador tal y como se establece en [_set_new_handler](set-new-handler.md). De forma predeterminada, **malloc** no llama a la rutina del nuevo controlador en caso de error al asignar memoria. Puede invalidar este comportamiento predeterminado para que, cuando **malloc** no pueda asignar memoria, **malloc** llame a la rutina del nuevo controlador de la misma manera que el operador **New** cuando se produce un error por la misma razón. Para invalidar el valor predeterminado `_set_new_mode(1)` , llame al principio en el programa o VINCÚLELO con NEWMODE. OBJ (vea [Opciones de vínculo](../../c-runtime-library/link-options.md)).

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **malloc** se resuelve como [_malloc_dbg](malloc-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, vea [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

**malloc** está marcado `__declspec(noalias)` como `__declspec(restrict)`y; Esto significa que se garantiza que la función no modifica las variables globales y que el puntero devuelto no tiene alias. Para obtener más información, consulte [noalias](../../cpp/noalias.md) y [restrict](../../cpp/restrict.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**malloc**|\<stdlib.h> y \<malloc.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[ningún](free.md)<br/>
[realloc](realloc.md)<br/>
[_aligned_malloc](aligned-malloc.md)<br/>
