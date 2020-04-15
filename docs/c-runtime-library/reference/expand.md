---
title: _expand
ms.date: 4/2/2020
api_name:
- _expand
- _o__expand
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 7f2a789bc5f475411808bc00a4280b7573b67cf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347560"
---
# <a name="_expand"></a>_expand

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

*Tamaño*<br/>
Nuevo tamaño en bytes.

## <a name="return-value"></a>Valor devuelto

**_expand** devuelve un puntero void al bloque de memoria reasignado. **_expand**, a diferencia de **realloc**, no puede mover un bloque para cambiar su tamaño. Por lo tanto, si hay suficiente memoria disponible para expandir el bloque sin moverlo, el parámetro *memblock* para **_expand** es el mismo que el valor devuelto.

**_expand** devuelve **NULL** cuando se detecta un error durante su operación. Por ejemplo, si se utiliza **_expand** para reducir un bloque de memoria, podría detectar daños en el montón de bloques pequeños o un puntero de bloque no válido y devolver **NULL**.

Si no hay suficiente memoria disponible para expandir el bloque al tamaño especificado sin moverlo, la función devuelve **NULL**. **_expand** nunca devuelve un bloque expandido a un tamaño menor del solicitado. Si se produce un error, **errno** indica la naturaleza del error. Para obtener más información acerca de **errno**, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para comprobar el nuevo tamaño del elemento, utilice **_msize**. Para obtener un puntero a un tipo distinto de **void**, utilice una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Observaciones

La función **_expand** cambia el tamaño de un bloque de memoria asignado anteriormente al intentar expandir o contraer el bloque sin mover su ubicación en el montón. El parámetro *memblock* apunta al principio del bloque. El parámetro *size* proporciona el nuevo tamaño del bloque, en bytes. El contenido del bloque queda sin modificar hasta el menor de los tamaños nuevos y antiguos. *memblock* no debe ser un bloque que ha sido liberado.

> [!NOTE]
> En plataformas de 64 bits, es posible **que _expand** no contrate el bloque si el nuevo tamaño es menor que el tamaño actual; en particular, si el bloque tenía un tamaño inferior a 16K y, por lo tanto, se asignaba en el montón de baja fragmentación, **_expand** deja el bloque sin cambios y devuelve *memblock*.

Cuando la aplicación está vinculada con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **_expand** se resuelve [en _expand_dbg](expand-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

Esta función valida sus parámetros. Si *memblock* es un puntero nulo, esta función invoca un controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece **en EINVAL** y la función devuelve **NULL**. Si *size* es mayor que **_HEAP_MAXREQ**, **errno** se establece en **ENOMEM** y la función devuelve **NULL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Asignación de memoria](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[Gratis](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
