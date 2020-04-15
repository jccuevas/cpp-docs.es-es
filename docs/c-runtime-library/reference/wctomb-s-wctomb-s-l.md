---
title: wctomb_s, _wctomb_s_l
ms.date: 4/2/2020
api_name:
- _wctomb_s_l
- wctomb_s
- _o__wctomb_s_l
- _o_wctomb_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 1ddc9a991f28c4a2ea491f3ddd04d78f6345e255
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367252"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s, _wctomb_s_l

Convierte un carácter ancho en el carácter multibyte correspondiente. Versión de [wctomb, _wctomb_l](wctomb-wctomb-l.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*pRetValue*<br/>
Número de bytes o un código que indica el resultado.

*mbchar*<br/>
Dirección de un carácter multibyte.

*sizeInBytes*<br/>
Tamaño del *búfer mbchar*.

*Wchar*<br/>
Carácter ancho.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

Condiciones de error

|*mbchar*|*sizeInBytes*|Valor devuelto|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**Null**|>0|**EINVAL**|no modificado|
|cualquiera|>**INT_MAX**|**EINVAL**|no modificado|
|cualquiera|demasiado pequeño|**EINVAL**|no modificado|

Si se da alguna de las condiciones de error anteriores, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **wctomb** devuelve **EINVAL** y establece **errno** en **EINVAL**.

## <a name="remarks"></a>Observaciones

La función **wctomb_s** convierte su argumento *wchar* en el carácter multibyte correspondiente y almacena el resultado en *mbchar*. Puede llamar a la función desde cualquier ubicación de cualquier programa.

Si **wctomb_s** convierte el carácter ancho en un carácter multibyte, coloca el número de bytes (que nunca es mayor que **MB_CUR_MAX)** en el carácter ancho en el entero al que apunta *pRetValue*. Si *wchar* es el carácter nulo de caracteres anchos (L'-0'), **wctomb_s** rellena *pRetValue* con 1. Si el puntero de destino *mbchar* es **NULL**, **wctomb_s** coloca 0 en *pRetValue*. Si la conversión no es posible en la configuración regional actual, **wctomb_s** coloca -1 en *pRetValue*.

**wctomb_s** utiliza la configuración regional actual para la información dependiente de la configuración regional; **_wctomb_s_l** es idéntica, excepto que utiliza la configuración regional pasada en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa ilustra el comportamiento de la función **wctomb.**

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
