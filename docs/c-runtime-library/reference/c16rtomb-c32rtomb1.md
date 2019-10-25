---
title: c16rtomb, c32rtomb
ms.date: 10/22/2019
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
ms.openlocfilehash: 8f480d9b450b528275fea78ae878269fa6a4fa54
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811071"
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb

Convierte un carácter ancho UTF-16 o UTF-32 en un carácter multibyte UTF-8.

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

\ *mbchar*
Puntero a una matriz para almacenar el carácter multibyte UTF-8 convertido.

*wchar*\
Carácter ancho que se va a convertir.

\ de *Estado*
Un puntero a un objeto **mbstate_t** .

## <a name="return-value"></a>Valor devuelto

Número de bytes almacenados en el objeto de matriz *mbchar*, incluidas las secuencias de desplazamiento. Si *WCHAR* no es un carácter ancho válido, se devuelve el valor (**size_t**) (-1), **errno** se establece en **EILSEQ**y el valor de *State* no está especificado.

## <a name="remarks"></a>Comentarios

La función **c16rtomb** convierte el carácter UTF-16 le *WCHAR* en la secuencia de caracteres estrechos multibyte de UTF-8 equivalente. Si *mbchar* no es un puntero nulo, la función almacena la secuencia convertida en el objeto de matriz al que apunta *mbchar*. Hasta **MB_CUR_MAX** bytes se almacenan en *mbchar*y el *Estado* se establece en el estado de desplazamiento multibyte resultante.

Si *WCHAR* es un carácter ancho nulo, se almacena una secuencia necesaria para restaurar el estado de desplazamiento inicial, si es necesario, seguida del carácter nulo. el *Estado* se establece en el estado de conversión inicial. La función **c32rtomb** es idéntica, pero convierte un carácter UTF-32.

Si *mbchar* es un puntero nulo, el comportamiento es equivalente a una llamada a la función que sustituye un búfer interno para *mbchar* y un carácter nulo ancho para *WCHAR*.

El objeto de estado de la conversión de *Estado* permite realizar llamadas posteriores a esta función y a otras funciones reiniciables que mantienen el estado de desplazamiento de los caracteres de salida multibyte. Los resultados son indefinidos al mezclar el uso de funciones reiniciables y no reiniciables.

Para convertir caracteres UTF-16 en caracteres multibyte no UTF-8, use las funciones [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md), [wcstombs_s o _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md) .

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**c16rtomb**, **c32rtomb**|C, C++: \<uchar.h>|

Para obtener información sobre la compatibilidad, vea [Compatibilidad](../compatibility.md).

## <a name="see-also"></a>Vea también

\ de [conversión de datos](../data-conversion.md)
[Configuración regional](../locale.md)\
[Interpretación de secuencias de caracteres multibyte](../interpretation-of-multibyte-character-sequences.md)\
[mbrtoc16, mbrtoc32](mbrtoc16-mbrtoc323.md)\
[wcrtomb](wcrtomb.md)\
[wcrtomb_s](wcrtomb-s.md)
