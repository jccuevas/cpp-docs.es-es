---
title: strftime, wcsftime, _strftime_l, _wcsftime_l
ms.date: 4/2/2020
api_name:
- strftime
- _wcsftime_l
- _strftime_l
- wcsftime
- _o__strftime_l
- _o__wcsftime_l
- _o_strftime
- _o_wcsftime
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 5da2c128c54fd88bb874b360f5a966f17b14a935
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350017"
---
# <a name="strftime-wcsftime-_strftime_l-_wcsftime_l"></a>strftime, wcsftime, _strftime_l, _wcsftime_l

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

*Maxsize*<br/>
Tamaño del búfer *strDest,* medido en caracteres (**char** o **wchar_t**).

*Formato*<br/>
Cadena de control de formato.

*timeptr*<br/>
estructura de datos **tm.**

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**strftime** devuelve el número de caracteres colocados en *strDest* y **wcsftime** devuelve el número correspondiente de caracteres anchos.

Si el número total de caracteres, incluido el null de terminación, es mayor que *maxsize*, tanto **strftime** como **wcsftime** devuelven 0 y el contenido de *strDest* es indeterminado.

El número de caracteres en *strDest* es igual al número de caracteres literales en *formato,* así como a los caracteres que se pueden agregar al *formato* a través de códigos de formato. El carácter nulo final de una cadena no se contabiliza en el valor devuelto.

## <a name="remarks"></a>Observaciones

Las funciones **strftime** y **wcsftime** dan formato al valor de tiempo **tm** en *timeptr* según el argumento de *formato* proporcionado y almacenan el resultado en el *búfer strDest*. A lo sumo, los caracteres *maxsize* se colocan en la cadena. Para obtener una descripción de los campos de la estructura *timeptr,* vea [asctime](asctime-wasctime.md). **wcsftime** es el equivalente de caracteres anchos de **strftime**; su argumento de puntero de cadena apunta a una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

