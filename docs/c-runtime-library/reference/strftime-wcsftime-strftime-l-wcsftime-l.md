---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 03/22/2018
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
helpviewer_keywords:
- _strftime_l function
- strftime function
- tcsftime function
- _wcsftime_l function
- wcsftime function
- _tcsftime function
- time strings
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
ms.openlocfilehash: 932a7827ef61a5e111f86f8bc44291827843b76e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353851"
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

*maxsize*<br/>
Tamaño de la *strDest* búfer, expresado en caracteres (**char** o **wchar_t**).

*format*<br/>
Cadena de control de formato.

*timeptr*<br/>
**TM** estructura de datos.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**strftime** devuelve el número de caracteres que se colocan en *strDest* y **wcsftime** devuelve el número correspondiente de caracteres anchos.

Si el número total de caracteres, incluido el carácter nulo final, es más de *maxsize*, ambos **strftime** y **wcsftime** devuelven 0 y el contenido de  *strDest* son indeterminados.

El número de caracteres en *strDest* es igual al número de caracteres literales de *formato* , así como todos los caracteres que se pueden agregar a *formato* mediante códigos de formato. El carácter nulo final de una cadena no se contabiliza en el valor devuelto.

## <a name="remarks"></a>Comentarios

El **strftime** y **wcsftime** formato funciones el **tm** hora con el valor en *timeptr* según proporcionado  *formato* argumento y almacenan el resultado en el búfer *strDest*. A lo sumo, *maxsize* caracteres se colocan en la cadena. Para obtener una descripción de los campos de la *timeptr* estructura, vea [asctime](asctime-wasctime.md). **wcsftime** es el equivalente de caracteres anchos de **strftime**; su argumento de puntero de cadena señala a una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

Esta función valida sus parámetros. Si *strDest*, *formato*, o *timeptr* es un puntero nulo, o si el **tm** estructura de datos dirigido por *timeptr* no es válido (por ejemplo, si contiene valores fuera del intervalo para la fecha u hora), o si el *formato* cadena contiene un código de formato no válido, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve 0 y establece **errno** a **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

El *formato* argumento consta de uno o más códigos; como en **printf**, los códigos de formato están precedidos por un signo de porcentaje (**%**). Caracteres que no comienzan por **%** se copian sin cambios a *strDest*. El **LC_TIME** categoría de la configuración regional actual afecta al formato de salida de **strftime**. (Para obtener más información sobre **LC_TIME**, consulte [setlocale](setlocale-wsetlocale.md).) El **strftime** y **wcsftime** funciones usan el conjunto actual configuración regional. El **_strftime_l** y **_wcsftime_l** versiones de estas funciones son idénticas salvo que toman la configuración regional como parámetro y usarlo en lugar de establecida actualmente configuración regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

El **strftime** funciones admiten estos códigos de formato:

|||
|-|-|
|Código|Cadena de reemplazo|
|**%a**|Nombre del día laborable abreviado en la configuración regional|
|**%A**|Nombre del día laborable completo en la configuración regional|
|**%b**|Nombre abreviado del mes en la configuración regional|
|**%B**|Nombre completo del mes en la configuración regional|
|**%c**|Representación de fecha y hora adecuada para la configuración regional|
|**%C**|El año dividido entre 100 y truncado en un entero, como un número decimal (00−99)|
|**%d**|Día del mes como un número decimal (01-31)|
|**%D**|Equivalente a **%m/%d/%y**|
|**%e**|Día del mes como un número decimal (1-31), donde solo dígitos están precedidos por un espacio|
|**%F**|Equivalente a **%Y %m-%d**|
|**%g**|Los 2 últimos dígitos del año ISO 8601 basado en semana como un número decimal (00 – 99)|
|**%G**|Año ISO 8601 basado en semana como un número decimal|
|**%h**|Nombre abreviado del mes (equivalente a **%b**)|
|**%H**|Hora en formato de 24 horas (00 - 23)|
|**%I**|Hora en formato de 12 horas (01-12)|
|**%j**|Día del año como número decimal (001-366)|
|**%m**|Mes como un número decimal (01-12)|
|**%M**|Minuto como número decimal (00 - 59)|
|**%n**|Un carácter de nueva línea (**\n**)|
|**%p**|A.m. y la configuración regional. Indicador de reloj de 12 horas|
|**%r**|Tiempo de reloj de 12 horas de la configuración regional|
|**%R**|Equivalente a **% H: %M**|
|**%S**|Segundo como número decimal (00 - 59)|
|**%t**|Un carácter de tabulación horizontal (**\t**)|
|**%T**|Equivalente a **% H: % M: %S**, el formato de hora ISO 8601|
|**%u**|Día de la semana ISO 8601 como un número decimal (1-7; El lunes es 1)|
|**%U**|Número de semana del año como número decimal (00 – 53), donde el primer domingo es el primer día de la semana 1|
|**%V**|Número de semana ISO 8601 como un número decimal (00 – 53)|
|**%w**|Día de la semana como un número decimal (0 - 6; El domingo es 0)|
|**%W**|Número de semana del año como número decimal (00 – 53), donde el primer lunes es el primer día de la semana 1|
|**%x**|Representación de fecha para la configuración regional|
|**%X**|Representación en tiempo de la configuración regional|
|**%y**|Año sin siglo como número decimal (00 – 99)|
|**%Y**|Año con siglo como número decimal|
|**%z**|El desplazamiento de UTC en formato ISO 8601; No hay caracteres si la zona horaria es desconocida|
|**%Z**|Del ya sea la configuración regional nombre de zona horaria o abreviatura de la zona horaria, dependiendo de la configuración del registro; No hay caracteres si la zona horaria es desconocida|
|**%%**|Signo de porcentaje|

Como en el **printf** función, el **#** marca puede aplicar un prefijo cualquier código de formato. En ese caso, el significado del código de formato cambia del siguiente modo.

|Código de formato|Significado|
|-----------------|-------------|
|**%#a**, **%#A**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X**, **%#z**, **%#Z**, **%#%**|**#** se omitirá la marca.|
|**%#c**|Long fecha y hora representación, adecuado para la configuración regional. Por ejemplo: "Martes, 14 de marzo de 1995, 12:41:29".|
|**%#x**|Representación de fecha larga, adecuada a la configuración regional. Por ejemplo: "Martes, 14 de marzo de 1995."|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **% #I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S**, **%#T** , **%#U**, **%#V**, **%#W**, **%#y**, **%#Y**|Quitar ceros o espacios (si existe).|

La semana ISO 8601 y año basado en semana producidas por **%V**, **%g**, y **%G**, usa una semana que empieza el lunes, donde 1 semana es la semana que contiene 4 de enero, que es el primero semana en los que se incluye al menos cuatro días del año. Si el primer lunes del año es el 2 º, 3 o 4 de mayo, los días anteriores forman parte de la última semana del año anterior. Durante esos días, **%V** se sustituye por 53 y ambos **%g** y **%G** se reemplazan por los dígitos del año anterior.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> o \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> o \<wchar.h>|

El **_strftime_l** y **_wcsftime_l** funciones son específicas de Microsoft. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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
