---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
ms.date: 4/2/2020
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
- _o__strtoui64
- _o__strtoui64_l
- _o__wcstoui64
- _o__wcstoui64_l
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
ms.openlocfilehash: 430d72595aadc677fe51d9ed868e4388071decec
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912448"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

Convierte una cadena en un valor de **__int64** sin signo.

## <a name="syntax"></a>Sintaxis

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*strSource*<br/>
Cadena terminada en NULL que se va a convertir.

*endptr*<br/>
Puntero al carácter que detiene el examen.

*base*<br/>
Base numérica que se va a usar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_strtoui64** devuelve el valor representado en la cadena *strSource*, excepto cuando la representación provocaría un desbordamiento, en cuyo caso devuelve **_UI64_MAX**. **_strtoui64** devuelve 0 si no se puede realizar ninguna conversión.

**_UI64_MAX** se define en límites. C.

Si *strSource* es **null** o la *base* es distinta de cero y menor que 2 o mayor que 36, **errno** se establece en **EINVAL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Observaciones

La función **_strtoui64** convierte *strSource* en un __int64 **sin signo** **__int64**. **_wcstoui64** es una versión con caracteres anchos de **_strtoui64**; su argumento *strSource* es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

Ambas funciones dejan de leer la cadena *strSource* en el primer carácter que no reconocen como parte de un número. Puede tratarse del carácter nulo final o puede ser el primer carácter numérico mayor o igual que *base*.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

La configuración de la categoría **LC_NUMERIC** de la configuración regional actual determina el reconocimiento del carácter de base en *strSource*; para obtener más información, vea [setlocale](setlocale-wsetlocale.md). Las funciones sin el sufijo _l usan la configuración regional actual; **_strtoui64_l** y **_wcstoui64_l** son idénticos a las funciones correspondientes sin el sufijo **_L** , salvo que usan la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no es **null**, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que apunta *endptr*. Si no se puede realizar ninguna conversión (no se encontraron dígitos válidos o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación a la que apunta *endptr*.

**_strtoui64** espera que *strSource* señale a una cadena con el formato siguiente:

> [*espacio en blanco*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **x** }]] [*dígitos* &#124; *Letras*]

Un espacio en *blanco* puede constar de caracteres de espacio y tabulación, que se omiten. los *dígitos* son uno o más dígitos decimales. las *Letras* son una o varias letras de la ' a ' a la ' z ' (o de la ' a ' a la ' z '). El primer carácter que no se ajusta a este formato detiene el análisis. Si *base* se encuentra entre 2 y 36, se utiliza como base del número. Si *base* es 0, los caracteres iniciales de la cadena a la que apunta *strSource* se usan para determinar la base. Si el primer carácter es 0 y el segundo carácter no es 'x' ni 'X', la cadena se interpreta como entero octal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras de la "a" a la "z" (o de la "A" a la "Z") se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que *base*. El primer carácter que está fuera del intervalo de la base detiene el análisis. Por ejemplo, si *base* es 0 y el primer carácter examinado es "0", se supone un entero octal y un carácter "8" o "9" detendrá el examen.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<stdlib.h> o \<wchar.h>|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