Esta función valida sus parámetros. Si *strDest*, *format*, o *timeptr* es un puntero nulo, o si la estructura de datos **tm** dirigida por *timeptr* no es válida (por ejemplo, si contiene valores fuera del intervalo para la hora o la fecha), o si la cadena de *formato* contiene un código de formato no válido, se invoca el controlador de parámetros no válidos, como se describe en Validación de [parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve 0 y establece **errno en** **EINVAL**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsftime**|**strftime**|**strftime**|**wcsftime**|

El argumento *format* consta de uno o varios códigos; como en **printf**, los códigos de**%** formato van precedidos de un signo de porcentaje ( ). Los caracteres que **%** no comienzan con se copian sin cambios en *strDest*. La categoría **LC_TIME** de la configuración regional actual afecta al formato de salida de **strftime**. (Para obtener más información sobre **LC_TIME**, consulte [setlocale](setlocale-wsetlocale.md).) Las funciones **strftime** y **wcsftime** utilizan la configuración regional establecida actualmente. Las **versiones _strftime_l** y **_wcsftime_l** de estas funciones son idénticas, excepto que toman la configuración regional como parámetro y lo usan en lugar de la configuración regional establecida actualmente. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Las funciones **strftime** admiten estos códigos de formato:

|||
|-|-|
|Código|Cadena de reemplazo|
|**%a**|Abreviado nombre entre semana en la configuración regional|
|**%A**|Nombre completo del día de la semana en la configuración regional|
|**%b**|Nombre del mes abreviado en la configuración regional|
|**%B**|Nombre del mes completo en la configuración regional|
|**%c**|Representación de fecha y hora adecuada para la configuración regional|
|**%C**|El año dividido por 100 y truncado a un entero, como un número decimal (00-99)|
|**%d**|Día del mes como número decimal (01 - 31)|
|**%D**|Equivalente a **%m/%d/%y**|
|**%e**|Día del mes como un número decimal (1 - 31), donde los dígitos individuales están precedidos por un espacio|
|**%F**|Equivalente a **%Y-%m-%d**|
|**%g**|Los últimos 2 dígitos del año basado en la semana ISO 8601 como número decimal (00 - 99)|
|**%G**|El año basado en la semana ISO 8601 como número decimal|
|**%h**|Nombre del mes abreviado (equivalente a **%b**)|
|**%H**|Hora en formato de 24 horas (00 - 23)|
|**%I**|Hora en formato de 12 horas (01 - 12)|
|**%j**|Día del año como número decimal (001 - 366)|
|**%m**|Mes como número decimal (01 - 12)|
|**%M**|Minuto como número decimal (00 - 59)|
|**%n**|Un carácter de nueva línea (**n**)|
|**%p**|La localidad es A.M./P.M. Indicador de reloj de 12 horas|
|**%r**|Horario de 12 horas del lugar|
|**%R**|Equivalente a **%H:%M**|
|**%S**|Segundo como número decimal (00 - 59)|
|**%t**|Un carácter de tabulación horizontal (**.t**)|
|**%T**|Equivalente a **%H:%M:%S**, el formato de hora ISO 8601|
|**%u**|ISO 8601 día de la semana como un número decimal (1 - 7; Lunes es 1)|
|**%U**|Número de semana del año como número decimal (00 - 53), donde el primer domingo es el primer día de la semana 1|
|**%V**|Número de semana ISO 8601 como número decimal (00 - 53)|
|**%w**|Día de la semana como número decimal (0 - 6; Domingo es 0)|
|**%W**|Número de semana del año como número decimal (00 - 53), donde el primer lunes es el primer día de la semana 1|
|**%x**|Representación de fecha para la configuración regional|
|**%X**|Representación de la hora para la configuración regional|
|**%y**|Año sin siglo, como número decimal (00 - 99)|
|**%Y**|Año con siglo como número decimal|
|**%z**|El desplazamiento de UTC en formato ISO 8601; no hay caracteres si se desconoce la zona horaria|
|**%Z**|El nombre de zona horaria de la configuración regional o la abreviatura de zona horaria, dependiendo de la configuración del Registro; no hay caracteres si se desconoce la zona horaria|
|**%%**|Signo de porcentaje|

Al igual que en **#** la función **printf,** el indicador puede prefijar cualquier código de formato. En ese caso, el significado del código de formato cambia del siguiente modo.

|Código de formato|Significado|
|-----------------|-------------|
|**%#a**, **%#A #a**, **%#b**, **%#B**, **%#g**, **%#G**, **%#h**, **%#n**, **%#p**, **%#t**, **%#u**, **%#w**, **%#X**, **%#z**, **%#Z**,**%#%**|**#** bandera se ignora.|
|**%#c**|Larga representación de fecha y hora, apropiada para la configuración regional. Por ejemplo: "Martes, 14 de marzo de 1995, 12:41:29".|
|**%#x**|Representación de fecha larga, apropiada para la configuración regional. Por ejemplo: "Martes, 14 de marzo de 1995".|
|**%#d**, **%#D**, **%#e**, **%#F**, **%#H**, **%#I**, **%#j**, **%#m**, **%#M**, **%#r**, **%#R**, **%#S** **, %#T**, **%#U**, **%#V #W**, **%#W**, **%#y**, **%#Y**|Elimine los ceros o espacios a la izquierda (si los hay).|

La semana ISO 8601 y el año de la semana producido por **%V**, **%g**, y **%G**, utiliza una semana que comienza el lunes, donde la semana 1 es la semana que contiene el 4 de enero, que es la primera semana que incluye al menos cuatro días del año. Si el primer lunes del año es el 2o, 3o o 4o, los días anteriores forman parte de la última semana del año anterior. Para esos días, **%V** se sustituye por 53, y **tanto %g** como **%G** se sustituyen por los dígitos del año anterior.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strftime**|\<time.h>|
|**wcsftime**|\<time.h> o \<wchar.h>|
|**_strftime_l**|\<time.h>|
|**_wcsftime_l**|\<time.h> o \<wchar.h>|

Las funciones **_strftime_l** y **_wcsftime_l** son específicas de Microsoft. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [time](time-time32-time64.md).

## <a name="see-also"></a>Consulte también

[Configuración regional](../../c-runtime-library/locale.md) <br/>
[Administración de hora](../../c-runtime-library/time-management.md) <br/>
[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md) <br/>
[localeconv](localeconv.md) <br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md) <br/>
[Funciones strcoll](../../c-runtime-library/strcoll-functions.md) <br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
