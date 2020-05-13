---
title: _mbsnbcpy, _mbsnbcpy_l
ms.date: 4/2/2020
api_name:
- _mbsnbcpy
- _mbsnbcpy_l
- _o__mbsnbcpy
- _o__mbsnbcpy_l
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
- mbsnbcpy
- _mbsnbcpy
- mbsnbcpy_l
- _mbsnbcpy_l
helpviewer_keywords:
- mbsnbcpy function
- _mbsnbcpy_l function
- _mbsnbcpy function
- _tcsncpy function
- tcsncpy_l function
- _tcsncpy_l function
- mbsnbcpy_l function
- tcsncpy function
ms.assetid: 83d17b50-3cbf-4df9-bce8-3b6d52f85d04
ms.openlocfilehash: ea89458a51360b8781cb713fc9412239d2e03c78
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911894"
---
# <a name="_mbsnbcpy-_mbsnbcpy_l"></a>_mbsnbcpy, _mbsnbcpy_l

Copia **n** bytes de una cadena en una cadena de destino. Hay disponibles versiones más seguras de estas funciones; vea [_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
unsigned char * _mbsnbcpy(
   unsigned char * strDest,
   const unsigned char * strSource,
   size_t count
);
unsigned char * _mbsnbcpy_l(
   unsigned char * strDest,
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
unsigned char * _mbsnbcpy(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count
); // C++ only
template <size_t size>
unsigned char * _mbsnbcpy_l(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*strDest*<br/>
Destino de la cadena de caracteres que se va a copiar.

*strSource*<br/>
Cadena de caracteres que se va a copiar.

*count*<br/>
Número de bytes que se van a copiar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbsnbcpy** devuelve un puntero a la cadena de caracteres de destino. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Observaciones

La función **_mbsnbcpy** copia el *número* de bytes de *strSource* a *strDest*. Si *Count* supera el tamaño de *strDest* o las cadenas de origen y de destino se superponen, el comportamiento de **_mbsnbcpy** es indefinido.

Si *strSource* o *strDest* es un puntero nulo, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve **null** y establece **errno** en **EINVAL**.

El valor de salida se ve afectado por la configuración de la categoría **LC_CTYPE** de la configuración regional. vea [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones son idénticas, salvo que las que no tienen el sufijo **_L** usan la configuración regional actual y las versiones que tienen el sufijo **_L** usan en su lugar el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Estas funciones pueden ser vulnerables a amenazas de saturación del búfer. Las saturaciones del búfer pueden utilizarse para ejecutar código atacante arbitrario, lo que puede producir una elevación de privilegios ilícita y poner en peligro el sistema. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

En C++, estas funciones tienen sobrecargas de plantilla que invocan a los homólogos más recientes y seguros de dichas funciones. Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncpy**|[strncpy](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|**_mbsnbcpy**|[wcsncpy](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|
|**_tcsncpy_l**|**_strncpy_l**|**_mbsnbcp_l**|**_wcsncpy_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbcpy**|\<mbstring.h>|
|**_mbsnbcpy_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
