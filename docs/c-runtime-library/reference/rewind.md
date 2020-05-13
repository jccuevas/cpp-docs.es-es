---
title: rewind
ms.date: 4/2/2020
api_name:
- rewind
- _o_rewind
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rewind
helpviewer_keywords:
- rewind function
- repositioning file pointers
- file pointers [C++], repositioning
- file pointers [C++]
ms.assetid: 1a460ce1-28d8-4b5e-83a6-633dca29c28a
ms.openlocfilehash: 645b8bf105641b9f13a9f9fc0605e6b8526b4b56
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917756"
---
# <a name="rewind"></a>rewind

Cambia la posición del puntero de archivo al principio de un archivo.

## <a name="syntax"></a>Sintaxis

```C
void rewind(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*misiones*<br/>
Puntero a la estructura **FILE**.

## <a name="remarks"></a>Observaciones

La función **Rewind** cambia la posición del puntero de archivo asociado al *flujo* al principio del archivo. Una llamada a **rewind** es similar a

**(void) fseek (** _Stream_**, 0L, SEEK_SET);**

Sin embargo, a diferencia de [fseek](fseek-fseeki64.md), el **rebobinado** borra los indicadores de error de la secuencia, así como el indicador de fin de archivo. Además, a diferencia de [fseek](fseek-fseeki64.md), el **rebobinado** no devuelve un valor para indicar si el puntero se ha colocado correctamente.

Para borrar el búfer del teclado, use el **rebobinado** con la secuencia **stdin**, que está asociada con el teclado de forma predeterminada.

Si Stream es un puntero **nulo** , se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve y **errno** se establece en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**rebobinar**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_rewind.c
/* This program first opens a file named
* crt_rewind.out for input and output and writes two
* integers to the file. Next, it uses rewind to
* reposition the file pointer to the beginning of
* the file and reads the data back in.
*/
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int data1, data2;

   data1 = 1;
   data2 = -37;

   fopen_s( &stream, "crt_rewind.out", "w+" );
   if( stream != NULL )
   {
      fprintf( stream, "%d %d", data1, data2 );
      printf( "The values written are: %d and %d\n", data1, data2 );
      rewind( stream );
      fscanf_s( stream, "%d %d", &data1, &data2 );
      printf( "The values read are: %d and %d\n", data1, data2 );
      fclose( stream );
   }
}
```

### <a name="output"></a>Salida

```Output
The values written are: 1 and -37
The values read are: 1 and -37
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
