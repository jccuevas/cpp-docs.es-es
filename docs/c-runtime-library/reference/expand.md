---
title: _expand
ms.date: 11/04/2016
apiname:
- _expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: c1606bedbb1264bddb7674c829fe456f506d6584
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335209"
---
# <a name="expand"></a>_expand

Cambia el tamaño de un bloque de memoria.

## <a name="syntax"></a>Sintaxis

```C
void *_expand(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*memblock*<br/>
Puntero al bloque de memoria asignado previamente.

*size*<br/>
Nuevo tamaño en bytes.

## <a name="return-value"></a>Valor devuelto

**_expandir** devuelve un puntero void al bloque de memoria reasignado. **_expandir**, a diferencia **realloc**, no se puede mover un bloque para cambiar su tamaño. Por lo tanto, si no hay suficiente memoria disponible para expandir el bloque sin moverlo, el *memblock* parámetro **_expand** es el mismo que el valor devuelto.

**_expandir** devuelve **NULL** cuando se detecta un error durante su funcionamiento. Por ejemplo, si **_expand** es usa para reducir un bloque de memoria, podría detectar daños en el montón en bloque pequeño o un puntero de bloque no válido y devolver **NULL**.

Si no hay suficiente memoria disponible para expandir el bloque al tamaño determinado sin moverlo, la función devuelve **NULL**. **_expandir** nunca devuelve un bloque expandido a un tamaño menor que solicitado. Si se produce un error, **errno** indica la naturaleza del error. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para comprobar el nuevo tamaño del elemento, use **_msize**. Para obtener un puntero a un tipo distinto **void**, use un conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Comentarios

El **_expand** función cambia el tamaño de un bloque de memoria asignado previamente intentando expandir o contraer el bloque sin mover su ubicación en el montón. El *memblock* parámetro apunta al principio del bloque. El *tamaño* parámetro proporciona el nuevo tamaño del bloque, en bytes. El contenido del bloque queda sin modificar hasta el menor de los tamaños nuevos y antiguos. *memblock* no debe ser un bloque que se ha liberado.

> [!NOTE]
> En las plataformas de 64 bits, **_expand** no se puede contraer el bloque si el nuevo tamaño es menor que el tamaño actual; en concreto, si el bloque era inferior a 16 KB de tamaño y, por tanto, se asigna en el montón de baja fragmentación, **_expandir**  deja el bloque sin modificar y devuelve *memblock*.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas de tiempo de ejecución de C, **_expand** se resuelve como [_expand_dbg](expand-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

Esta función valida sus parámetros. Si *memblock* es un puntero nulo, esta función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**. Si *tamaño* es mayor que **_HEAP_MAXREQ**, **errno** está establecido en **ENOMEM** y la función devuelve **NULL**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>Vea también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
