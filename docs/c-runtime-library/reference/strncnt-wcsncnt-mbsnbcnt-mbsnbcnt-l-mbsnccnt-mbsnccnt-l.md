---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
ms.date: 11/04/2016
api_name:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
ms.openlocfilehash: 4c00ae3ff845dfbc3daf4a3ea6ce5c34c43e475f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947298"
---
# <a name="_strncnt-_wcsncnt-_mbsnbcnt-_mbsnbcnt_l-_mbsnccnt-_mbsnccnt_l"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l

Devuelve el número de caracteres o bytes de un recuento especificado.

> [!IMPORTANT]
> **_mbsnbcnt**, **_mbsnbcnt_l**, **_mbsnccnt**y **_mbsnccnt_l** no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Cadena que se va a examinar.

*count*<br/>
Número de caracteres o bytes que se van a examinar en *Str*.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbsnbcnt** y **_mbsnbcnt_l** devuelven el número de bytes que se encuentran en el primer *recuento* de caracteres multibyte de *Str*. **_mbsnccnt** y **_mbsnccnt_l** devuelven el número de caracteres que se encuentran en el primer *recuento* de bytes de *Str*. Si se encuentra un carácter nulo antes de que se haya completado el examen de *Str* , devuelven el número de bytes o caracteres encontrados antes del carácter nulo. Si *Str* consta de menos de caracteres de *recuento* o bytes, devuelve el número de caracteres o bytes de la cadena. Si *Count* es menor que cero, devuelven 0. En versiones anteriores, estas funciones tenían un valor devuelto de tipo **int** en lugar de **size_t**.

**_strncnt** devuelve el número de caracteres en el primer *número* de bytes de la cadena de un solo byte *Str*. **_wcsncnt** devuelve el número de caracteres en el primer número de caracteres anchos de la cadena de *caracteres anchos* *Str*.

## <a name="remarks"></a>Comentarios

**_mbsnbcnt** y **_mbsnbcnt_l** cuentan el número de bytes que se encuentran en el primer *recuento* de caracteres multibyte de *Str*. **_mbsnbcnt** y **_mbsnbcnt_l** reemplazan a **mtob** y deben usarse en lugar de **mtob**.

**_mbsnccnt** y **_mbsnccnt_l** cuentan el número de caracteres que se encuentran en el primer *recuento* de bytes de *Str*. Si **_mbsnccnt** y **_mbsnccnt_l** encuentran un carácter nulo en el segundo byte de un carácter de doble byte, el primer byte también se considera NULL y no se incluye en el valor de recuento devuelto. **_mbsnccnt** y **_mbsnccnt_l** reemplazan a **btom** y deben usarse en lugar de **btom**.

Si *Str* es un puntero **nulo** o *Count* es 0, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md), **errno** se establece en **EINVAL**y la función devuelve 0.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

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

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

### <a name="output"></a>Resultados

```Output
The first 10 characters are single-byte.
```

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
