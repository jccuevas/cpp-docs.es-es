---
title: wctomb, _wctomb_l
ms.date: 4/2/2020
api_name:
- _wctomb_l
- wctomb
- _o__wctomb_l
- _o_wctomb
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: 0a95d61c50af5f49e69df8ae20efccfd3fb8ff5f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910428"
---
# <a name="wctomb-_wctomb_l"></a>wctomb, _wctomb_l

Convierte un carácter ancho en el carácter multibyte correspondiente. Hay disponibles versiones más seguras de estas funciones; vea [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md).

## <a name="syntax"></a>Sintaxis

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*mbchar*<br/>
Dirección de un carácter multibyte.

*WCHAR*<br/>
Carácter ancho.

## <a name="return-value"></a>Valor devuelto

Si **wctomb** convierte el carácter ancho en un carácter multibyte, devuelve el número de bytes (que nunca es mayor que **MB_CUR_MAX**) en el carácter ancho. Si *WCHAR* es el carácter nulo de caracteres anchos (L ' \ 0 '), **wctomb** devuelve 1. Si el puntero de destino *mbchar* es **null**, **wctomb** devuelve 0. Si la conversión no es posible en la configuración regional actual, **wctomb** devuelve-1 y **errno** se establece en **EILSEQ**.

## <a name="remarks"></a>Observaciones

La función **wctomb** convierte su argumento *WCHAR* en el carácter multibyte correspondiente y almacena el resultado en *mbchar*. Puede llamar a la función desde cualquier ubicación de cualquier programa. **wctomb** usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; **_wctomb_l** es idéntica a **wctomb** , salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

**wctomb** valida sus parámetros. Si *mbchar* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve-1.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa muestra el comportamiento de la función wctomb.

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
