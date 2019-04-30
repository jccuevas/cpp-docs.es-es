---
title: _set_printf_count_output
ms.date: 11/04/2016
apiname:
- _set_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 0d4847d850b39c7c03ea92a98499715b1e6a4913
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356529"
---
# <a name="setprintfcountoutput"></a>_set_printf_count_output

Habilitar o deshabilitar la compatibilidad de la **%n** formatear en [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-familia de funciones.

## <a name="syntax"></a>Sintaxis

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Parámetros

*enable*<br/>
Un valor distinto de cero para habilitar **%n** admitir, 0 para deshabilitar **%n** admite.

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

El estado de **%n** admite antes de llamar a esta función: distinto de cero if **%n** se ha habilitado la compatibilidad, 0 si se deshabilitó.

## <a name="remarks"></a>Comentarios

Por motivos de seguridad, compatibilidad con la **%n** especificador de formato está deshabilitado de forma predeterminada en **printf** y todas sus variantes. Si **%n** se encuentra en un **printf** especificación de formato, el comportamiento predeterminado consiste en invocar el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Una llamada a **_set_printf_count_output** con un argumento distinto de cero provocará **printf**-familia de funciones para interpretar **%n** como se describe en [formato Sintaxis de especificación: funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

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
