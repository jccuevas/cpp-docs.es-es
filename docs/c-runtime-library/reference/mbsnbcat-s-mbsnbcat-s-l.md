---
title: _mbsnbcat_s, _mbsnbcat_s_l
ms.date: 11/04/2016
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: 8a3f66f8fc8d4fd659880e8793fdaae635f9f7ba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952272"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>_mbsnbcat_s, _mbsnbcat_s_l

Anexa a una cadena de caracteres multibyte, como máximo, los primeros **n** bytes de otra cadena de caracteres multibyte. Se trata de versiones de [_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md) que tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Cadena de destino de caracteres multibyte terminada en NULL.

*sizeInBytes*<br/>
Tamaño del búfer de *destino* en bytes.

*src*<br/>
Cadena de origen de caracteres multibyte terminada en NULL.

*count*<br/>
Número de bytes de *src* que se van a anexar al *destino*.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto; en caso contrario, código de error.

### <a name="error-conditions"></a>Condiciones de error

|**Dest**|*sizeInBytes*|*src*|Valor devuelto|
|------------|-------------------|-----------|------------------|
|**NULL**|any|any|**EINVAL**|
|Cualquiera|<= 0|any|**EINVAL**|
|Cualquiera|any|**NULL**|**EINVAL**|

Si se produce alguna de las condiciones de error, la función genera un error de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se controla el error, la función devuelve **EINVAL** y establece **errno** en **EINVAL**.

## <a name="remarks"></a>Comentarios

La función **_mbsnbcat_s** anexa a *dest*, como máximo, el primer *número* de bytes de *src*. Si el byte que precede inmediatamente al carácter nulo de *dest* es un byte inicial, lo sobrescribe el byte inicial de *src*. De lo contrario, el byte inicial de *src* sobrescribe el carácter nulo de finalización de *dest*. Si aparece un byte nulo en *src* antes de que se anexen bytes de *recuento* , **_mbsnbcat_s** anexa todos los bytes de *src*, hasta el carácter nulo. Si el *recuento* es mayor que la longitud de *src*, se usa la longitud de *src* en lugar de *Count*. La cadena resultante se termina con un carácter nulo. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.

El valor de salida se ve afectado por la configuración de la categoría **LC_CTYPE** de la configuración regional. vea [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones son idénticas, salvo que las que no tienen el sufijo **_L** usan la configuración regional actual y las que tienen el sufijo **_L** usan en su lugar el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden inferir automáticamente la longitud de búfer, lo que elimina la necesidad de especificar un argumento de tamaño, y pueden usar automáticamente funciones más recientes y seguras para reemplazar las funciones anteriores no seguras. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
