---
title: _snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l
ms.date: 11/04/2016
api_name:
- _snwscanf_s_l
- _snwscanf_s
- _snscanf_s
- _snscanf_s_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sntscanf_s
- snscanf_s
- _snwscanf_s_l
- sntscanf_s_l
- snwscanf_s_l
- snwscanf_s
- _snscanf_s
- _snwscanf_s
- snscanf_s_l
- _sntscanf_s_l
- _snscanf_s_l
- sntscanf_s
helpviewer_keywords:
- _snscanf_s_l function
- snwscanf_s function
- _snwscanf_s function
- sntscanf_s_l function
- sntscanf_s function
- _snwscanf_s_l function
- _snscanf_s function
- snscanf_s_l function
- strings [C++], reading data from
- _sntscanf_s_l function
- reading data, strings
- snscanf_s function
- strings [C++], reading
- _sntscanf_s function
- snwscanf_s_l function
ms.assetid: 72356653-7362-461a-af73-597b9c0a8094
ms.openlocfilehash: 33507990c1b7e2c6fd1b30e2bdb9277ab611ef2a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947945"
---
# <a name="_snscanf_s-_snscanf_s_l-_snwscanf_s-_snwscanf_s_l"></a>_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l

Lee datos con formato de una longitud especificada a partir de una cadena. Se trata de versiones de [_snscanf, _snscanf_l, _snwscanf, _snwscanf_l](snscanf-snscanf-l-snwscanf-snwscanf-l.md) que incluyen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int __cdecl _snscanf_s(
   const char * input,
   size_t length,
   const char * format [, argument_list]
);
int __cdecl _snscanf_s_l(
   const char * input,
   size_t length,
   const char * format,
   locale_t locale [, argument_list]
);
int __cdecl _snwscanf_s(
   const wchar_t * input,
   size_t length,
   const wchar_t * format [, argument_list]
);
int __cdecl _snwscanf_s_l(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   locale_t locale [, argument_list]
);
```

### <a name="parameters"></a>Parámetros

*input*<br/>
Cadena de entrada que se va a examinar.

*length*<br/>
Número de caracteres que se van a examinar en la *entrada*.

*format*<br/>
Uno o varios especificadores de formato.

*locale*<br/>
Configuración regional que se va a usar.

*argument_list*<br/>
Argumentos opcionales que se van a asignar según la cadena de formato.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el número de campos convertidos y asignados correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es **EOF** para un error o si el final de la cadena se alcanza antes de la primera conversión. Para obtener más información, vea [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

Si la *entrada* o el *formato* es un puntero **nulo** , se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EOF** y establecen **errno** en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Esta función es como **sscanf_s** , salvo que proporciona la capacidad de especificar un número fijo de caracteres que se van a examinar desde la cadena de entrada. Para obtener más información, vea [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

El parámetro de tamaño de búfer es necesario con los caracteres de campo de tipo **c**, **c**, **s**, **s**y **[** . Para obtener más información, vea [scanf (Caracteres de campo de tipo)](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> El parámetro de tamaño es de tipo sin **signo**, no **size_t**.

Las versiones de estas funciones con el sufijo **_L** son idénticas, salvo que utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf_s**|**_snscanf_s**|**_snscanf_s**|**_snwscanf_s**|
|**_sntscanf_s_l**|**_snscanf_s_l**|**_snscanf_s_l**|**_snwscanf_s_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_snscanf_s**, **_snscanf_s_l**|\<stdio.h>|
|**_snwscanf_s**, **_snwscanf_s_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_snscanf_s.c
// This example scans a string of
// numbers, using both the character
// and wide character secure versions
// of the snscanf function.

#include <stdio.h>

int main( )
{
    char        str1[] = "15 12 14...";
    wchar_t     str2[] = L"15 12 14...";
    char        s1[3];
    wchar_t     s2[3];
    int         i;
    float       fp;

    i = _snscanf_s( str1, 6,  "%s %f", s1, 3, &fp);
    printf_s("_snscanf_s converted %d fields: ", i);
    printf_s("%s and %f\n", s1, fp);

    i = _snwscanf_s( str2, 6,  L"%s %f", s2, 3, &fp);
    wprintf_s(L"_snwscanf_s converted %d fields: ", i);
    wprintf_s(L"%s and %f\n", s2, fp);
}
```

```Output
_snscanf_s converted 2 fields: 15 and 12.000000
_snwscanf_s converted 2 fields: 15 and 12.000000
```

## <a name="see-also"></a>Vea también

[scanf (especificación de ancho)](../../c-runtime-library/scanf-width-specification.md)<br/>
