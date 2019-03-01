---
title: memcmp, wmemcmp
ms.date: 11/04/2016
apiname:
- memcmp
- wmemcmp
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memcmp
- wmemcmp
helpviewer_keywords:
- wmemcmp function
- memcmp function
ms.assetid: 0c21c3e3-8ee4-40e5-add1-eb26d225fd8d
ms.openlocfilehash: 4feaa692ced7777d757b579c1b131b541dccea66
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210242"
---
# <a name="memcmp-wmemcmp"></a>memcmp, wmemcmp

Compara los caracteres de dos búferes.

## <a name="syntax"></a>Sintaxis

```C
int memcmp(
   const void *buffer1,
   const void *buffer2,
   size_t count
);
int wmemcmp(
   const wchar_t * buffer1,
   const wchar_t * buffer2,
   size_t count
);
```

### <a name="parameters"></a>Parámetros

*buffer1*<br/>
Primer búfer.

*buffer2*<br/>
Segundo búfer.

*count*<br/>
Número de caracteres que se van a comparar. (Compara los bytes de **memcmp**, caracteres anchos para **wmemcmp**).

## <a name="return-value"></a>Valor devuelto

El valor devuelto indica la relación entre los búferes.

|Valor devuelto|Relación de primera *recuento* caracteres de buf1 y buf2|
|------------------|---------------------------------------------------------------|
|< 0|*buffer1* menor *buffer2*|
|0|*buffer1* idéntico al *buffer2*|
|> 0|*buffer1* mayor *buffer2*|

## <a name="remarks"></a>Comentarios

Compara los primeros *recuento* caracteres de *buffer1* y *buffer2* y devuelve un valor que indica su relación. El signo de un valor devuelto distinto de cero es el signo de la diferencia entre el primer par de valores de los búferes. Los valores se interpretan como **sin signo** **char** para **memcmp**y como **wchar_t** para **wmemcmp**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**memcmp**|\<memory.h> o \<string.h>|
|**wmemcmp**|\<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de la [biblioteca en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_memcmp.c
/* This program uses memcmp to compare
* the strings named first and second. If the first
* 19 bytes of the strings are equal, the program
* considers the strings to be equal.
*/

#include <string.h>
#include <stdio.h>

int main( void )
{
   char first[]  = "12345678901234567890";
   char second[] = "12345678901234567891";
   int int_arr1[] = {1,2,3,4};
   int int_arr2[] = {1,2,3,4};
   int result;

   printf( "Compare '%.19s' to '%.19s':\n", first, second );
   result = memcmp( first, second, 19 );
   if( result < 0 )
      printf( "First is less than second.\n" );
   else if( result == 0 )
      printf( "First is equal to second.\n" );
   else
      printf( "First is greater than second.\n" );

   printf( "Compare '%d,%d' to '%d,%d':\n", int_arr1[0], int_arr1[1], int_arr2[0], int_arr2[1]);
   result = memcmp( int_arr1, int_arr2, sizeof(int) * 2 );
   if( result < 0 )
      printf( "int_arr1 is less than int_arr2.\n" );
   else if( result == 0 )
      printf( "int_arr1 is equal to int_arr2.\n" );
   else
      printf( "int_arr1 is greater than int_arr2.\n" );
}
```

```Output
Compare '1234567890123456789' to '1234567890123456789':
First is equal to second.
Compare '1,2' to '1,2':
int_arr1 is equal to int_arr2.
```

## <a name="see-also"></a>Vea también

[Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
