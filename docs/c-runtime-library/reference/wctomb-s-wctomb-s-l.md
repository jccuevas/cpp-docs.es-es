---
title: wctomb_s, _wctomb_s_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wctomb_s_l
- wctomb_s
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
- wctomb_s
- _wctomb_s_l
dev_langs:
- C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb0a44414b01d0105f911732bc3dd2662a278158
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="wctombs-wctombsl"></a>wctomb_s, _wctomb_s_l

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
Tamaño del búfer *mbchar*.

*wchar*<br/>
Carácter ancho.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

Condiciones de error

|*mbchar*|*sizeInBytes*|Valor devuelto|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|no modificado|
|any|>**INT_MAX**|**EINVAL**|no modificado|
|any|demasiado pequeño|**EINVAL**|no modificado|

Si se da alguna de las condiciones de error anteriores, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **wctomb** devuelve **EINVAL** y establece **errno** a **EINVAL**.

## <a name="remarks"></a>Comentarios

El **wctomb_s** función convierte su *wchar* argumento en el carácter multibyte correspondiente y almacena el resultado en *mbchar*. Puede llamar a la función desde cualquier ubicación de cualquier programa.

Si **wctomb_s** convierte el carácter ancho en un carácter multibyte, coloca el número de bytes (que nunca es mayor que **MB_CUR_MAX**) en el carácter ancho en el entero que señala *pRetValue*. Si *wchar* es el carácter null de caracteres anchos (L '\0'), **wctomb_s** rellena *pRetValue* con 1. Si el puntero de destino *mbchar* es NULL, **wctomb_s** coloca 0 en *pRetValue*. Si la conversión no es posible en la configuración regional actual, **wctomb_s** pone -1 en *pRetValue*.

**wctomb_s** utiliza la configuración regional actual para obtener información de dependiente de la configuración regional; **_wctomb_s_l** es idéntica, salvo que usa la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa muestra el comportamiento de la **wctomb** (función).

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

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)<br/>
