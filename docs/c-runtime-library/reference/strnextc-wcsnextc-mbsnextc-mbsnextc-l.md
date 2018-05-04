---
title: _strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strnextc
- _mbsnextc_l
- _mbsnextc
- _wcsnextc
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
apitype: DLLExport
f1_keywords:
- strnextc
- tcsnextc
- _mbsnextc_l
- _mbsnextc
- mbsnextc_l
- ftcsnextc
- mbsnextc
- _tcsnextc
- _wcsnextc
- _ftcsnextc
- _strnextc
- wcsnextc
dev_langs:
- C++
helpviewer_keywords:
- _mbsnextc function
- _tcsnextc function
- _wcsnextc function
- tcsnextc function
- strnextc function
- mbsnextc function
- _strnextc function
- _mbsnextc_l function
- mbsnextc_l function
- wcsnextc function
ms.assetid: e3086173-9eb5-4540-a23a-5d866bd05340
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f759ce9a4617ab0ca8e97ef308508d836b53b742
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="strnextc-wcsnextc-mbsnextc-mbsnextcl"></a>_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l

Busca el siguiente carácter de una cadena.

> [!IMPORTANT]
> **_mbsnextc** y **_mbsnextc_l** no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _strnextc(
   const char *str
);
unsigned int _wscnextc(
   const wchar_t *str
);
unsigned int _mbsnextc(
   const unsigned char *str
);
unsigned int _mbsnextc_l(
   const unsigned char *str,
   _locale_t locale
);

```

### <a name="parameters"></a>Parámetros

*str*<br/>
Cadena de origen.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el valor entero del siguiente carácter en *str*.

## <a name="remarks"></a>Comentarios

El **_mbsnextc** función devuelve el valor entero del siguiente carácter multibyte en *str*, sin avanzar el puntero de cadena. **_mbsnextc** reconoce las secuencias de caracteres multibyte según la [página de códigos multibyte](../../c-runtime-library/code-pages.md) actualmente en uso.

Si *str* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve 0.

**Nota de seguridad** Esta API crea la posible amenaza de un problema de saturación del búfer. Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnextc**|**_strnextc**|**_mbsnextc**|**_wcsnextc**|

**_strnextc** y **_wcsnextc** son versiones de cadena de caracteres anchos de y de cadena de caracteres de byte único **_mbsnextc**. **_wcsnextc** devuelve el valor entero del siguiente carácter ancho en *str*; **_strnextc** devuelve el valor entero del siguiente carácter de un solo byte en *str*. **_strnextc** y **_wcsnextc** se proporcionan solo para esta asignación y no debe usarse en caso contrario. Para obtener más información, vea [Usar asignaciones de texto genérico](../../c-runtime-library/using-generic-text-mappings.md) y [Asignaciones de texto genérico](../../c-runtime-library/generic-text-mappings.md).

**_mbsnextc_l** es idéntica, salvo que usa el parámetro locale pasado en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnextc**|\<mbstring.h>|
|**_mbsnextc_l**|\<mbstring.h>|
|**_strnextc**|\<tchar.h>|
|**_wcsnextc**|\<tchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strdec, _wcsdec, _mbsdec, _mbsdec_l](strdec-wcsdec-mbsdec-mbsdec-l.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
