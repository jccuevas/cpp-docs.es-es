---
title: _strrev, _wcsrev, _mbsrev, _mbsrev_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _wcsrev
- _mbsrev
- _strrev
- _mbsrev_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strrev
- _ftcsrev
- _tcsrev
- mbsrev
- mbsrev_l
- _wcsrev_fstrrev
- _mbsrev
dev_langs:
- C++
helpviewer_keywords:
- _mbsrev_l function
- characters [C++], switching
- _mbsrev function
- strrev function
- _ftcsrev function
- strings [C++], reversing
- wcsrev function
- _strrev function
- mbsrev_l function
- reversing characters in strings
- ftcsrev function
- characters [C++], reversing order
- _wcsrev function
- mbsrev function
- tcsrev function
- _tcsrev function
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8b925b3c67dda4d29208a7027bb7905502df432
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="strrev-wcsrev-mbsrev-mbsrevl"></a>_strrev, _wcsrev, _mbsrev, _mbsrev_l

Invierte los caracteres de una cadena.

> [!IMPORTANT]
> **_mbsrev** y **_mbsrev_l** no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char *_strrev(
   char *str
);
wchar_t *_wcsrev(
   wchar_t *str
);
unsigned char *_mbsrev(
   unsigned char *str
);
unsigned char *_mbsrev_l(
   unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Cadena terminada en NULL que se va a invertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la cadena modificada. No se reserva ningún valor devuelto para indicar un error.

## <a name="remarks"></a>Comentarios

El **_strrev** función invierte el orden de los caracteres de *str*. El carácter nulo de finalización no cambia de lugar. **_wcsrev** y **_mbsrev** son versiones de caracteres multibyte y anchos de **_strrev**. Los argumentos y el valor devuelto de **_wcsrev** son caracteres anchos cadenas; los de **_mbsrev** son cadenas de caracteres multibyte. Para **_mbsrev**, el orden de bytes de cada carácter multibyte en *str* no cambia. Estas tres funciones se comportan exactamente igual.

**_mbsrev** valida sus parámetros. Si el valor *string1* o *string2* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_mbsrev** devuelve **NULL** y establece **errno** a **EINVAL**. **_strrev** y **_wcsrev** no validan sus parámetros.

El valor de salida se ve afectado por el valor de la **LC_CTYPE** valor de la categoría de la configuración regional; vea [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones son idénticas, salvo que las que no tienen la **_l** sufijo usan la configuración regional actual y las que tienen la **_l** sufijo en su lugar, use el parámetro de configuración regional que pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Estas funciones pueden ser vulnerables a amenazas de saturación del búfer. Las saturaciones del búfer se pueden usar para ataques del sistema, ya que pueden producir una elevación de privilegios no justificada. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrev**|**_strrev**|**_mbsrev**|**_wcsrev**|
|**N/D**|**N/D**|**_mbsrev_l**|**N/D**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strrev**|\<string.h>|
|**_wcsrev**|\<string.h> o \<wchar.h>|
|**_mbsrev**, **_mbsrev_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strrev.c
// This program checks a string to see
// whether it is a palindrome: that is, whether
// it reads the same forward and backward.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char* string = "Able was I ere I saw Elba";
   int result;

   // Reverse string and compare (ignore case):
   result = _stricmp( string, _strrev( _strdup( string ) ) );
   if( result == 0 )
      printf( "The string \"%s\" is a palindrome\n", string );
   else
      printf( "The string \"%s\" is not a palindrome\n", string );
}
```

```Output
The string "Able was I ere I saw Elba" is a palindrome
```

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
