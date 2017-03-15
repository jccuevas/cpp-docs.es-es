---
title: "strftime, wcsftime, _strftime_l, _wcsftime_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strftime"
  - "_wcsftime_l"
  - "_strftime_l"
  - "wcsftime"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcsftime"
  - "strftime"
  - "wcsftime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strftime_l (función)"
  - "strftime (función)"
  - "tcsftime (función)"
  - "_wcsftime_l (función)"
  - "wcsftime (función)"
  - "_tcsftime (función)"
  - "cadenas de hora"
ms.assetid: 6330ff20-4729-4c4a-82af-932915d893ea
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# strftime, wcsftime, _strftime_l, _wcsftime_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Dar formato a una cadena de tiempo.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `strDest`  
 Cadena de salida  
  
 `maxsize`  
 Tamaño del búfer de `strDest` , medido en caracteres \(`char` o `wchart_t`\).  
  
 `format`  
 Cadena de control de formato.  
  
 `timeptr`  
 estructura de datos de`tm` .  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `strftime` devuelve el número de caracteres título en `strDest` y `wcsftime` devuelve el número correspondiente de caracteres anchos.  
  
 Si el número total de caracteres, incluido el carácter null final, es más que `maxsize`, `strftime` y `wcsftime` devuelve 0 y el contenido de `strDest` están ocultos.  
  
 El número de caracteres de `strDest` es igual al número de caracteres literales en `format` así como de cualquier carácter que se pueden agregar a `format` mediante códigos de formato.  La null final de una cadena no se cuenta en el valor devuelto.  
  
## Comentarios  
 Las funciones de `strftime` y de `wcsftime` da formato al valor de tiempo de `tm` en `timeptr` según el argumento proporcionado de `format` y almacena el resultado en el búfer *`strDest`.* A lo sumo, caracteres de `maxsize` se colocan en la cadena.  Para obtener una descripción de los campos de la estructura de `timeptr` , vea [asctime](../../c-runtime-library/reference/asctime-wasctime.md).  `wcsftime` es el equivalente de caracteres anchos de `strftime`; los puntos de argumento de cadena\- puntero a una cadena de caracteres.  Por lo demás, estas funciones se comportan exactamente igual.  
  
> [!NOTE]
>  En versiones anteriores de Visual C\+\+ 2005, la documentación descrito el parámetro de `format` de `wcsftime` como si el tipo de datos `const wchar_t *`, pero la implementación real del tipo de datos de `format` era `const char *`.  La implementación del tipode datos de `format`se ha actualizado para reflejar la documentación anterior y actual, es decir, `const wchar_t *`.  
  
 Esta función valida sus parámetros.  Si `strDest`, `format`, o`timeptr` es un puntero null, o si la estructura de datos de `tm` dirigida por `timeptr` no es válida \(por ejemplo, si contiene por valores de intervalo para la hora o la fecha\), o si la cadena de `format` contiene un código de formato no válido, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve 0 y establece `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsftime`|`strftime`|`strftime`|`wcsftime`|  
  
 El argumento de `format` consta de uno o más códigos; como en `printf`, los códigos de formato va precedido por un signo de porcentaje \(`%`\).  Los caracteres que no comienzan con `%` se copian sin cambiar a *`strDest`.* La categoría de `LC_TIME` de la configuración regional actual afecta al formato de salida de `strftime`. \(Para obtener más información sobre `LC_TIME`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).\) Las funciones sin el sufijo de `_l` utilizan la configuración regional actualmente establecido.  Las versiones de estas funciones con el sufijo de `_l` son idénticas salvo que toman la configuración regional como parámetro y utilizan que en lugar de la configuración regional actualmente establecido.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Los códigos de formato para `strftime` se muestran a continuación:  
  
 `%a`  
 Nombre del día de la semana abreviado  
  
 `%A`  
 Nombre completo del día de la semana  
  
 `%b`  
 Nombre abreviado de meses  
  
 `%B`  
 Nombre completo del mes  
  
 `%c`  
 Representación de fecha y hora adecuada para la configuración regional  
  
 `%d`  
 Día de mes como un número decimal \(01 – 31\)  
  
 `%H`  
 Hora en el formato de 24 horas \(00 – 23\)  
  
 `%I`  
 Hora en formato de hora 12 \(01 – 12\)  
  
 `%j`  
 Día del año como un número decimal \(001 – 366\)  
  
 `%m`  
 Mes como un número decimal \(01 – 12\)  
  
 `%M`  
 Minuto como un número decimal \(00 – 59\)  
  
 `%p`  
 Marcador actual a.m.\/PM. de configuración regional del reloj de 12 horas  
  
 `%S`  
 Segundo como un número decimal \(00 – 59\)  
  
 `%U`  
 Semana del año como un número decimal, con sunday como primer día de la semana \(00 – 53\)  
  
 `%w`  
 Día de la semana como un número decimal \(0 – 6; Domingo es 0\)  
  
 `%W`  
 Semana del año como un número decimal, con lunes como primer día de la semana \(00 – 53\)  
  
 `%x`  
 Presentación de la fecha para la configuración regional actual  
  
 `%X`  
 Representación de tiempo para la configuración regional actual  
  
 `%y`  
 Año sin el siglo, como un número decimal \(00 – 99\)  
  
 `%Y`  
 Año con el siglo, como un número decimal  
  
 `%z, %Z`  
 El nombre de la zona horaria o la abreviatura de la zona horaria, dependiendo de la configuración de registro; ningún carácter si la zona horaria es desconocida  
  
 `%%`  
 Signo de porcentaje  
  
 Como en la función de `printf` , el indicador de `#` puede prefijo cualquier código de formato.  En ese caso, el significado del código de formato cambia como sigue.  
  
|Código de formato|Significado|  
|-----------------------|-----------------|  
|`%#a, %#A, %#b, %#B, %#p, %#X, %#z, %#Z, %#%`|se omite el indicador de`#` .|  
|`%#c`|La presentación de la fecha larga y la hora, es adecuado para la configuración regional actual.  Por ejemplo: “Martes 14 de marzo de 1995, 12:41: 29 ".|  
|`%#x`|La representación de fecha larga, adecuadas para la configuración regional actual.  Por ejemplo: “Martes 14 de marzo de 1995”.|  
|`%#d, %#H, %#I, %#j, %#m, %#M, %#S, %#U, %#w, %#W, %#y, %#Y`|Quite los ceros iniciales \(si existe\).|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strftime`|\<time.h\>|  
|`wcsftime`|\<time.h o\> wchar.h \<\>|  
|`_strftime_l`|\<time.h\>|  
|`_wcsftime_l`|\<time.h o\> wchar.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [tiempo](../../c-runtime-library/reference/time-time32-time64.md).  
  
## Equivalente en .NET Framework  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## Vea también  
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [strxfrm, wcsxfrm, \_strxfrm\_l, \_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)