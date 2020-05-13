---
title: _memicmp, _memicmp_l
ms.date: 4/2/2020
api_name:
- _memicmp_l
- _memicmp
- _o__memicmp
- _o__memicmp_l
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _memicmp
- memicmp_l
- _memicmp_l
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
ms.openlocfilehash: 365b57dc300da5686895d66fa642e3870612c2ed
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915398"
---
# <a name="_memicmp-_memicmp_l"></a>_memicmp, _memicmp_l

Compara los caracteres de dos búferes (distingue entre mayúsculas y minúsculas).

## <a name="syntax"></a>Sintaxis

```C
int _memicmp(
   const void *buffer1,
   const void *buffer2,
   size_t count
);
int _memicmp_l(
   const void *buffer1,
   const void *buffer2,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*buffer1*<br/>
Primer búfer.

*buffer2*<br/>
Segundo búfer.

*count*<br/>
Número de caracteres.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

El valor devuelto indica la relación entre los búferes.

|Valor devuelto|Relación de los primeros count bytes de buf1 y buf2|
|------------------|--------------------------------------------------------|
|< 0|*buffer1* es menor que *buffer2*.|
|0|*buffer1* idéntico a *buffer2*.|
|> 0|*buffer1* mayor que *buffer2*.|
|**_NLSCMPERROR**|Se produjo un error.|

## <a name="remarks"></a>Observaciones

La función **_memicmp** compara los primeros caracteres de *recuento* de los dos búferes *buffer1* y *buffer2* byte por byte. La comparación no distingue entre mayúsculas y minúsculas.

Si *buffer1* o *buffer2* es un puntero nulo, esta función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve **_NLSCMPERROR** y establece **errno** en **EINVAL**.

**_memicmp** usa la configuración regional actual para el comportamiento dependiente de la configuración regional; **_memicmp_l** es idéntico, salvo que usa la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_memicmp**|\<memory.h> o \<string.h>|
|**_memicmp_l**|\<memory.h> o \<string.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_memicmp.c
// This program uses _memicmp to compare
// the first 29 letters of the strings named first and
// second without regard to the case of the letters.

#include <memory.h>
#include <stdio.h>
#include <string.h>

int main( void )
{
   int result;
   char first[] = "Those Who Will Not Learn from History";
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";
   // Note that the 29th character is right here ^

   printf( "Compare '%.29s' to '%.29s'\n", first, second );
   result = _memicmp( first, second, 29 );
   if( result < 0 )
      printf( "First is less than second.\n" );
   else if( result == 0 )
      printf( "First is equal to second.\n" );
   else if( result > 0 )
      printf( "First is greater than second.\n" );
}
```

```Output
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'
First is equal to second.
```

## <a name="see-also"></a>Consulte también

[Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
