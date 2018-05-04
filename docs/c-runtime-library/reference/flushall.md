---
title: _flushall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _flushall
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
- _flushall
dev_langs:
- C++
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb094e2f99e0554320df69946470f42f461819d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="flushall"></a>_flushall

Vacía todos los flujos y borra todos los búferes.

## <a name="syntax"></a>Sintaxis

```C
int _flushall( void );
```

## <a name="return-value"></a>Valor devuelto

**_flushall** devuelve el número de flujos abiertos (entrada y salida). No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

De forma predeterminada, el **_flushall** función escribe en el contenido de todos los búferes asociados a los flujos de salida abiertos los archivos correspondientes. Se borra el contenido actual de todos los búferes asociados a los flujos de entrada abiertos. Normalmente, el sistema operativo mantiene estos búferes y determina el momento óptimo para escribir los datos automáticamente en el disco: cuando el búfer está lleno, cuando se cierra un flujo o cuando un programa finaliza con normalidad sin cerrar flujos.

Si una lectura sigue a una llamada a **_flushall**, nuevos datos se leen de los archivos de entrada en los búferes. Todos los flujos permanecen abiertos después de llamar a **_flushall**.

La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escribe directamente en el disco y no en los búferes del sistema operativo. Sin tener que volver a escribir un programa existente, puede habilitar esta característica vinculando los archivos objeto del programa a Commode.obj. En el archivo ejecutable resultante, las llamadas a **_flushall** escribir el contenido de todos los búferes en el disco. Solo **_flushall** y [fflush](fflush.md) se ven afectados por Commode.obj.

Para obtener información sobre cómo controlar la característica de confirmación en disco, consulte [E/S de secuencia](../../c-runtime-library/stream-i-o.md), [fopen](fopen-wfopen.md) y [_fdopen](fdopen-wfdopen.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
