---
title: _mbsnbcpy_s, _mbsnbcpy_s_l
ms.date: 4/2/2020
api_name:
- _mbsnbcpy_s_l
- _mbsnbcpy_s
- _o__mbsnbcpy_s
- _o__mbsnbcpy_s_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbcpy_s_l
- _mbsnbcpy_s
- mbsnbcpy_s
- _mbsnbcpy_s_l
helpviewer_keywords:
- _mbsnbcpy_s function
- tcsncpy_s function
- mbsnbcpy_s_l function
- _tcsncpy_s_l function
- mbsnbcpy_s function
- tcsncpy_s_l function
- _mbsnbcpy_s_l function
- _tcsncpy_s function
ms.assetid: dfff64ab-fe6f-49c4-99ba-75014e2b0cd6
ms.openlocfilehash: 670055ca67e8196805851767596f56028350e32a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911887"
---
# <a name="_mbsnbcpy_s-_mbsnbcpy_s_l"></a>_mbsnbcpy_s, _mbsnbcpy_s_l

Copia **n** bytes de una cadena en una cadena de destino. Estas versiones de [_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md) incluyen mejoras de seguridad, tal como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _mbsnbcpy_s(
   unsigned char * strDest,
   size_t sizeInBytes,
   const unsigned char * strSource,
   size_t count
);
errno_t _mbsnbcpy_s_l(
   unsigned char * strDest,
   size_t sizeInBytes,
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcpy_s(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcpy_s_l(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*strDest*<br/>
Destino de la cadena de caracteres que se va a copiar.

*sizeInBytes*<br/>
Tamaño del búfer de destino.

*strSource*<br/>
Cadena de caracteres que se va a copiar.

*count*<br/>
Número de bytes que se van a copiar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto; **EINVAL** si se pasó un parámetro incorrecto.

## <a name="remarks"></a>Observaciones

La función **_mbsnbcpy_s** copia el *número* de bytes de *strSource* a *strDest*. Si *Count* supera el tamaño de *strDest*, cualquiera de las cadenas de entrada es un puntero nulo, o *sizeInBytes* o *Count* es 0, la función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, la función devuelve **EINVAL**. Si las cadenas de origen y de destino se superponen, el comportamiento de **_mbsnbcpy_s** es indefinido.

El valor de salida se ve afectado por el valor de la categoría **LC_CTYPE** de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

> [!NOTE]
> A diferencia de la versión no segura de esta función, **_mbsnbcpy_s** no realiza ningún relleno nulo y siempre termina en NULL la cadena.

En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

Las versiones de la biblioteca de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncpy_s**|**_strncpy_s**|**_mbsnbcpy_s**|**_wcsncpy_s**|
|**_tcsncpy_s_l**|**_strncpy_s_l**|**_mbsnbcpy_s_l**|**_wcsncpy_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbcpy_s**|\<mbstring.h>|
|**_mbsnbcpy_s_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
