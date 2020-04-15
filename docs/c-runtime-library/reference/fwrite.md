---
title: fwrite
ms.date: 4/2/2020
api_name:
- fwrite
- _o_fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: a5bd6da3c8d16189f7ff0db744901e03513acc21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345393"
---
# <a name="fwrite"></a>fwrite

Escribe datos en un flujo.

## <a name="syntax"></a>Sintaxis

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*Búfer*<br/>
Puntero a los datos que se van a escribir.

*Tamaño*<br/>
Tamaño del elemento en bytes.

*count*<br/>
Número máximo de elementos que se va a escribir.

*Corriente*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fwrite** devuelve el número de elementos completos escritos realmente, que puede ser menor que *el recuento* si se produce un error. De igual modo, si se produce un error, no se podrá conocer el indicador de posición de archivo. Si *la secuencia* o el *búfer* es un puntero nulo, o si se especifica un número impar de bytes que se van a escribir en modo Unicode, la función invoca el controlador de parámetros no válidos, como se describe en [Validación](../../c-runtime-library/parameter-validation.md)de parámetros . Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve 0.

## <a name="remarks"></a>Observaciones

La función **fwrite** escribe para *contar* elementos, de longitud de *tamaño* cada uno, desde el *búfer* hasta la *secuencia*de salida. El puntero de archivo asociado a *la secuencia* (si hay uno) se incrementa por el número de bytes realmente escritos. Si *la secuencia* se abre en modo de texto, cada avance de línea se sustituye por un par de avance de línea de retorno de carro. Este reemplazo no tiene efecto alguno en el valor devuelto.

Cuando la *secuencia* se abre en modo de traducción Unicode, por ejemplo, si la *secuencia* se abre llamando a **fopen** y utilizando un parámetro mode que incluye **ccs-UNICODE**, **ccs-UTF-16LE**, o **ccs-UTF-8**, o si el modo se cambia a un modo de traducción Unicode mediante **_setmode** y un parámetro de modo que incluye **_O_WTEXT**, **_O_U16TEXT,** o **_O_U8TEXT**—*buffer* se interpreta como un puntero a una matriz de **wchar_t** que contiene datos UTF-16. Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.

Como esta función bloquea el subproceso de llamada, es segura para los subprocesos. Para obtener una versión sin bloqueo, consulte **_fwrite_nolock**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fread](fread.md).

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
