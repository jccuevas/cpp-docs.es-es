---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 4/2/2020
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
- _o__mbsnbcnt
- _o__mbsnbcnt_l
- _o__mbsnccnt
- _o__mbsnccnt_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
ms.openlocfilehash: bfd339a38dd5df30ece72059525860603ee10748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364180"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Devuelve el número de caracteres o bytes de un recuento especificado.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**y **_mbsnccnt_l** no se pueden usar en aplicaciones que se ejecutan en Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
size_t _strncnt(
   const char *str,
   size_t count
);
size_t _wcsncnt(
   const wchar_t *str,
   size_t count
);
size_t _mbsnbcnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnbcnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
size_t _mbsnccnt(
   const unsigned char *str,
   size_t count
);
size_t _mbsnccnt_l(
   const unsigned char *str,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Cadena que se va a examinar.

*count*<br/>
Número de caracteres o bytes que se examinarán en *str*.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbsnbcnt** y **_mbsnbcnt_l** devuelven el número de bytes encontrados en el primer *recuento* de caracteres multibyte de *str*. **_mbsnccnt** y **_mbsnccnt_l** devuelven el número de caracteres que se encuentran en el primer *recuento* de bytes de *str*. Si se encuentra un carácter nulo antes de que se haya completado el examen de *str,* devuelven el número de bytes o caracteres encontrados antes del carácter nulo. Si *str* consta de menos de *contar* caracteres o bytes, devuelven el número de caracteres o bytes de la cadena. Si *count* es menor que cero, devuelven 0. En versiones anteriores, estas funciones tenían un valor devuelto de tipo **int** en lugar de **size_t**.

**_strncnt** devuelve el número de caracteres de los primeros bytes de *recuento* de la cadena de un solo byte *str*. **_wcsncnt** devuelve el número de caracteres del primer *recuento* de caracteres anchos de la cadena de caracteres *anchos str*.

## <a name="remarks"></a>Observaciones

**_mbsnbcnt** y **_mbsnbcnt_l** cuentan el número de bytes encontrados en el primer *recuento* de caracteres multibyte de *str*. **_mbsnbcnt** y **_mbsnbcnt_l** reemplazar **mtob** y debe utilizarse en lugar de **mtob**.

**_mbsnccnt** y **_mbsnccnt_l** recuento del número de caracteres que se encuentran en el primer *recuento* de bytes de *str*. Si **_mbsnccnt** y **_mbsnccnt_l** encuentran un carácter nulo en el segundo byte de un carácter de doble byte, el primer byte también se considera null y no se incluye en el valor de recuento devuelto. **_mbsnccnt** y **_mbsnccnt_l** reemplazar **btom** y debe utilizarse en lugar de **btom**.

Si *str* es un puntero **NULL** o es *count* es 0, estas funciones invocan el controlador de parámetros no válidos como se describe en [Validación](../../c-runtime-library/parameter-validation.md)de parámetros , **errno** se establece en **EINVAL**y la función devuelve 0.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|-------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnbcnt**|**_strncnt**|**_mbsnbcnt**|**_wcsncnt**|
|**_tcsnccnt**|**_strncnt**|**_mbsnbcnt**|N/D|
|**_wcsncnt**|N/D|N/D|**_mbsnbcnt**|
|**_wcsncnt**|N/D|N/D|**_mbsnccnt**|
|N/D|N/D|**_mbsnbcnt_l**|**_mbsnccnt_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbcnt**|\<mbstring.h>|
|**_mbsnbcnt_l**|\<mbstring.h>|
|**_mbsnccnt**|\<mbstring.h>|
|**_mbsnccnt_l**|\<mbstring.h>|
|**_strncnt**|\<tchar.h>|
|**_wcsncnt**|\<tchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_mbsnbcnt.c

#include  <mbstring.h>
#include  <stdio.h>

int main( void )
{
   unsigned char str[] = "This is a multibyte-character string.";
   unsigned int char_count, byte_count;
   char_count = _mbsnccnt( str, 10 );
   byte_count = _mbsnbcnt( str, 10 );
   if ( byte_count - char_count )
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );
   else
      printf( "The first 10 characters are single-byte.\n");
}
```

### <a name="output"></a>Output

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>Consulte también

[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
