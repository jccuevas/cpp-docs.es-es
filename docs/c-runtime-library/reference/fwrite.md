---
title: fwrite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fwrite
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
- fwrite
dev_langs:
- C++
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b91ad6efe0573bc469e0752ed27978b12018ee7
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fwrite** devuelve el número de completo elementos escritos realmente, lo que puede ser menor que *recuento* si se produce un error. De igual modo, si se produce un error, no se podrá conocer el indicador de posición de archivo. Si el valor *flujo* o *búfer* es un puntero nulo, o si se especifica un número impar de bytes que se escribirán en el modo Unicode, la función invoca el controlador de parámetros no válidos, tal y como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve 0.

## <a name="remarks"></a>Comentarios

El **fwrite** función escribe hasta *recuento* elementos de *tamaño* longitud cada uno, de *búfer* a la salida de *flujo*. El puntero de archivo asociado a *flujo* (si hay alguno) que se incrementa el número de bytes escritos realmente. Si *flujo* se abre en modo de texto, cada salto de línea se reemplaza por un retorno de carro y avance de línea par. Este reemplazo no tiene efecto alguno en el valor devuelto.

Cuando *flujo* se abre en modo de traducción de Unicode, por ejemplo, si *flujo* se abre mediante una llamada a **fopen** y el uso de un parámetro de modo que incluya **ccs = UNICODE**, **ccs = UTF-16LE**, o **ccs = UTF-8**, o si el modo se cambia a un modo de traducción de Unicode mediante el uso de **_setmode** y un modo parámetro que incluye **_O_WTEXT**, **_O_U16TEXT**, o **_O_U8TEXT**:*búfer* se interpreta como un puntero a un matriz de **wchar_t** que contiene datos UTF-16. Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.

Como esta función bloquea el subproceso de llamada, es segura para los subprocesos. Para obtener una versión de no bloqueo, vea **_fwrite_nolock**.

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
