---
title: _set_printf_count_output
ms.date: 11/04/2016
api_name:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d53b4e4c56a69582a4eb517fa1a5c9e10cd7d2f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948419"
---
# <a name="_set_printf_count_output"></a>_set_printf_count_output

Habilitar o deshabilitar la compatibilidad con el formato **% n** en las funciones [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-Family.

## <a name="syntax"></a>Sintaxis

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Parámetros

*enable*<br/>
Un valor distinto de cero para habilitar la compatibilidad con **% n** , 0 para deshabilitar la compatibilidad con **% n** .

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

El estado de **% n** es compatible antes de llamar a esta función: distinto de cero si se habilitó la compatibilidad con **% n** , 0 si estaba deshabilitada.

## <a name="remarks"></a>Comentarios

Por motivos de seguridad, la compatibilidad con el especificador de formato **% n** está deshabilitada de forma predeterminada en **printf** y en todas sus variantes. Si se encuentra **% n** en una especificación de formato **printf** , el comportamiento predeterminado es invocar el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). La llamada a **_set_printf_count_output** con un argumento distinto de cero provocará que las funciones de la familia **printf**interpreten **% n** como se describe en [Sintaxis de especificación de formato: funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>Vea también

[_get_printf_count_output](get-printf-count-output.md)<br/>
