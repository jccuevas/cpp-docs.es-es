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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8878bb046a122b545f969dd067c37eeb97126387
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920256"
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

*size*<br/>
Nuevo tamaño en bytes.

## <a name="return-value"></a>Valor devuelto

**_expand** devuelve un puntero void al bloque de memoria reasignado. **_expand**, a diferencia de **realloc**, no puede desplace un bloque para cambiar su tamaño. Por lo tanto, si hay suficiente memoria disponible para expandir el bloque sin moverlo, el parámetro *memblock* para **_expand** es el mismo que el valor devuelto.

**_expand** devuelve **null** cuando se detecta un error durante su funcionamiento. Por ejemplo, si se usa **_expand** para reducir un bloque de memoria, podría detectar daños en el montón de bloques pequeños o en un puntero de bloque no válido y devolver **null**.

Si no hay suficiente memoria disponible para expandir el bloque al tamaño dado sin moverlo, la función devuelve **null**. **_expand** nunca devuelve un bloque expandido a un tamaño menor que el solicitado. Si se produce un error, **errno** indica la naturaleza del error. Para obtener más información acerca de **errno**, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

El valor devuelto apunta a un espacio de almacenamiento confirmado como correctamente alineado para almacenar cualquier tipo de objeto. Para comprobar el nuevo tamaño del elemento, use **_msize**. Para obtener un puntero a un tipo distinto de **void**, use una conversión de tipo en el valor devuelto.

## <a name="remarks"></a>Observaciones

La función **_expand** cambia el tamaño de un bloque de memoria asignado previamente intentando expandir o contraer el bloque sin mover su ubicación en el montón. El parámetro *memblock* apunta al principio del bloque. El parámetro *size* proporciona el nuevo tamaño del bloque, en bytes. El contenido del bloque queda sin modificar hasta el menor de los tamaños nuevos y antiguos. *memblock* no debe ser un bloque que se ha liberado.

> [!NOTE]
> En las plataformas de 64 bits, **_expand** podría no contratar el bloque si el nuevo tamaño es menor que el tamaño actual; en concreto, si el bloque tenía menos de 16 k de tamaño y, por lo tanto, se asigna en el montón de fragmentación baja, **_expand** deja el bloque sin cambios y devuelve *memblock*.

Cuando la aplicación se vincula con una versión de depuración de las bibliotecas en tiempo de ejecución de C, **_expand** se resuelve en [_expand_dbg](expand-dbg.md). Para obtener más información sobre cómo se administra el montón durante el proceso de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

Esta función valida sus parámetros. Si *memblock* es un puntero nulo, esta función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **null**. Si *el tamaño* es mayor que **_HEAP_MAXREQ**, **errno** se establece en **ENOMEM** y la función devuelve **null**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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
[ningún](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
