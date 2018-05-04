---
title: strftime, wcsftime, _strftime_l, _wcsftime_l | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
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
- _tcsftime
- strftime
- wcsftime
- _strftime_l
- _wcsftime_l
dev_langs:
- C++
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 573e89b7be9818ac45f70c7c614e3bf7869c95f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

Da formato a una cadena de hora.

## <a name="syntax"></a>Sintaxis

```C
size_t strftime(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr
);
size_t _strftime_l(
   char *strDest,
   size_t maxsize,
   const char *format,
   const struct tm *timeptr,
   _locale_t locale
);
size_t wcsftime(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr
);
size_t _wcsftime_l(
   wchar_t *strDest,
   size_t maxsize,
   const wchar_t *format,
   const struct tm *timeptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*strDest*<br/>
Cadena de salida

*MaxSize*<br/>
Tamaño de la *strDest* búfer, en caracteres (**char** o **wchar_t**).

*format*<br/>
Cadena de control de formato.

*timeptr*<br/>
**TM** estructura de datos.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**strftime** devuelve el número de caracteres que se colocan en *strDest* y **wcsftime** devuelve el número correspondiente de caracteres anchos.

Si el número total de caracteres, incluido el carácter null final, es más de *maxsize*, ambos **strftime** y **wcsftime** devuelven 0 y el contenido de  *strDest* son indeterminados.

El número de caracteres en *strDest* es igual al número de caracteres literales de *formato* , así como los caracteres que pueden agregarse a *formato* a través de códigos de formato. El carácter nulo final de una cadena no se contabiliza en el valor devuelto.

## <a name="remarks"></a>Comentarios

El **strftime** y **wcsftime** formato funciones el **tm** hora con el valor en *timeptr* según proporcionado  *formato* argumento y el resultado en el búfer de la tienda *strDest*. A lo sumo, *maxsize* caracteres se colocan en la cadena. Para obtener una descripción de los campos de la *timeptr* estructura, vea [asctime](asctime-wasctime.md). **wcsftime** es el equivalente de caracteres anchos de **strftime**; su argumento de puntero de cadena señala a una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

Esta función valida sus parámetros. Si *strDest*, *formato*, o *timeptr* es un puntero nulo, o si la **tm** estructura de datos mencionado en *timeptr* no es válida (por ejemplo, si contiene valores fuera del intervalo para la fecha u hora), o si la *formato* cadena contiene un código de formato no válido, se invoca el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve 0 y establece **errno** a **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

El *formato* argumento se compone de uno o más códigos; como en **printf**, los códigos de formato están precedidos por un signo de porcentaje (**%**). Caracteres que no comienzan por **%** se copiarán sin ninguna modificación a *strDest*. El **LC_TIME** categoría de la configuración regional actual afecta al formato de salida de **strftime**. (Para obtener más información sobre **LC_TIME**, consulte [setlocale](setlocale-wsetlocale.md).) El **strftime** y **wcsftime** funciones usan el conjunto actual configuración regional. El **_strftime_l** y **_wcsftime_l** versiones de estas funciones son idénticas salvo que se toman la configuración regional como parámetro y que utilice el conjunto actual configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

El **strftime** funciones admiten estos códigos de formato:

|||
|-|-|
|Código|Cadena de reemplazo|
|**%a)**|Nombre de día de la semana abreviado en la configuración regional|
|**%A)**|Nombre del día completo en la configuración regional|
|**%b**|Nombre abreviado del mes en la configuración regional|
|**%B**|Nombre completo del mes en la configuración regional|
|**%c**|Representación de fecha y hora adecuada para la configuración regional|
|**%C**|El año se divide en 100 y se trunca a un entero, como un número decimal (00−99)|
|**%d**|Día del mes como un número decimal (01-31)|
|**%D**|Equivalente a **%m/%d/%y**|
|**%e**|Día del mes como un número decimal (1-31), donde decena está precedido por un espacio|
|**%F**|Equivalente a **%Y %m-%d**|
|**%g**|Los últimos 2 dígitos del año ISO 8601 basado en la semana como un número decimal (00 – 99)|
|**%G**|El año de ISO 8601 basado en la semana como un número decimal|
|**%h**|Nombre abreviado del mes (equivalente a **%b**)|
|**%H**|Hora en formato de 24 horas (00 – 23)|
|**%I**|Hora en formato de 12 horas (01-12)|
|**%j**|Día del año como un número decimal (001-366)|
|**%m**|Mes como un número decimal (01-12)|
|**%M**|Minuto como un número decimal (00 - 59)|
|**%n**|Un carácter de nueva línea (**\n**)|
|**%p**|A.m./P.M. de la configuración regional. Indicador de reloj de 12 horas|
|**%r**|Tiempo de reloj de 12 horas de la configuración regional|
|**%R**|Equivalente a **% H: %M**|
|**%S**|Segundo como un número decimal (00 - 59)|
|**%t**|Un carácter de tabulación horizontal (**\t**)|
|**%T**|Equivalente a **H: % M: %S**, el formato de hora ISO 8601|
|**%u**|Día de la semana ISO 8601 como un número decimal (1-7; El lunes es 1)|
|**%U**|Número de semana del año como un número decimal (00 - 53), donde el primer domingo es el primer día de la semana 1|
|**%V**|Número de semana ISO 8601 como un número decimal (00 - 53)|
|**%w**|Día de la semana como un número decimal (0 - 6; El domingo es 0)|
|**%W**|Número de semana del año como un número decimal (00 - 53), donde el primer lunes es el primer día de la semana 1|
|**%x**|Representación de fecha para la configuración regional|
|**%X**|Representación de hora para la configuración regional|
|**%y**|Año sin el siglo, como número decimal (00 – 99)|
|**%Y**|Año con siglo como número decimal|
|**%z**|El desplazamiento de UTC en formato ISO 8601; ningún carácter si no se conoce la zona horaria|
|**%Z**|Del ya sea la configuración regional nombre de zona horaria o abreviatura de la zona horaria, dependiendo de la configuración del registro; ningún carácter si no se conoce la zona horaria|
|**%%**|Signo de porcentaje|

Como en el **printf** función, el **#** marca puede anteponer cualquier código de formato. En ese caso, el significado del código de formato cambia del siguiente modo.

|Código de formato|Significado|
|-----------------|-------------|
|**% #a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X** , **%#z**, **%#Z**, **%#%**|**#** se omite la marca.|
|**%#c**|Tiempo fecha y hora representación, adecuado para la configuración regional. Por ejemplo: "Martes, 14 de marzo de 1995, 12:41:29".|
|**%#x**|Representación de fecha larga, adecuado para la configuración regional. Por ejemplo: "Martes, 14 de marzo de 1995".|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **% #I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T** , **%#U**, **%#V**, **%#W**, **%#y**, **%#Y**|Quitar ceros o espacios (si existe).|

La semana ISO 8601 y año semana-based producidas por **%V**, **%g**, y **%G**, usa una semana que empieza el lunes, donde 1 semana es la semana que contiene mayo de enero 4 de, que es el primer elemento semana que incluye al menos cuatro días del año. Si el primer lunes del año es la 2, 3 o 4 de mayo, los días anteriores forman parte de la última semana del año anterior. Durante esos días, **%V** se sustituye por 53 y ambos **%g** y **%G** se reemplazan por los dígitos del año anterior.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> o \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> o \<wchar.h>|

El **_strftime_l** y **_wcsftime_l** funciones son específicos de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [time](time-time32-time64.md).

## <a name="see-also"></a>Vea también

[Configuración regional](../../c-runtime-library/locale.md) <br/>
[Administración del tiempo](../../c-runtime-library/time-management.md) <br/>
[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
