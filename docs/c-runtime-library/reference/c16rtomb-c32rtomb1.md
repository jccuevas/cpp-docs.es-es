---
title: c16rtomb, c32rtomb1
ms.date: 11/04/2016
apiname:
- c16rtomb
- c32rtomb
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: 0d735363bbb317b06c1ebc73a2b0678479a243ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536596"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

Convierte un carácter ancho UTF-16 o UTF-32 en un carácter multibyte en la configuración regional actual.

## <a name="syntax"></a>Sintaxis

```C
size_t c16rtomb(
    char *mbchar,
    char16_t wchar,
    mbstate_t *state
);
size_t c32rtomb(
    char *mbchar,
    char32_t wchar,
    mbstate_t *state
);
```

### <a name="parameters"></a>Parámetros

*mbchar*<br/>
Puntero a una matriz para almacenar el carácter convertido multibyte.

*wchar*<br/>
Carácter ancho que se va a convertir.

*state*<br/>
Un puntero a un **mbstate_t** objeto.

## <a name="return-value"></a>Valor devuelto

El número de bytes almacenados en el objeto de matriz *mbchar*, incluidas las secuencias de desplazamiento. Si *wchar* no es un carácter ancho válido, el valor (**size_t**)(-1) se devuelve, **errno** está establecido en **EILSEQ**y el valor de *estado* no se ha especificado.

## <a name="remarks"></a>Comentarios

El **c16rtomb** función convierte el carácter UTF-16 *wchar* a la secuencia de caracteres estrechos multibyte equivalentes en la configuración regional actual. Si *mbchar* no es un puntero nulo, la función almacena la secuencia convertida en el objeto de matriz señalada por *mbchar*. Hasta **MB_CUR_MAX** bytes se almacenan en *mbchar*, y *estado* está establecido en el estado de desplazamiento multibyte resultante.    Si *wchar* es un carácter ancho nulo, necesarios para una secuencia de restauración se almacena el estado de desplazamiento inicial, si es necesario, seguido por el carácter null, y *estado* está establecido en el estado de conversión inicial. El **c32rtomb** función es idéntica, pero convierte un carácter UTF-32.

Si *mbchar* es un puntero nulo, el comportamiento es equivalente a una llamada a la función que sustituye un búfer interno para *mbchar* y un carácter nulo ancho para *wchar*.

El *estado* objeto de estado de la conversión le permite realizar las llamadas posteriores a esta función y otras funciones reiniciables que mantienen el estado de desplazamiento de los caracteres multibyte de salida. Los resultados son indefinidos al mezclar el uso de funciones reiniciables y no reiniciables, o si una llamada a **setlocale** se realiza entre las llamadas a funciones reiniciables.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++: \<uchar.h>|

Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)<br/>
[wcrtomb](wcrtomb.md)<br/>
[wcrtomb_s](wcrtomb-s.md)<br/>
