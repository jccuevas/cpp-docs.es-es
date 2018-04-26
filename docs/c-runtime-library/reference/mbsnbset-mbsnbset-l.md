---
title: _mbsnbset, _mbsnbset_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _mbsnbset
- _mbsnbset_l
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
- mbsnbset
- mbsnbset_l
- _mbsnbset
- _mbsnbset_l
dev_langs:
- C++
helpviewer_keywords:
- tcsnset function
- _tcsnset_l function
- _mbsnbset function
- _tcsnset function
- _mbsnbset_l function
- mbsnbset_l function
- tcsnset_l function
- mbsnbset function
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 462e435c1b93561cf5ca21dd20ad2025ac6f9661
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="mbsnbset-mbsnbsetl"></a>_mbsnbset, _mbsnbset_l

Establece el primer argumento **n** bytes de una cadena de caracteres multibyte en un carácter especificado. Hay disponibles versiones más seguras de estas funciones; vea [_mbsnbset_s, _mbsnbset_s_l](mbsnbset-s-mbsnbset-s-l.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
unsigned char *_mbsnbset(
   unsigned char *str,
   unsigned int c,
   size_t count
);
unsigned char *_mbsnbset_l(
   unsigned char *str,
   unsigned int c,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Cadena que se va a modificar.

*c*<br/>
Valor del carácter de un solo byte o multibyte.

*count*<br/>
Número de bytes que se van a establecer.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_mbsnbset** devuelve un puntero a la cadena modificada.

## <a name="remarks"></a>Comentarios

El **_mbsnbset** y **_mbsnbset_l** funciones establecen, como máximo, los primeros *recuento* bytes de *str* a *c*. Si *recuento* es mayor que la longitud de *str*, la longitud de *str* se utiliza en lugar de *recuento*. Si *c* es un carácter multibyte y no se puede establecer totalmente en el último byte especificado por *recuento*, el último byte se completa con un carácter en blanco. **_mbsnbset** y **_mbsnbset_l** , no se establecerá una terminación null al final de *str*.

**_mbsnbset** y **_mbsnbset_l** es similar a **_mbsnset**, salvo que establece *recuento* bytes en lugar de *recuento* caracteres de *c*.

Si *str* es **NULL** o *recuento* es cero, esta función genera una excepción de parámetro no válido, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**. Además, si *c* no es un carácter multibyte válido, **errno** está establecido en **EINVAL** y un espacio se utiliza en su lugar.

El valor de salida se ve afectado por el valor de la **LC_CTYPE** valor de la categoría de la configuración regional; vea [setlocale](setlocale-wsetlocale.md) para obtener más información. El **_mbsnbset** versión de esta función usa la configuración regional actual para este comportamiento dependiente de la configuración regional; la **_mbsnbset_l** versión es idéntica, salvo que usa el parámetro locale pasado en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

**Nota de seguridad** Esta API crea la posible amenaza de un problema de saturación del búfer. Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnset**|**_strnset**|**_mbsnbset**|**_wcsnset**|
|**_tcsnset_l**|**_strnset_l**|**_mbsnbset_l**|**_wcsnset_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mbsnbset**|\<mbstring.h>|
|**_mbsnbset_l**|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_mbsnbset.c
// compile with: /W3
#include <mbstring.h>
#include <stdio.h>

int main( void )
{
   char string[15] = "This is a test";
   /* Set not more than 4 bytes of string to be *'s */
   printf( "Before: %s\n", string );
   _mbsnbset( string, '*', 4 ); // C4996
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s
   printf( "After:  %s\n", string );
}
```

### <a name="output"></a>Salida

```Output
Before: This is a test
After:  **** is a test
```

## <a name="see-also"></a>Vea también

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
