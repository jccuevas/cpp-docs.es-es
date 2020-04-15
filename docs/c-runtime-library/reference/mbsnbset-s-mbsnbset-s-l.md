---
title: _mbsnbset_s, _mbsnbset_s_l
ms.date: 4/2/2020
api_name:
- _mbsnbset_s_l
- _mbsnbset_s
- _o__mbsnbset_s
- _o__mbsnbset_s_l
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
- mbsnbset_s
- _mbsnbset_s_l
- _mbsnbset_s
- mbsnbset_s_l
helpviewer_keywords:
- tcsnset_s function
- mbsnbset_s function
- mbsnbset_s_l function
- _mbsnbset_s_l function
- _tcsnset_s_l function
- _mbsnbset_s function
- _tcsnset_s function
- tcsnset_s_l function
ms.assetid: 811f92c9-cc31-4bbd-8017-2d1bfc6fb96f
ms.openlocfilehash: 0ecfac1f9c0f1f9aeb8de85411b0b2f696b578e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81339021"
---
# <a name="_mbsnbset_s-_mbsnbset_s_l"></a>_mbsnbset_s, _mbsnbset_s_l

Establece los primeros **n** bytes de una cadena de caracteres multibyte en un carácter especificado. Estas versiones de [_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md) incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _mbsnbset_s(
   unsigned char *str,
   size_t size,
   unsigned int c,
   size_t count
);
errno_t _mbsnbset_s_l(
   unsigned char *str,
   size_t size,
   unsigned int c,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbset_s(
   unsigned char (&str)[size],
   unsigned int c,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbset_s_l(
   unsigned char (&str)[size],
   unsigned int c,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Cadena que se va a modificar.

*Tamaño*<br/>
Tamaño del búfer de cadena.

*C*<br/>
Valor del carácter de un solo byte o multibyte.

*count*<br/>
Número de bytes que se van a establecer.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto; en caso contrario, código de error.

## <a name="remarks"></a>Observaciones

Las funciones **_mbsnbset_s** y **_mbsnbset_s_l** establecen, como máximo, los primeros bytes de *recuento* de *str* a *c*. Si *count* es mayor que la longitud de *str*, se utiliza la longitud de *str* en lugar de *count*. Si *c* es un carácter multibyte y no se puede establecer completamente en el último byte especificado por *count*, el último byte se rellena con un carácter en blanco. **_mbsnbset_s** y **_mbsnbset_s_l** no colocan un valor null de terminación al final de *str*.

**_mbsnbset_s** y **_mbsnbset_s_l** se asemejan **a _mbsnset**, excepto que establecen bytes de *recuento* en lugar de *contar* caracteres de *c*.

Si *str* es **NULL** o *count* es cero, esta función genera una excepción de parámetro no válida, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece **en EINVAL** y la función devuelve **NULL**. Además, si *c* no es un carácter multibyte válido, **errno** se establece en **EINVAL** y se utiliza un espacio en su lugar.

El valor de salida se ve afectado por la configuración de la **LC_CTYPE** configuración de categoría de la configuración regional; ver [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. La **versión _mbsnbset_s** de esta función utiliza la configuración regional actual para este comportamiento dependiente de la configuración regional; la **versión _mbsnbset_s_l** es idéntica, excepto que en su lugar utiliza el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

En C++, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir automáticamente la longitud del búfer, lo que elimina la necesidad de especificar un argumento de tamaño. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset_s**|**_strnset_s**|**_mbsnbset_s**|**_wcsnset_s**|
|**_tcsnset_s_l**|`_strnset_s _l`|**_mbsnbset_s_l**|**_wcsnset_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbset_s**|\<mbstring.h>|
|**_mbsnbset_s_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_mbsnbset_s.c
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset_s( string, sizeof(string), '*', 4 );
   printf( "After:  %s\n", string );
}
```

## <a name="output"></a>Output

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Consulte también

[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
