---
title: _itoa, _itow (funciones)
ms.date: 08/19/2019
apiname:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: afe7a190fe6630e3fbcb42d0d782e050952f56fc
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630407"
---
# <a name="itoa-_itoa-ltoa-_ltoa-ultoa-_ultoa-_i64toa-_ui64toa-_itow-_ltow-_ultow-_i64tow-_ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Convierte un entero en cadena. Hay disponibles versiones más seguras de estas funciones; vea [_itoa_s, _itow_s Functions](itoa-s-itow-s.md).

## <a name="syntax"></a>Sintaxis

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These Posix versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>Parámetros

*value*<br/>
Número que se va a convertir.

*buffer*<br/>
Búfer que contiene el resultado de la conversión.

*radix*<br/>
Base que se va a usar para la conversión de *valor*, que debe estar en el intervalo 2-36.

*size*<br/>
Longitud del búfer en unidades del tipo de carácter. Este parámetro se deduce del argumento *buffer* en C++.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve un puntero al *búfer*. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

Las funciones **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**y **ui64toa** convierten los dígitos del argumento de *valor* dado en una cadena de caracteres terminada en NULL y almacenan el resultado (hasta 33 caracteres para **_itoa** , **_ltoa**y **_ultoa**, y 65 para **_i64toa** y **ui64toa**) en el *búfer*. Si la *base* es igual a 10 y el *valor* es negativo, el primer carácter de la cadena almacenada es **-** el signo menos (). Las funciones **_itow**, **_ltow**, **_ultow**, **_i64tow**y **_ui64tow** son versiones de caracteres anchos de **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**y **ui64toa**, respectivamente.

> [!IMPORTANT]
> Estas funciones pueden escribir más allá del final de un búfer que es demasiado pequeño. Para evitar las saturaciones del búfer, asegúrese de que el *búfer* sea lo suficientemente grande como para contener los dígitos convertidos más el carácter nulo final y un carácter de signo. El uso incorrecto de estas funciones puede provocar serios problemas de seguridad en el código.

Debido a su potencial de problemas de seguridad, de forma predeterminada, estas funciones causan [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)de advertencia de desuso: **Esta función o variable puede no ser segura. Considere la** posibilidad de usar *safe_function* **en su lugar. Para deshabilitar el desuso, utilice _CRT_SECURE_NO_WARNINGS.** Se recomienda cambiar el código fuente para usar el *safe_function* sugerido por el mensaje de advertencia. Las funciones más seguras no escriben más caracteres que el tamaño de búfer especificado. Para obtener más información, vea [_itoa_s, _itow_s Functions](itoa-s-itow-s.md).

Para usar estas funciones sin la advertencia de desuso, defina la macro de preprocesador **_CRT_SECURE_NO_WARNINGS** antes de incluir los encabezados de CRT. Puede hacerlo en la línea de comandos en un símbolo del sistema para desarrolladores agregando la opción del compilador **/D_CRT_SECURE_NO_WARNINGS** al comando **cl** . En caso contrario, defina la macro en los archivos de código fuente. Si usa encabezados precompilados, defina la macro en la parte superior del encabezado precompilado include File, *PCH. h* (*stdafx. h* en Visual Studio 2017 y versiones anteriores). Para definir la macro en el código fuente, use una directiva de **#define** antes de incluir cualquier encabezado de CRT, como en este ejemplo:

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

En C++, estas funciones tienen sobrecargas de plantilla que invocan sus homólogos más seguros. Para obtener más información, consulta [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Los nombres POSIX **itoa**, **ltoa**y **ultoa** existen como alias para las funciones **_itoa**, **_ltoa**y **_ultoa** . Los nombres POSIX están en desuso porque no siguen las convenciones de nombres de funciones específicas de la implementación de ISO C. De forma predeterminada, estas funciones causan [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)de advertencia de desuso: **El nombre POSIX de este elemento está en desuso. En su lugar, use ISO C y C++ el nombre compatible:** *new_name*. Se recomienda cambiar el código fuente para usar las versiones más seguras de estas funciones, **_itoa_s**, **_ltoa_s**o **_ultoa_s**. Para obtener más información, vea [_itoa_s, _itow_s Functions](itoa-s-itow-s.md).

En cuanto a la portabilidad del código fuente, puede que prefiera conservar los nombres POSIX en el código. Para usar estas funciones sin la advertencia de desuso, defina las macros de preprocesador **_CRT_NONSTDC_NO_WARNINGS** y **_CRT_SECURE_NO_WARNINGS** antes de incluir los encabezados de CRT. Puede hacerlo en la línea de comandos en un símbolo del sistema para desarrolladores agregando las opciones del compilador **/D_CRT_SECURE_NO_WARNINGS** y **/D_CRT_NONSTDC_NO_WARNINGS** al comando **cl** . En caso contrario, defina las macros en los archivos de código fuente. Si usa encabezados precompilados, defina las macros en la parte superior del archivo de inclusión del encabezado precompilado. Para definir las macros en el código fuente, utilice las directivas de **#define** antes de incluir cualquier encabezado de CRT, como en este ejemplo:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Macros de recuento de conversión máximo

Para ayudarle a crear búferes seguros para las conversiones, CRT incluye algunas macros útiles. Estos definen el tamaño del búfer necesario para convertir el valor más largo posible de cada tipo entero, incluidos el carácter nulo y el terminador null, para varias bases comunes. Para asegurarse de que el búfer de conversión es lo suficientemente grande como para recibir cualquier conversión enla base especificada por la base, utilice una de estas macros definidas al asignar el búfer. Esto ayuda a evitar errores de saturación del búfer al convertir tipos enteros en cadenas. Estas macros se definen al incluir stdlib. h o WCHAR. h en el origen.

Para usar una de estas macros en una función de conversión de cadenas, declare el búfer de conversión del tipo de carácter adecuado y use el valor de la macro para el tipo entero y base como dimensión de búfer. En esta tabla se enumeran las macros adecuadas para cada función de las bases enumeradas:

||||
|-|-|-|
|Funciones|radix|Macros|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

En este ejemplo se usa una macro de recuento de conversión para definir un búfer lo suficientemente grande como para contener un largo **sin signo** en base 2:

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h> o \<wchar.h>|

Estas funciones y macros son específicas de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este ejemplo muestra el uso de algunas de las funciones de conversión de enteros. Observe el uso de la macro **_CRT_SECURE_NO_WARNINGS** para silenciar la advertencia C4996.

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s, _itow_s (funciones)](itoa-s-itow-s.md)<br/>
