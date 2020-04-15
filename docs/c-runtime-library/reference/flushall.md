---
title: _flushall
ms.date: 4/2/2020
api_name:
- _flushall
- _o__flushall
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: 93181c0fe941a1c5e259e706771495666329bcb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346620"
---
# <a name="_flushall"></a>_flushall

Vacía todos los flujos y borra todos los búferes.

## <a name="syntax"></a>Sintaxis

```C
int _flushall( void );
```

## <a name="return-value"></a>Valor devuelto

**_flushall** devuelve el número de secuencias abiertas (entrada y salida). No se devuelve ningún error.

## <a name="remarks"></a>Observaciones

De forma predeterminada, la función **_flushall** escribe en los archivos adecuados el contenido de todos los búferes asociados con las secuencias de salida abiertas. Se borra el contenido actual de todos los búferes asociados a los flujos de entrada abiertos. Normalmente, el sistema operativo mantiene estos búferes y determina el momento óptimo para escribir los datos automáticamente en el disco: cuando el búfer está lleno, cuando se cierra un flujo o cuando un programa finaliza con normalidad sin cerrar flujos.

Si una lectura sigue a una llamada a **_flushall**, se leen nuevos datos de los archivos de entrada en los búferes. Todas las secuencias permanecen abiertas después de la llamada a **_flushall**.

La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escribe directamente en el disco y no en los búferes del sistema operativo. Sin reescribir un programa existente, puede habilitar esta función vinculando los archivos de objetodel con Commode.obj. En el archivo ejecutable resultante, las llamadas a **_flushall** escribir el contenido de todos los búferes en el disco. Commode.obj solo afecta **a _flushall** y [fflush.](fflush.md)

Para obtener información sobre cómo controlar la característica de confirmación en disco, consulte [E/S de secuencia](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) y [_fdopen](fdopen-wfdopen.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
