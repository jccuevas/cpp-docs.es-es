---
title: setvbuf
ms.date: 4/2/2020
api_name:
- setvbuf
- _o_setvbuf
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
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: 907d02e94c79acf09dfa99a8b42e9f448d32dcfa
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915752"
---
# <a name="setvbuf"></a>setvbuf

Controla el almacenamiento en búfer de la secuencia y el tamaño del búfer.

## <a name="syntax"></a>Sintaxis

```C
int setvbuf(
   FILE *stream,
   char *buffer,
   int mode,
   size_t size
);
```

### <a name="parameters"></a>Parámetros

*misiones*<br/>
Puntero a la estructura **FILE**.

*búfer*<br/>
Búfer asignado por el usuario.

*mode*<br/>
Modo de almacenamiento en búfer.

*size*<br/>
Tamaño del búfer en bytes. Intervalo permitido: 2 <= *tamaño* <= INT_MAX (2147483647). Internamente, el valor proporcionado para el *tamaño* se redondea hacia abajo al múltiplo más próximo de 2.

## <a name="return-value"></a>Valor devuelto

Si la operación se realiza correctamente, devuelve 0.

Si *Stream* es **null**, o si el *modo* o *el tamaño* no está dentro de un cambio válido, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **setvbuf (** permite que el programa controle el almacenamiento en búfer y el tamaño de búfer de la *secuencia*. la *secuencia* debe hacer referencia a un archivo abierto que no haya sufrido una operación de e/s desde que se abrió. La matriz a la que apunta el *búfer* se usa como búfer, a menos que sea **null**, en cuyo caso **setvbuf (** usa un búfer asignado automáticamente de *tamaño*de \* longitud/2 2 bytes.

El modo debe ser **_IOFBF**, **_IOLBF**o **_IONBF**. Si el *modo* es **_IOFBF** o **_IOLBF**, se usa el *tamaño* como el tamaño del búfer. Si el *modo* es **_IONBF**, el flujo no se almacena en búfer y se omiten el *tamaño* y el *búfer* . Los valores para el *modo* y sus significados son:

|valor de *modo*|Significado|
|-|-|
| **_IOFBF** | Almacenamiento en búfer completo; es decir, el *búfer* se utiliza como búfer y el *tamaño* se utiliza como tamaño del búfer. Si *buffer* es **null**, se usa un *tamaño* de búfer asignado automáticamente de bytes de longitud. |
| **_IOLBF** | En algunos sistemas, esto proporciona un almacenamiento en búfer en línea, Sin embargo, para Win32, el comportamiento es el mismo que el almacenamiento en búfer completo **_IOFBF** . |
| **_IONBF** | No se usa ningún búfer, independientemente del *búfer* o *el tamaño*. |

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_setvbuf.c
// This program opens two streams: stream1
// and stream2. It then uses setvbuf to give stream1 a
// user-defined buffer of 1024 bytes and stream2 no buffer.
//

#include <stdio.h>

int main( void )
{
   char buf[1024];
   FILE *stream1, *stream2;

   if( fopen_s( &stream1, "data1", "a" ) == 0 &&
       fopen_s( &stream2, "data2", "w" ) == 0 )
   {
      if( setvbuf( stream1, buf, _IOFBF, sizeof( buf ) ) != 0 )
         printf( "Incorrect type or size of buffer for stream1\n" );
      else
         printf( "'stream1' now has a buffer of 1024 bytes\n" );
      if( setvbuf( stream2, NULL, _IONBF, 0 ) != 0 )
         printf( "Incorrect type or size of buffer for stream2\n" );
      else
         printf( "'stream2' now has no buffer\n" );
      _fcloseall();
   }
}
```

```Output
'stream1' now has a buffer of 1024 bytes
'stream2' now has no buffer
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
