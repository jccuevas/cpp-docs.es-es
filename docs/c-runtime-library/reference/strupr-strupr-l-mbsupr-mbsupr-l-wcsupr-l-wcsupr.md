---
title: _strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mbsupr_l
- _mbsupr
- _strupr_l
- _wcsupr
- _wcsupr_l
- _strupr
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
- ntoskrnl.exe
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbsupr
- _ftcsupr
- mbsupr
- _tcsupr
- strupr_l
- _fstrupr
- _strupr
- mbsupr_l
- _wcsupr
dev_langs:
- C++
helpviewer_keywords:
- tcsupr_l function
- mbsupr function
- strupr function
- uppercase, converting strings to
- wcsupr function
- _wcsupr function
- string conversion [C++], case
- ftcsupr function
- _ftcsupr function
- _wcsupr_l function
- wcsupr_l function
- strings [C++], case
- tcsupr function
- _tcsupr_l function
- _fstrupr function
- _strupr_l function
- _mbsupr_l function
- converting case, CRT functions
- fstrupr function
- mbsupr_l function
- strupr_l function
- _strupr function
- _mbsupr function
- _tcsupr function
- strings [C++], converting case
ms.assetid: caac8f16-c233-41b6-91ce-575ec7061b77
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a1b9300abfc68e1d6044e1eec290bdb0625c1b80
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="strupr-struprl-mbsupr-mbsuprl-wcsuprl-wcsupr"></a>_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr

Cambia la cadena a mayúsculas. Hay disponibles versiones más seguras de estas funciones; vea [_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md).

> [!IMPORTANT]
> **_mbsupr** y **_mbsupr_l** no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *_strupr(
   char *str
);
wchar_t *_wcsupr(
   wchar_t *str
);
unsigned char *_mbsupr(
   unsigned char *str
);
char *_strupr_l(
   char *str,
   _locale_t locale
);
wchar_t *_wcsupr_l(
   wchar_t *str,
   _locale_t locale
);
unsigned char *_mbsupr_l(
   unsigned char *str,
   _locale_t locale
);
template <size_t size>
char *_strupr(
   char (&str)[size]
); // C++ only
template <size_t size>
wchar_t *_wcsupr(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
unsigned char *_mbsupr(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
char *_strupr_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
wchar_t *_wcsupr_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
unsigned char *_mbsupr_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Cadena que se va a poner en mayúsculas.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la cadena modificada. Dado que la modificación se hace en contexto, el puntero devuelto es el mismo que el puntero que se pasa como argumento de entrada. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Comentarios

El **_strupr** función convierte, en su lugar, cada minúscula de *str* a mayúsculas. La conversión viene determinada por la **LC_CTYPE** valor de la categoría de la configuración regional. Otros caracteres no resultan afectados. Para obtener más información sobre **LC_CTYPE**, consulte [setlocale](setlocale-wsetlocale.md). Las versiones de estas funciones sin el **_l** sufijo use la configuración regional actual; las versiones con el **_l** sufijo son idénticas salvo que usan la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

**_wcsupr** y **_mbsupr** son versiones de caracteres multibyte y anchos de **_strupr**. El argumento y el valor devuelto de **_wcsupr** son caracteres anchos cadenas; los de **_mbsupr** son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.

Si *str* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones devuelven la cadena original y establecen **errno** a **EINVAL**.

En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsupr**|**_strupr**|**_mbsupr**|**_wcsupr**|
|**_tcsupr_l**|**_strupr_l**|**_mbsupr_l**|**_wcsupr_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strupr**, **_strupr_l**|\<string.h>|
|**_wcsupr**, **_wcsupr_l**|\<string.h> o \<wchar.h>|
|**_mbsupr**, **_mbsupr_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_strlwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md).

## <a name="see-also"></a>Vea también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)<br/>
