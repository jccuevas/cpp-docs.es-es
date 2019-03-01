---
title: memset, wmemset
ms.date: 11/04/2016
apiname:
- wmemset
- memset
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memset
- wmemset
helpviewer_keywords:
- wmemset function
- memset function
ms.assetid: e7ceb01b-df69-49c2-b294-a39358ad4699
ms.openlocfilehash: d517c5565ef07a834d7ef864e495a4bb33351007
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210073"
---
# <a name="memset-wmemset"></a>memset, wmemset

Establece búferes en un carácter especificado.

## <a name="syntax"></a>Sintaxis

```C
void *memset(
   void *dest,
   int c,
   size_t count
);
wchar_t *wmemset(
   wchar_t *dest,
   wchar_t c,
   size_t count
);
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Puntero al destino.

*c*<br/>
Carácter que se va a establecer.

*count*<br/>
Número de caracteres.

## <a name="return-value"></a>Valor devuelto

El valor de *dest*.

## <a name="remarks"></a>Comentarios

Establece los primeros *recuento* caracteres de *dest* al carácter *c*.

**Nota de seguridad** Asegúrese de que el búfer de destino tenga suficiente espacio para al menos *recuento* caracteres. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/desktop/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**memset**|\<memory.h> o \<string.h>|
|**wmemset**|\<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_memset.c
/* This program uses memset to
* set the first four chars of buffer to "*".
*/

#include <memory.h>
#include <stdio.h>

int main( void )
{
   char buffer[] = "This is a test of the memset function";

   printf( "Before: %s\n", buffer );
   memset( buffer, '*', 4 );
   printf( "After:  %s\n", buffer );
}
```

### <a name="output"></a>Salida

```Output
Before: This is a test of the memset function
After:  **** is a test of the memset function
```

A continuación se muestra un ejemplo del uso de wmemset:

```C
// crt_wmemset.c
/* This program uses memset to
* set the first four chars of buffer to "*".
*/

#include <wchar.h>
#include <stdio.h>

int main( void )
{
   wchar_t buffer[] = L"This is a test of the wmemset function";

   wprintf( L"Before: %s\n", buffer );
   wmemset( buffer, '*', 4 );
   wprintf( L"After:  %s\n", buffer );
}
```

### <a name="output"></a>Salida

```Output
Before: This is a test of the wmemset function
After:  **** is a test of the wmemset function
```

## <a name="see-also"></a>Vea también

[Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
