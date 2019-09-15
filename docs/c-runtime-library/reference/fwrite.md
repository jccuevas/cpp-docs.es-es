---
title: fwrite
ms.date: 11/04/2016
api_name:
- fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: 8149e0f2cbc84c2c28093d86fecd5ff2a9db7aba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956195"
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

*buffer*<br/>
Puntero a los datos que se van a escribir.

*size*<br/>
Tamaño del elemento en bytes.

*count*<br/>
Número máximo de elementos que se va a escribir.

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fwrite** devuelve el número de elementos completos escritos realmente, que puede ser menor que *Count* si se produce un error. De igual modo, si se produce un error, no se podrá conocer el indicador de posición de archivo. Si la *secuencia* o el *búfer* es un puntero nulo, o si se especifica un número impar de bytes en el modo Unicode, la función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve 0.

## <a name="remarks"></a>Comentarios

La función **fwrite** escribe hasta el *número* de elementos, de longitud de *tamaño* cada uno, desde el *búfer* hasta el *flujo*de salida. El puntero de archivo asociado al *flujo* (si hay alguno) se incrementa según el número de bytes escritos realmente. Si el *flujo* se abre en modo de texto, cada avance de línea se reemplaza por un par de retorno de carro y avance de línea. Este reemplazo no tiene efecto alguno en el valor devuelto.

Cuando el *flujo* se abre en el modo de conversión Unicode (por ejemplo, si la *secuencia* se abre llamando a **fopen** y usando un parámetro de modo que incluye **CCS = Unicode**, **CCS = UTF-16LE**o **CCS = UTF-8**) o si el modo es cambiado a un modo de conversión Unicode mediante **_setmode** y un parámetro de modo que incluye **_O_WTEXT**, **_O_U16TEXT**o **_O_U8TEXT**: el*búfer* se interpreta como un puntero a una matriz de **wchar_t** que contiene Datos UTF-16. Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.

Como esta función bloquea el subproceso de llamada, es segura para los subprocesos. Para una versión que no sea de bloqueo, vea **_fwrite_nolock**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [fread](fread.md).

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
