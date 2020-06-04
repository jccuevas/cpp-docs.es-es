---
title: wcstombs, _wcstombs_l
ms.date: 4/2/2020
api_name:
- wcstombs
- _wcstombs_l
- _o__wcstombs_l
- _o_wcstombs
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
- wcstombs
- _wcstombs_l
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
ms.openlocfilehash: 33c7554f1ab5c9822a1908a4b50d0ee0764615ae
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910640"
---
# <a name="wcstombs-_wcstombs_l"></a>wcstombs, _wcstombs_l

Convierte una secuencia de caracteres anchos en una secuencia correspondiente de caracteres multibyte. Hay disponibles versiones más seguras de estas funciones; vea [wcstombs_s, _wcstombs_s_l](wcstombs-s-wcstombs-s-l.md).

## <a name="syntax"></a>Sintaxis

```C
size_t wcstombs(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count
);
size_t _wcstombs_l(
   char *mbstr,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
size_t wcstombs(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only
template <size_t size>
size_t _wcstombs_l(
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*mbstr*<br/>
Dirección de una secuencia de caracteres multibyte.

*wcstr*<br/>
Dirección de una secuencia de caracteres anchos.

*count*<br/>
Número máximo de bytes que se pueden almacenar en la cadena de salida multibyte.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Si **wcstombs** convierte correctamente la cadena multibyte, devuelve el número de bytes escritos en la cadena de salida multibyte, sin incluir el carácter null de terminación (si existe). Si el argumento *mbstr* es **null**, **wcstombs** devuelve el tamaño necesario en bytes de la cadena de destino. Si **wcstombs** encuentra un carácter ancho que no se puede convertir en un carácter multibyte, devuelve-1 convertido al tipo **size_t** y establece **errno** en **EILSEQ**.

## <a name="remarks"></a>Observaciones

La función **wcstombs** convierte la cadena de caracteres anchos a la que apunta *wcstr* en los caracteres multibyte correspondientes y almacena los resultados en la matriz *mbstr* . El parámetro *Count* indica el número máximo de bytes que se pueden almacenar en la cadena de salida multibyte (es decir, el tamaño de *mbstr*). En general, no se conoce el número de bytes que se necesitarán al convertir una cadena de caracteres anchos. Algunos caracteres anchos necesitarán un solo byte de la cadena de salida; otros necesitarán dos. Si hay dos bytes en la cadena de salida multibyte para cada carácter ancho de la cadena de entrada (incluido el carácter ancho nulo), se garantiza que el resultado cabe.

Si **wcstombs** detecta el carácter nulo de caracteres anchos (L ' \ 0 ') antes o cuando se produce el *recuento* , lo convierte en un 0 de 8 bits y se detiene. Por lo tanto, la cadena de caracteres multibyte en *mbstr* está terminada en NULL solo si **wcstombs** encuentra un carácter nulo de caracteres anchos durante la conversión. Si las secuencias señaladas por *wcstr* y *mbstr* se superponen, el comportamiento de **wcstombs** es indefinido.

Si el argumento *mbstr* es **null**, **wcstombs** devuelve el tamaño necesario en bytes de la cadena de destino.

**wcstombs** valida sus parámetros. Si *wcstr* es **null**, o si *Count* es mayor que **INT_MAX**, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, la función establece **errno** en **EINVAL** y devuelve-1.

**wcstombs** usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; **_wcstombs_l** es idéntico, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wcstombs**|\<stdlib.h>|
|**_wcstombs_l**|\<stdlib.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa muestra el comportamiento de la función **wcstombs** .

```C
// crt_wcstombs.c
// compile with: /W3
// This example demonstrates the use
// of wcstombs, which converts a string
// of wide characters to a string of
// multibyte characters.

#include <stdlib.h>
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t  count;
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t *pWCBuffer = L"Hello, world.";

    printf("Convert wide-character string:\n" );

    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996
    // Note: wcstombs is deprecated; consider using wcstombs_s instead
    printf("   Characters converted: %u\n",
            count );
    printf("    Multibyte character: %s\n\n",
           pMBBuffer );

    free(pMBBuffer);
}
```

```Output
Convert wide-character string:
   Characters converted: 13
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
