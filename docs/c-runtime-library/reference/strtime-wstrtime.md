---
title: "_strtime, _wstrtime | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wstrtime"
  - "_strtime"
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
  - "_wstrtime"
  - "_strtime"
  - "wstrtime"
  - "strtime"
  - "_tstrtime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtime (función)"
  - "_tstrtime (función)"
  - "_wstrtime (función)"
  - "copiar hora en búferes"
  - "strtime (función)"
  - "hora, copiar"
  - "tstrtime (función)"
  - "wstrtime (función)"
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# _strtime, _wstrtime
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copie el tiempo en un búfer.  Hay disponibles versiones más seguras de estas funciones; vea [\_strtime\_s, \_wstrtime\_s](../../c-runtime-library/reference/strtime-s-wstrtime-s.md).  
  
## Sintaxis  
  
```  
char *_strtime(  
   char *timestr   
);  
wchar_t *_wstrtime(  
   wchar_t *timestr   
);  
template <size_t size>  
char *_strtime(  
   char (&timestr)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wstrtime(  
   wchar_t (&timestr)[size]  
); // C++ only  
```  
  
#### Parámetros  
 `timestr`  
 Cadena de tiempo.  
  
## Valor devuelto  
 Devuelve un puntero a la cadena de caracteres resultante `timestr`.  
  
## Comentarios  
 La función de `_strtime` copia la hora local actual en el búfer indicada por *`timestr`.* El tiempo se le da formato a `hh:mm:ss` donde dos dígitos `hh` que representan la hora en la notación de 24 horas, `mm` es dos dígitos que representan los minutos más allá de la hora, y `ss` es dos dígitos que representan segundos.  Por ejemplo, la cadena `18:23:44` representa 23 minutos y 44 segundos más allá 6 de la tarde. El búfer debe ser por lo menos 9 bytes de longitud.  
  
 `_wstrtime` es una versión con caracteres anchos de `_strtime`; el argumento y el valor devuelto de `_wstrtime` son cadenas de caracteres anchos.  Estas funciones se comportan exactamente igual de otra manera. Si `timestr` es un puntero de `NULL` o si `timestr` se da formato incorrectamente, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la excepción puede continuar, estas funciones devuelven un valor NULL y `errno` determinado a `EINVAL` si `timestr` era NULL o `errno` determinado a `ERANGE` si `timestr` se da formato incorrecto.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstrtime`|`_strtime`|`_strtime`|`_wstrtime`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strtime`|\<time.h\>|  
|`_wstrtime`|\<time.h o\> wchar.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_strtime.c  
// compile with: /W3  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char tbuffer [9];  
   _strtime( tbuffer ); // C4996  
   // Note: _strtime is deprecated; consider using _strtime_s instead  
   printf( "The current time is %s \n", tbuffer );  
}  
```  
  
  **La hora actual es 14:21: 44**   
## Equivalente en .NET Framework  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [mktime, \_mktime32, \_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)