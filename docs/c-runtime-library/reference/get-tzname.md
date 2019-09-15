---
title: _get_tzname
ms.date: 10/22/2018
api_name:
- _get_tzname
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
ms.openlocfilehash: 9f86a4997c328e86597e3bad8a7f7a3a5f5f50b6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955622"
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

*index*<br/>
Índice de uno de los dos nombres de zona horaria que se van a recuperar.

|*index*|Contenido de *TimeZoneName*|valor predeterminado de *TimeZoneName*|
|-|-|-|
|0|Nombre de zona horaria|"PST"|
|1|Nombre de zona de hora estándar de horario de verano|"PDT"|
|> 1 o < 0|**errno** establecido en **EINVAL**|no modificado|

A menos que los valores se cambien explícitamente durante el tiempo de ejecución, los valores predeterminados son "PST" y "PDT", respectivamente.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto; de lo contrario, un valor de tipo **errno** .

Si *TimeZoneName* es **null**, o *sizeInBytes* es cero o menor que cero (pero no ambos), se invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **EINVAL**.

### <a name="error-conditions"></a>Condiciones de error

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Valor devuelto|Contenido de *TimeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|tamaño de nombre de ZH|**NULL**|0|0 o 1|0|no modificado|
|tamaño de nombre de ZH|any|> 0|0 o 1|0|Nombre de ZH|
|no modificado|**NULL**|> 0|any|**EINVAL**|no modificado|
|no modificado|any|cero|any|**EINVAL**|no modificado|
|no modificado|any|> 0|> 1|**EINVAL**|no modificado|

## <a name="remarks"></a>Comentarios

La función **_get_tzname** recupera la representación de la cadena de caracteres del nombre de la zona horaria actual o el nombre de la zona horaria estándar de horario de verano (DST) en la dirección de *TimeZoneName* según el valor de índice, junto con el tamaño de la cadena en *pReturnValue*. Si *TimeZoneName* es **null** y *sizeInBytes* es cero, se devuelve el tamaño de la cadena necesaria para contener la zona horaria especificada y un valor null de terminación en bytes en *pReturnValue*. Los valores de índice deben ser 0 para la zona horaria estándar o 1 para la zona horaria estándar de horario de verano; cualquier otro valor de *index* tiene resultados indeterminados.

## <a name="example"></a>Ejemplo

En este ejemplo se llama a **_get_tzname** para obtener el tamaño de búfer necesario para mostrar el nombre de la zona horaria estándar de horario de verano actual, se asigna un búfer de ese tamaño, se llama de nuevo a **_get_tzname** para cargar el nombre en el búfer y se imprime en la consola.

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

### <a name="output"></a>Resultados

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Administración del tiempo](../../c-runtime-library/time-management.md)<br/>
[errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
