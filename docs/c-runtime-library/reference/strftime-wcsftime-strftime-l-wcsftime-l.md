---
title: strftime, wcsftime, _strftime_l, _wcsftime_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 1a5331b77e218c5fe5796b2df6d0f61578657758
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="strftime-wcsftime-strftimel-wcsftimel"></a>strftime, wcsftime, _strftime_l, _wcsftime_l
Da formato a una cadena de hora.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
  
#### <a name="parameters"></a>Parámetros  
 `strDest`  
 Cadena de salida  
  
 `maxsize`  
 Tamaño del búfer `strDest`, expresado en caracteres (`char` o `wchart_t`).  
  
 `format`  
 Cadena de control de formato.  
  
 `timeptr`  
Estructura de datos  `tm`.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 `strftime` devuelve el número de caracteres que se colocan en `strDest` y `wcsftime` devuelve el número correspondiente de caracteres anchos.  
  
 Si el número total de caracteres, incluido el carácter nulo final, es superior a `maxsize`, `strftime` y `wcsftime` devuelven 0 y el contenido de `strDest` es indeterminado.  
  
 El número de caracteres de `strDest` es igual al número de caracteres literales de `format`, así como todos los caracteres que puedan agregarse a `format` mediante códigos de formato. El carácter nulo final de una cadena no se contabiliza en el valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 El `strftime` y `wcsftime` formato funciones el `tm` hora con el valor en `timeptr` según proporcionado `format` argumento y el resultado en el búfer de la tienda `strDest`. Como máximo se colocan `maxsize` caracteres en la cadena. Para obtener una descripción de los campos de la estructura `timeptr`, vea [asctime](../../c-runtime-library/reference/asctime-wasctime.md). `wcsftime` es el equivalente en caracteres anchos de `strftime`; su argumento de puntero de cadena señala a una cadena con caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.  
  
> [!NOTE]
>  En las versiones anteriores de Visual C++ 2005, en la documentación se describía que el parámetro `format` de `wcsftime` tenía el tipo de datos `const wchar_t *`, aunque la implementación real del tipo de datos `format` era `const char *`. La implementación de la `format` tipo de datos se ha actualizado para reflejar la documentación anterior y actual, es decir, `const wchar_t *`.  
  
 Esta función valida sus parámetros. Si `strDest`, `format`, o `timeptr` es un puntero nulo, o si la `tm` estructura de datos mencionado en `timeptr` no es válida (por ejemplo, si contiene valores fuera del intervalo para la fecha u hora), o si la `format` cadena contiene un código de formato no válido, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve 0 y establece `errno` en `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|  
  
 El argumento `format` consta de uno o más códigos; como en `printf`, los códigos de formato están precedidos por un signo de porcentaje (`%`). Caracteres que no comienzan por `%` se copiarán sin ninguna modificación a `strDest`. La categoría `LC_TIME` de la configuración regional actual afecta al formato de salida de `strftime` (para obtener más información sobre `LC_TIME`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)). Las funciones que no tienen el sufijo `_l` usan la configuración regional establecida en ese momento. Las versiones de estas funciones que tienen el sufijo `_l` son idénticas, salvo que toman la configuración regional como un parámetro y lo usan en vez de la configuración regional establecida en ese momento. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 A continuación se detallan los códigos de formato de `strftime`:  
  
 `%a`  
 Nombre abreviado del día de la semana  
  
 `%A`  
 Nombre completo del día de la semana  
  
 `%b`  
 Nombre abreviado del mes  
  
 `%B`  
 Nombre completo del mes  
  
 `%c`  
 Representación de fecha y hora adecuada para la configuración regional  
  
 `%d`  
 Día del mes como número decimal (01-31)  
  
 `%H`  
 Hora en formato de 24 horas (00 – 23)  
  
 `%I`  
 Hora en formato de 12 horas (01-12)  
  
 `%j`  
 Día del año como número decimal (001-366)  
  
 `%m`  
 Mes como número decimal (01-12)  
  
 `%M`  
 Minuto como número decimal (00 - 59)  
  
 `%p`  
 Hora a. m./p. m. actual de la configuración regional Indicador de reloj de 12 horas  
  
 `%S`  
 Segundo como número decimal (00 - 59)  
  
 `%U`  
 Semana del año como número decimal, siendo el domingo como primer día de la semana (00 - 53)  
  
 `%w`  
 Día de la semana como número decimal (0 - 6; El domingo es 0)  
  
 `%W`  
 Semana del año como número decimal, con el lunes como primer día de la semana (00 - 53)  
  
 `%x`  
 Representación de la fecha para la configuración regional actual  
  
 `%X`  
 Representación de la hora para la configuración regional actual  
  
 `%y`  
 Año sin el siglo, como número decimal (00 – 99)  
  
 `%Y`  
 Año con siglo como número decimal  
  
 `%z, %Z`  
 El nombre o la abreviatura de la zona horaria, dependiendo de la configuración del registro; sin caracteres si la zona horaria es desconocida  
  
 `%%`  
 Signo de porcentaje  
  
 Como en la función `printf`, la marca `#` puede aplicar un prefijo a cualquier código de formato. En ese caso, el significado del código de formato cambia del siguiente modo.  
  
|Código de formato|Significado|  
|-----------------|-------------|  
|`%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#%`|La marca `#` se omite.|  
|`%#c`|Representación de fecha y hora larga, adecuada para la configuración regional actual. Por ejemplo: "Martes, 14 de marzo de 1995, 12:41:29".|  
|`%#x`|Representación de fecha larga, adecuada para la configuración regional actual. Por ejemplo: "Martes, 14 de marzo de 1995".|  
|`%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y`|Se quitan los ceros a la izquierda (en caso de haberlos).|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`strftime`|\<time.h>|  
|`wcsftime`|\<time.h> o \<wchar.h>|  
|`_strftime_l`|\<time.h>|  
|`_wcsftime_l`|\<time.h> o \<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [time](../../c-runtime-library/reference/time-time32-time64.md).  
  
## <a name="see-also"></a>Vea también  
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll (Funciones)](../../c-runtime-library/strcoll-functions.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)
