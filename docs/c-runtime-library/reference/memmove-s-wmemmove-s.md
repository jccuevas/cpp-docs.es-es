---
title: memmove_s, wmemmove_s
ms.date: 4/2/2020
api_name:
- wmemmove_s
- memmove_s
- _o_wmemmove_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: 04f920543c4f6a3d433e6426a96d617a3608a270
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914098"
---
# <a name="memmove_s-wmemmove_s"></a>memmove_s, wmemmove_s

Mueve un búfer a otro. Se trata de versiones de [memmove, wmemmove](memmove-wmemmove.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t memmove_s(
   void *dest,
   size_t numberOfElements,
   const void *src,
   size_t count
);
errno_t wmemmove_s(
   wchar_t *dest,
   size_t numberOfElements,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Objeto de destino.

*numberOfElements*<br/>
Tamaño del búfer de destino.

*src*<br/>
Objeto de origen.

*count*<br/>
Número de bytes (**memmove_s**) o caracteres (**wmemmove_s**) que se van a copiar.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error

### <a name="error-conditions"></a>Condiciones de error

|*dest*|*numberOfElements*|*src*|Valor devuelto|Contenido de *dest*|
|------------|------------------------|-----------|------------------|------------------------|
|**ACEPTA**|cualquiera|cualquiera|**EINVAL**|no modificado|
|cualquiera|cualquiera|**ACEPTA**|**EINVAL**|no modificado|
|cualquiera|< *recuento*|cualquiera|**ERANGE**|no modificado|

## <a name="remarks"></a>Observaciones

Copia los bytes de *número* de caracteres de *src* a *dest*. Si algunas regiones del área de origen y de destino se superponen, **memmove_s** garantiza que se copian los bytes de origen originales en la región superpuesta antes de que se sobrescriban.

Si *dest* o si *src* es un puntero nulo, o si la cadena de destino es demasiado pequeña, estas funciones invocan un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones devuelven **EINVAL** y establecen **errno** en **EINVAL**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**memmove_s**|\<string.h>|
|**wmemmove_s**|\<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_memmove_s.c
//
// The program demonstrates the
// memmove_s function which works as expected
// for moving overlapping regions.

#include <stdio.h>
#include <string.h>

int main()
{
   char str[] = "0123456789";

   printf("Before: %s\n", str);

   // Move six bytes from the start of the string
   // to a new position shifted by one byte. To protect against
   // buffer overrun, the secure version of memmove requires the
   // the length of the destination string to be specified.

   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);

   printf_s(" After: %s\n", str);
}
```

### <a name="output"></a>Salida

```Output
Before: 0123456789
After: 0012345789
```

## <a name="see-also"></a>Vea también

[Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
