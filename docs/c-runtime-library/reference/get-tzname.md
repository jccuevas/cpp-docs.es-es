---
title: _get_tzname | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _get_tzname
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_tzname
- get_tzname
dev_langs:
- C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d773d5d98466963ef621cc3fa7bc5ab8b4acc40a
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990313"
---
# <a name="gettzname"></a>_get_tzname

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
La longitud de cadena de *timeZoneName* incluido un terminador nulo.

*timeZoneName*<br/>
La dirección de una cadena de caracteres para la representación de nombre de zona horaria o el nombre de zona de hora estándar de horario de verano (DST), según *índice*.

*sizeInBytes*<br/>
El tamaño de la *timeZoneName* en bytes de la cadena de caracteres.

*index*<br/>
Índice de uno de los dos nombres de zona horaria que se van a recuperar.

|*index*|Contenido de *timeZoneName*|*timeZoneName* valor predeterminado|
|-|-|-|
|0|Nombre de zona horaria|"PST"|
|1|Nombre de zona de hora estándar de horario de verano|"PDT"|
|> 1 o < 0|**errno** establecido en **EINVAL**|no modificado|

A menos que los valores se cambien explícitamente durante el tiempo de ejecución, los valores predeterminados son "PST" y "PDT", respectivamente.

## <a name="return-value"></a>Valor devuelto

Cero si es correcto, en caso contrario, un **errno** tipo de valor.

Si bien *timeZoneName* es **NULL**, o *sizeInBytes* es cero o menor que cero (pero no ambos), se invoca un controlador de parámetros no válidos, como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** a **EINVAL** y devuelve **EINVAL**.

### <a name="error-conditions"></a>Condiciones de error

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|Valor devuelto|Contenido de *timeZoneName*|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|tamaño de nombre de ZH|**NULL**|0|0 o 1|0|no modificado|
|tamaño de nombre de ZH|any|> 0|0 o 1|0|Nombre de ZH|
|no modificado|**NULL**|> 0|any|**EINVAL**|no modificado|
|no modificado|any|cero|any|**EINVAL**|no modificado|
|no modificado|any|> 0|> 1|**EINVAL**|no modificado|

## <a name="remarks"></a>Comentarios

El **_get_tzname** función recupera la representación de cadena de caracteres de nombre de zona horaria actual o el nombre de zona de hora estándar de horario de verano (DST) en la dirección de *timeZoneName* en función de la índice de valor, junto con el tamaño de la cadena en *pReturnValue*. Si *timeZoneName* es **NULL** y *sizeInBytes* es cero, el tamaño de la cadena necesaria para almacenar la zona horaria especificada y se devuelve un valor null de terminación en bytes en *pReturnValue*. Los valores de índice deben ser 0 para la zona horaria estándar o 1 para la zona horaria estándar de horario de verano; cualquier otro valor de *índice* tienen resultados indeterminados.

## <a name="example"></a>Ejemplo

Este ejemplo llama a **_get_tzname** obtener el tamaño de búfer necesario para mostrar el nombre de zona de hora estándar de horario de verano actual, asigna un búfer de ese tamaño, las llamadas **_get_tzname** nuevo para cargar el nombre en el almacene en búfer y lo imprime en la consola.

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

### <a name="output"></a>Salida

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
