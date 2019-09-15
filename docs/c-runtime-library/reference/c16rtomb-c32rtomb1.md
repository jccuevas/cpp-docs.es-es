---
title: c16rtomb, c32rtomb
ms.date: 01/22/2018
api_name:
- c16rtomb
- c32rtomb
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
ms.openlocfilehash: a16effe48442ccbb5144b57ead2fb15c908fe898
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943427"
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
Un puntero a un objeto **mbstate_t** .

## <a name="return-value"></a>Valor devuelto

Número de bytes almacenados en el objeto de matriz *mbchar*, incluidas las secuencias de desplazamiento. Si *WCHAR* no es un carácter ancho válido, se devuelve el valor (**size_t**) (-1), **errno** se establece en **EILSEQ**y el valor de *State* no se especifica.

## <a name="remarks"></a>Comentarios

La función **c16rtomb** convierte *el carácter UTF-16 en la* secuencia de caracteres estrechos multibyte equivalentes en la configuración regional actual. Si *mbchar* no es un puntero nulo, la función almacena la secuencia convertida en el objeto de matriz al que apunta *mbchar*. Hasta **MB_CUR_MAX** bytes se almacenan en *mbchar*y el *Estado* se establece en el estado de desplazamiento multibyte resultante.    Si *WCHAR* es un carácter ancho nulo, se almacena una secuencia necesaria para restaurar el estado de desplazamiento inicial, si es necesario, seguido del carácter nulo y el *Estado* se establece en el estado de conversión inicial. La función **c32rtomb** es idéntica, pero convierte un carácter UTF-32.

Si *mbchar* es un puntero nulo, el comportamiento es equivalente a una llamada a la función que sustituye un búfer interno para *mbchar* y un carácter nulo ancho para *WCHAR*.

El objeto de estado de la conversión de *Estado* permite realizar llamadas posteriores a esta función y a otras funciones reiniciables que mantienen el estado de desplazamiento de los caracteres de salida multibyte. Los resultados son indefinidos al mezclar el uso de funciones reiniciables y no reiniciables, o si se realiza una llamada a **setlocale** entre las llamadas a funciones reiniciables.

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
