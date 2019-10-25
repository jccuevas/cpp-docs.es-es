---
title: fflush
ms.date: 09/11/2019
api_name:
- fflush
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
- fflush
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
ms.openlocfilehash: 966ff5622faaccd2d9e501b39da99b010e841c22
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940947"
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
> Si **fflush** devuelve **EOF**, es posible que se hayan perdido datos debido a un error de escritura. Al configurar un controlador de errores crítico, es más seguro desactivar el almacenamiento en búfer con la función **setvbuf (** o usar rutinas de e/s de bajo nivel como _ **Open**, **_close**y _ **Write** en lugar de las funciones de e/s de secuencias.

## <a name="remarks"></a>Comentarios

La función **fflush** vacía el *flujo*de la secuencia. Si la secuencia se ha abierto en modo de escritura, o se ha abierto en modo de actualización y la última operación ha sido una operación de escritura, el contenido del búfer de la secuencia se escribe en el archivo o dispositivo subyacentes y el búfer se descarta. Si la secuencia se abrió en modo de lectura, o si la secuencia no tiene ningún búfer, la llamada a **fflush** no tiene ningún efecto y se conserva cualquier búfer. Una llamada a **fflush** niega el efecto de cualquier llamada anterior a **ungetc** para la secuencia. La secuencia sigue abierta después de la llamada.

Si *Stream* es **null**, el comportamiento es el mismo que una llamada a **fflush** en cada flujo abierto. Se vacían todas las secuencias abiertas en modo de escritura y en modo de actualización en las que la última operación ha sido de escritura. La llamada no tiene ningún efecto en otras secuencias.

Normalmente, el sistema operativo mantiene los búferes y determina el momento óptimo para escribir los datos automáticamente en el disco: cuando el búfer está lleno, cuando se cierra una secuencia o cuando un programa finaliza con normalidad sin cerrar la secuencia. La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escriben directamente en el disco y no en los búferes del sistema operativo. Sin tener que volver a escribir un programa existente, puede habilitar esta característica vinculando los archivos objeto del programa a COMMODE.OBJ. En el archivo ejecutable resultante, las llamadas a **_flushall** escriben el contenido de todos los búferes en el disco. COMMODE. OBJ solo afecta a **_flushall** y **fflush** .

Para obtener información sobre cómo controlar la característica de confirmación en disco, consulte [E/S de secuencia](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) y [_fdopen](fdopen-wfdopen.md).

Esta función bloquea el subproceso de llamada y por lo tanto es segura para subprocesos. Para una versión que no sea de bloqueo, vea **_fflush_nolock**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fflush.c
// Compile with: cl /W4 crt_fflush.c
// This sample gets a number from the user, then writes it to a file.
// It ensures the write isn't lost on crash by calling fflush.
#include <stdio.h>

int * crash_the_program = 0;

int main(void)
{
    FILE * my_file;
    errno_t err = fopen_s(&my_file, "myfile.txt", "w");
    if (my_file && !err)
    {
        printf("Write a number: ");

        int my_number = 0;
        scanf_s("%d", &my_number);

        fprintf(my_file, "User selected %d\n", my_number);

        // Write data to a file immediately instead of buffering.
        fflush(my_file);
    
        if (my_number == 5)
        {
            // Without using fflush, no data was written to the file 
            // prior to the crash, so the data is lost.
            *crash_the_program = 5;
        }

        // Normally, fflush is not needed as closing the file will write the buffer.
        // Note that files are automatically closed and flushed during normal termination.
        fclose(my_file);
    }
    return 0;
}
```

```Input
5
```

```myfile.txt
User selected 5
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
