---
title: fflush
ms.date: 11/04/2016
apiname:
- fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: d03d20ee5024915d0ca4c5a21db4159e8c4f876a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333987"
---
# <a name="fflush"></a>fflush

Vacía una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fflush** devuelve 0 si el búfer se ha vaciado correctamente. También se devuelve el valor 0 en los casos en que la secuencia especificada no tiene ningún búfer o solo se abre para lectura. Un valor devuelto de **EOF** indica un error.

> [!NOTE]
> Si **fflush** devuelve **EOF**, pueden haberse perdidos debido a un error de escritura de datos. Al configurar un controlador de errores críticos, resulta más seguro desactivar el almacenamiento en búfer con el **setvbuf** función o usar rutinas de E/S de bajo nivel como **_open**, **_close**, y **_write** en lugar de las funciones de E/S de secuencia.

## <a name="remarks"></a>Comentarios

El **fflush** función vuelca el flujo *secuencia*. Si la secuencia se ha abierto en modo de escritura, o se ha abierto en modo de actualización y la última operación ha sido una operación de escritura, el contenido del búfer de la secuencia se escribe en el archivo o dispositivo subyacentes y el búfer se descarta. Si la secuencia se ha abierto en modo de lectura, o si la secuencia no tiene ningún búfer, la llamada a **fflush** no tiene ningún efecto y se conserva ningún búfer. Una llamada a **fflush** anula el efecto de cualquier llamada anterior a **ungetc** para la secuencia. La secuencia sigue abierta después de la llamada.

Si *secuencia* es **NULL**, el comportamiento es el mismo que una llamada a **fflush** en cada secuencia abierta. Se vacían todas las secuencias abiertas en modo de escritura y en modo de actualización en las que la última operación ha sido de escritura. La llamada no tiene ningún efecto en otras secuencias.

Normalmente, el sistema operativo mantiene los búferes y determina el momento óptimo para escribir los datos automáticamente en el disco: cuando el búfer está lleno, cuando se cierra una secuencia o cuando un programa finaliza con normalidad sin cerrar la secuencia. La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escriben directamente en el disco y no en los búferes del sistema operativo. Sin tener que volver a escribir un programa existente, puede habilitar esta característica vinculando los archivos objeto del programa a COMMODE.OBJ. En el archivo ejecutable resultante, las llamadas a **_flushall** escribir el contenido de todos los búferes en el disco. Solo **_flushall** y **fflush** se ven afectadas por COMMODE.OBJ.

Para obtener información sobre cómo controlar la característica de confirmación en disco, consulte [E/S de secuencia](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) y [_fdopen](fdopen-wfdopen.md).

Esta función bloquea el subproceso de llamada y por lo tanto es segura para subprocesos. Para obtener una versión que no sea de bloqueo, consulte **_fflush_nolock**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fflush.c
#include <stdio.h>
#include <conio.h>

int main( void )
{
   int integer;
   char string[81];

   // Read each word as a string.
   printf( "Enter a sentence of four words with scanf: " );
   for( integer = 0; integer < 4; integer++ )
   {
      scanf_s( "%s", string, sizeof(string) );
      printf( "%s\n", string );
   }

   // You must flush the input buffer before using gets.
   // fflush on input stream is an extension to the C standard
   fflush( stdin );
   printf( "Enter the same sentence with gets: " );
   gets_s( string, sizeof(string) );
   printf( "%s\n", string );
}
```

```Input
This is a test
This is a test
```

```Output
Enter a sentence of four words with scanf: This is a test
This
is
a
test
Enter the same sentence with gets: This is a test
This is a test
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
