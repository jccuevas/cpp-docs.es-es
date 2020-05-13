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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ab1e172374cd117b07cc62923d291fbd3972882e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919446"
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

*búfer*<br/>
Puntero a los datos que se van a escribir.

*size*<br/>
Tamaño del elemento en bytes.

*count*<br/>
Número máximo de elementos que se va a escribir.

*misiones*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fwrite** devuelve el número de elementos completos escritos realmente, que puede ser menor que *Count* si se produce un error. De igual modo, si se produce un error, no se podrá conocer el indicador de posición de archivo. Si la *secuencia* o el *búfer* es un puntero nulo, o si se especifica un número impar de bytes en el modo Unicode, la función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve 0.

## <a name="remarks"></a>Observaciones

La función **fwrite** escribe hasta el *número* de elementos, de longitud de *tamaño* cada uno, desde el *búfer* hasta el *flujo*de salida. El puntero de archivo asociado al *flujo* (si hay alguno) se incrementa según el número de bytes escritos realmente. Si el *flujo* se abre en modo de texto, cada avance de línea se reemplaza por un par de retorno de carro y avance de línea. Este reemplazo no tiene efecto alguno en el valor devuelto.

Cuando el *flujo* se abre en el modo de conversión Unicode (por ejemplo, si la *secuencia* se abre llamando a **fopen** y usando un parámetro de modo que incluye **CCS = Unicode**), **CCS = UTF-16LE**o **CCS = UTF-8**, o bien, si el modo se cambia a un modo de conversión Unicode mediante **_setmode** y un parámetro de modo que incluye **_O_WTEXT**, **_O_U16TEXT**o **_O_U8TEXT**, el*búfer* se interpreta como un puntero a una matriz de **wchar_t** que contiene datos UTF-16. Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.

Como esta función bloquea el subproceso de llamada, es segura para los subprocesos. Para obtener una versión que no sea de bloqueo, consulte **_fwrite_nolock**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fread](fread.md).

## <a name="see-also"></a>Consulta también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
