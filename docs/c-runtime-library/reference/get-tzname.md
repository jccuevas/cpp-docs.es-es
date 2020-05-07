---
title: _get_tzname
ms.date: 4/2/2020
api_name:
- _get_tzname
- _o__get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: bf63b0ade0adc0a2dfa471bbfbeebc0cb2d04911
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919681"
---
# <a name="_get_tzname"></a>_get_tzname

Recupera la representación de cadena de caracteres del nombre de zona horaria o el nombre de zona de hora estándar de horario de verano (DST).

## <a name="syntax"></a>Sintaxis

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>Parámetros

*pReturnValue*<br/>
La longitud de cadena de *TimeZoneName* , incluido un terminador null.

*timeZoneName*<br/>
La dirección de una cadena de caracteres para la representación del nombre de zona horaria o el nombre de zona horaria estándar de horario de verano (DST), dependiendo del *Índice*.

*sizeInBytes*<br/>
Tamaño de la cadena de caracteres *TimeZoneName* en bytes.

*índice*<br/>
Índice de uno de los dos nombres de zona horaria que se van a recuperar.

|*índice*|Contenido de *TimeZoneName*|valor predeterminado de *TimeZoneName*|
|-|-|-|
|0|Nombre de zona horaria|"PST"|
|1|Nombre de zona de hora estándar de horario de verano|"PDT"|
|> 1 o < 0|**errno** establecido en **EINVAL**|no modificado|

A menos que los valores se cambien explícitamente durante el tiempo de ejecución, los valores predeterminados son "PST" y "PDT", respectivamente.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto; de lo contrario, un valor de tipo **errno** .

Si *TimeZoneName* es **null**, o *sizeInBytes* es cero o menor que cero (pero no ambos), se invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **EINVAL**.

### <a name="error-conditions"></a>Condiciones de error

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*índice*|Valor devuelto|Contenido de *TimeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|tamaño de nombre de ZH|**ACEPTA**|0|0 o 1|0|no modificado|
|tamaño de nombre de ZH|cualquiera|> 0|0 o 1|0|Nombre de ZH|
|no modificado|**ACEPTA**|> 0|cualquiera|**EINVAL**|no modificado|
|no modificado|cualquiera|cero|cualquiera|**EINVAL**|no modificado|
|no modificado|cualquiera|> 0|> 1|**EINVAL**|no modificado|

## <a name="remarks"></a>Observaciones

La función **_get_tzname** recupera la representación de la cadena de caracteres del nombre de zona horaria actual o el nombre de la zona horaria estándar de horario de verano (DST) en la dirección de *TimeZoneName* en función del valor de índice, junto con el tamaño de la cadena en *pReturnValue*. Si *TimeZoneName* es **null** y *sizeInBytes* es cero, se devuelve el tamaño de la cadena necesaria para contener la zona horaria especificada y un valor null de terminación en bytes en *pReturnValue*. Los valores de índice deben ser 0 para la zona horaria estándar o 1 para la zona horaria estándar de horario de verano; cualquier otro valor de *index* tiene resultados indeterminados.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="example"></a>Ejemplo

Este ejemplo llama a **_get_tzname** para obtener el tamaño de búfer necesario para mostrar el nombre de la zona horaria estándar de horario de verano actual, asigna un búfer de ese tamaño, llama a **_get_tzname** de nuevo para cargar el nombre en el búfer y lo imprime en la consola.

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>Output

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Administración de hora](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
