---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 11/04/2016
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 18af20b5722364ea306daebdcb77f5771d8ea2b5
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703069"
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l

Convertir una secuencia de caracteres multibyte en una secuencia correspondiente de caracteres anchos. Versiones de [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*pReturnValue*<br/>
El número de caracteres convertidos.

*wcstr*<br/>
Dirección del búfer para la cadena de caracteres anchos convertida.

*sizeInWords*<br/>
El tamaño de la *wcstr* búfer en palabras.

*mbstr*<br/>
Dirección de una secuencia de caracteres multibyte terminados en nulo.

*count*<br/>
El número máximo de caracteres anchos a almacenar en el *wcstr* búfer, sin incluir el terminador nulo, o [_TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.

|Condición de error|Valor devuelto y **errno**|
|---------------------|------------------------------|
|*wcstr* es **NULL** y *sizeInWords* > 0|**EINVAL**|
|*mbstr* es **NULL**|**EINVAL**|
|El búfer de destino es demasiado pequeño para contener la cadena convertida (a menos que *recuento* es **_TRUNCATE**; vea Comentarios más abajo)|**ERANGE**|
|*wcstr* no **NULL** y *sizeInWords* == 0|**EINVAL**|

Si se produce alguna de estas condiciones, se invoca la excepción de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve un código de error y establece **errno** como se indica en la tabla.

## <a name="remarks"></a>Comentarios

El **mbstowcs_s** función convierte una cadena de caracteres multibyte que apunta *mbstr* en caracteres anchos almacenados en el búfer señalado por *wcstr*. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:

- Se encuentra un carácter multibyte nulo

- Se encuentra un carácter multibyte no válido

- El número de caracteres anchos almacenados en el *wcstr* búfer equals *recuento*.

La cadena de destino siempre termina en nulo (aun en caso de error).

Si *recuento* es el valor especial [_TRUNCATE](../../c-runtime-library/truncate.md), a continuación, **mbstowcs_s** convierte tanto de la cadena como cabe en el búfer de destino, dejando espacio para un valor null terminador.

Si **mbstowcs_s** convierte correctamente la cadena de origen, pone el tamaño en caracteres anchos de la cadena convertida, incluido el terminador nulo, en  *&#42;pReturnValue* (proporcionado *pReturnValue* no **NULL**). Esto ocurre incluso si la *wcstr* argumento es **NULL** y proporciona una manera de determinar el tamaño de búfer necesario. Observe que si *wcstr* es **NULL**, *recuento* se omite, y *sizeInWords* debe ser 0.

Si **mbstowcs_s** encuentra un carácter multibyte no válido, pone 0 en  *&#42;pReturnValue*, Establece el búfer de destino en una cadena vacía, establece **errno** a  **EILSEQ**y devuelve **EILSEQ**.

Si las secuencias señaladas por *mbstr* y *wcstr* se superponen, el comportamiento de **mbstowcs_s** es indefinido.

> [!IMPORTANT]
> Asegúrese de que *wcstr* y *mbstr* no se superponen y que *recuento* refleja correctamente el número de caracteres multibyte a convertir.

**mbstowcs_s** usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; **_mbstowcs_s_l** es idéntico, salvo que usa la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
