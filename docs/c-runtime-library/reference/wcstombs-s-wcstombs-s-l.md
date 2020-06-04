---
title: wcstombs_s, _wcstombs_s_l
ms.date: 4/2/2020
api_name:
- _wcstombs_s_l
- wcstombs_s
- _o__wcstombs_s_l
- _o_wcstombs_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcstombs_s
- _wcstombs_s_l
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
ms.openlocfilehash: 7254df673694bf4d91679f1a41837c10f61d28e2
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910609"
---
# <a name="wcstombs_s-_wcstombs_s_l"></a>wcstombs_s, _wcstombs_s_l

Convierte una secuencia de caracteres anchos en una secuencia correspondiente de caracteres multibyte. Versión de [wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t wcstombs_s(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count
);

errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char *mbstr,
   size_t sizeInBytes,
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
);

template <size_t size>
errno_t wcstombs_s(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count
); // C++ only

template <size_t size>
errno_t _wcstombs_s_l(
   size_t *pReturnValue,
   char (&mbstr)[size],
   const wchar_t *wcstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*pReturnValue*<br/>
Tamaño en bytes de la cadena convertida, incluido el terminador null.

*mbstr*<br/>
Dirección de un búfer para la cadena de caracteres multibyte convertida resultante.

*sizeInBytes*<br/>
Tamaño en bytes del búfer de *mbstr* .

*wcstr*<br/>
Apunta a la cadena de caracteres anchos que se va a convertir.

*count*<br/>
Número máximo de bytes que se van a almacenar en el búfer de *mbstr* , sin incluir el carácter nulo de terminación o [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

|Condición de error|Valor devuelto y **errno**|
|---------------------|------------------------------|
|*mbstr* es **NULL** y *sizeInBytes* > 0|**EINVAL**|
|*wcstr* es **null**|**EINVAL**|
|El búfer de destino es demasiado pequeño para contener la cadena convertida (a menos que el *recuento* sea **_TRUNCATE**; vea la sección Comentarios a continuación).|**ERANGE**|

Si se produce alguna de estas condiciones, se invoca la excepción de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve un código de error y establece **errno** como se indica en la tabla.

## <a name="remarks"></a>Observaciones

La función **wcstombs_s** convierte una cadena de caracteres anchos a la que apunta *wcstr* en caracteres multibyte almacenados en el búfer al que apunta *mbstr*. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:

- Se encuentre un carácter ancho nulo

- Se encuentre un carácter ancho que no se pueda convertir

- El número de bytes almacenados en el búfer de *mbstr* es igual a *Count*.

La cadena de destino siempre termina en nulo (aun en caso de error).

Si *Count* es el valor especial [_TRUNCATE](../../c-runtime-library/truncate.md), **wcstombs_s** convierte la parte de la cadena que quepa en el búfer de destino, a la vez que deja espacio para un terminador null. Si se trunca la cadena, el valor devuelto es **STRUNCATE**y la conversión se considera correcta.

Si **wcstombs_s** convierte correctamente la cadena de origen, coloca el tamaño en bytes de la cadena convertida, incluido el terminador null, en *&#42;PReturnValue* (proporcionado *pReturnValue* no es **null**). Esto ocurre incluso si el argumento *mbstr* es **null** y proporciona una manera de determinar el tamaño de búfer necesario. Tenga en cuenta que si *mbstr* es **null**, *Count* se omite.

Si **wcstombs_s** encuentra un carácter ancho que no se puede convertir en un carácter multibyte, pone 0 en *&#42;pReturnValue*, establece el búfer de destino en una cadena vacía, establece **errno** en **EILSEQ**y devuelve **EILSEQ**.

Si las secuencias señaladas por *wcstr* y *mbstr* se superponen, el comportamiento de **wcstombs_s** es indefinido.

> [!IMPORTANT]
> Asegúrese de que *wcstr* y *mbstr* no se superponen y que el *recuento* refleja correctamente el número de caracteres anchos que se van a convertir.

**wcstombs_s** usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; **_wcstombs_s_l** es idéntica a **wcstombs** , salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**wcstombs_s**|\<stdlib.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este programa muestra el comportamiento de la función **wcstombs_s** .

```C
// crt_wcstombs_s.c
// This example converts a wide character
// string to a multibyte character string.
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>

#define BUFFER_SIZE 100

int main( void )
{
    size_t   i;
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );
    wchar_t*pWCBuffer = L"Hello, world.";

    printf( "Convert wide-character string:\n" );

    // Conversion
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,
               pWCBuffer, (size_t)BUFFER_SIZE );

    // Output
    printf("   Characters converted: %u\n", i);
    printf("    Multibyte character: %s\n\n",
     pMBBuffer );

    // Free multibyte character buffer
    if (pMBBuffer)
    {
    free(pMBBuffer);
    }
}
```

```Output
Convert wide-character string:
   Characters converted: 14
    Multibyte character: Hello, world.
```

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
