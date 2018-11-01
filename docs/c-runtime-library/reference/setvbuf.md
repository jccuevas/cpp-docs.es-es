---
title: setvbuf
ms.date: 11/04/2016
apiname:
- setvbuf
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- setvbuf
helpviewer_keywords:
- controlling stream buffering
- stream buffering
- setvbuf function
ms.assetid: 6aa5aa37-3408-4fa0-992f-87f9f9c4baea
ms.openlocfilehash: b2a5cfc08da7812e32ad84940ab4c78288017720
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445778"
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

*secuencia*<br/>
Puntero a la estructura **FILE**.

*buffer*<br/>
Búfer asignado por el usuario.

*mode*<br/>
Modo de almacenamiento en búfer.

*size*<br/>
Tamaño del búfer en bytes. Intervalo permitido: 2 < = *tamaño* < = INT_MAX (2147483647). Internamente, el valor proporcionado para *tamaño* se redondea hacia abajo al múltiplo más cercano de 2.

## <a name="return-value"></a>Valor devuelto

Si la operación se realiza correctamente, devuelve 0.

Si *secuencia* es **NULL**, o si *modo* o *tamaño* es no dentro de un cambio válido, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** a **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **setvbuf** función permite que el programa controlar tanto el almacenamiento en búfer y tamaño del búfer de *secuencia*. *secuencia* debe hacer referencia a un archivo abierto que no se ha sometido a una operación de E/S desde que se abrió. La matriz señalada por *búfer* sirve como búfer, a menos que sea **NULL**, en cuyo caso **setvbuf** utiliza un búfer asignado automáticamente de longitud  *tamaño*/2 \* 2 bytes.

El modo debe ser **_IOFBF**, **_IOLBF**, o **_IONBF**. Si *modo* es **_IOFBF** o **_IOLBF**, a continuación, *tamaño* se utiliza como el tamaño del búfer. Si *modo* es **_IONBF**, la secuencia se almacena en búfer y *tamaño* y *búfer* se omiten. Los valores de *modo* y sus significados son:

|*modo* valor|Significado|
|-|-|
**_IOFBF**|Almacenamiento en búfer completo; es decir, *búfer* sirve como búfer y *tamaño* se utiliza como el tamaño del búfer. Si *búfer* es **NULL**, un búfer asignado automáticamente *tamaño* se utiliza la longitud de bytes.
**_IOLBF**|En algunos sistemas, esto proporciona un almacenamiento en búfer en línea, Sin embargo, para Win32, el comportamiento es igual a **_IOFBF** -almacenamiento en búfer completo.
**_IONBF**|No hay ningún búfer se usa, con independencia del *búfer* o *tamaño*.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**setvbuf**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[setbuf](setbuf.md)<br/>
