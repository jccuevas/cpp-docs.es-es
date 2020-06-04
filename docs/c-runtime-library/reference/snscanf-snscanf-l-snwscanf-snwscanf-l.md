---
title: _snscanf, _snscanf_l, _snwscanf, _snwscanf_l
ms.date: 11/04/2016
api_name:
- _snwscanf
- _snscanf_l
- _snscanf
- _snwscanf_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _snscanf
- _snscanf_l
- _snwscanf
- snscanf_l
- snscanf
- _sntscanf_l
- _sntscanf
- _snwscanf_l
- sntscanf_l
- sntscanf
- snwscanf
- snwscanf_l
helpviewer_keywords:
- snscanf_l function
- snwscanf function
- _sntscanf_l function
- sntscanf function
- _snwscanf_l function
- _sntscanf function
- _snscanf_l function
- sntscanf_l function
- strings [C++], reading data from
- snscanf function
- snwscanf_l function
- _snwscanf function
- reading data, strings
- strings [C++], reading
- _snscanf function
ms.assetid: da1ac890-f905-4cd7-954b-3c90957b5551
ms.openlocfilehash: f259eede1b2927b4676467c3450504f7ff7c19de
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947942"
---
# <a name="_snscanf-_snscanf_l-_snwscanf-_snwscanf_l"></a>_snscanf, _snscanf_l, _snwscanf, _snwscanf_l

Lee datos con formato de una longitud especificada a partir de una cadena. Hay disponibles versiones más seguras de estas funciones; vea [_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md).

## <a name="syntax"></a>Sintaxis

```C
int __cdecl _snscanf(
   const char * input,
   size_t length,
   const char * format,
   ...
);
int __cdecl _snscanf_l(
   const char * input,
   size_t length,
   const char * format,
   locale_t locale,
   ...
);
int __cdecl _snwscanf(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   ...
);
int __cdecl _snwscanf_l(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   locale_t locale,
   ...
);
```

### <a name="parameters"></a>Parámetros

*input*<br/>
Cadena de entrada que se va a examinar.

*length*<br/>
Número de caracteres que se van a examinar en la *entrada*.

*format*<br/>
Uno o varios especificadores de formato.

*...*<br/>
Variables opcionales que se usarán para almacenar los valores extraídos de la cadena de entrada mediante los especificadores de formato en *formato*.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el número de campos convertidos y asignados correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es **EOF** para un error o si el final de la cadena se alcanza antes de la primera conversión. Para obtener más información, vea [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md).

Si la *entrada* o el *formato* es un puntero **nulo** , o si la *longitud* es menor o igual que cero, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EOF** y establecen **errno** en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Esta función es como **sscanf** , salvo que proporciona la capacidad de especificar un número fijo de caracteres que se van a examinar desde la cadena de entrada. Para obtener más información, vea [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md).

Las versiones de estas funciones con el sufijo **_L** son idénticas, salvo que utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf**|**_snscanf**|**_snscanf**|**_snwscanf**|
|**_sntscanf_l**|**_snscanf_l**|**_snscanf_l**|**_snwscanf_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_snscanf**, **_snscanf_l**|\<stdio.h>|
|**_snwscanf**, **_snwscanf_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_snscanf.c
// compile with: /W3

#include <stdio.h>
int main( )
{
   char  str1[] = "15 12 14...";
   wchar_t  str2[] = L"15 12 14...";
   char  s1[3];
   wchar_t  s2[3];
   int   i;
   float fp;

   i = _snscanf( str1, 6,  "%s %f", s1, &fp); // C4996
   // Note: _snscanf is deprecated; consider using _snscanf_s instead
   printf("_snscanf converted %d fields: ", i);
   printf("%s and %f\n", s1, fp);

   i = _snwscanf( str2, 6,  L"%s %f", s2, &fp); // C4996
   // Note: _snwscanf is deprecated; consider using _snwscanf_s instead
   wprintf(L"_snwscanf converted %d fields: ", i);
   wprintf(L"%s and %f\n", s2, fp);
}
```

```Output
_snscanf converted 2 fields: 15 and 12.000000
_snwscanf converted 2 fields: 15 and 12.000000
```

## <a name="see-also"></a>Vea también

[scanf (especificación de ancho)](../../c-runtime-library/scanf-width-specification.md)<br/>
