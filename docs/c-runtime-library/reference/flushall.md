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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 1a53eeedd5dfa0f9c01fa5883a9db33e26e3ea17
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911626"
---
# <a name="_flushall"></a>_flushall

Vacía todos los flujos y borra todos los búferes.

## <a name="syntax"></a>Sintaxis

```C
int _flushall( void );
```

## <a name="return-value"></a>Valor devuelto

**_flushall** devuelve el número de flujos abiertos (entrada y salida). No se devuelve ningún error.

## <a name="remarks"></a>Observaciones

De forma predeterminada, la función **_flushall** escribe en los archivos correspondientes el contenido de todos los búferes asociados a los flujos de salida abiertos. Se borra el contenido actual de todos los búferes asociados a los flujos de entrada abiertos. Normalmente, el sistema operativo mantiene estos búferes y determina el momento óptimo para escribir los datos automáticamente en el disco: cuando el búfer está lleno, cuando se cierra un flujo o cuando un programa finaliza con normalidad sin cerrar flujos.

Si una lectura sigue una llamada a **_flushall**, se leen datos nuevos de los archivos de entrada en los búferes. Todas las secuencias permanecen abiertas después de la llamada a **_flushall**.

La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escribe directamente en el disco y no en los búferes del sistema operativo. Sin volver a escribir un programa existente, puede habilitar esta característica vinculando los archivos de objeto del programa con Commode. obj. En el archivo ejecutable resultante, las llamadas a **_flushall** escriben el contenido de todos los búferes en el disco. Commode. obj solo afecta a **_flushall** y [fflush](fflush.md) .

Para obtener información sobre cómo controlar la característica de confirmación en disco, consulte [E/S de secuencia](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) y [_fdopen](fdopen-wfdopen.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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
