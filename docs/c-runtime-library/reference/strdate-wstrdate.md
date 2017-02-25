---
title: "_strdate, _wstrdate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdate"
  - "_wstrdate"
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
  - "_tstrdate"
  - "wstrdate"
  - "_wstrdate"
  - "_strdate"
  - "strdate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "strdate (función)"
  - "fechas, copiar"
  - "tstrdate (función)"
  - "_wstrdate (función)"
  - "wstrdate (función)"
  - "_strdate (función)"
  - "_tstrdate (función)"
  - "copiar fechas"
ms.assetid: de8e4097-58f8-42ba-9dcd-cb4d9a9f1696
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _strdate, _wstrdate
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Fecha actual del sistema de la copia en un búfer.  Hay disponibles versiones más seguras de estas funciones; vea [\_strdate\_s, \_wstrdate\_s](../../c-runtime-library/reference/strdate-s-wstrdate-s.md).  
  
## Sintaxis  
  
```  
char *_strdate(  
   char *datestr   
);  
wchar_t *_wstrdate(  
   wchar_t *datestr   
);  
template <size_t size>  
char *_strdate(  
   char (&datestr)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wstrdate(  
   wchar_t (&datestr)[size]  
); // C++ only  
```  
  
#### Parámetros  
 `datestr`  
 Un puntero a un búfer que contiene la cadena de fecha con formato.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a la cadena de caracteres resultante `datestr`.  
  
## Comentarios  
 Versiones más seguras de estas funciones están disponibles; vea [\_strdate\_s, \_wstrdate\_s](../../c-runtime-library/reference/strdate-s-wstrdate-s.md).  Se recomienda que las funciones más seguras se utilicen siempre que sea posible.  
  
 La función de `_strdate` copia la fecha actual del sistema en el búfer indicada por `datestr`, `mm`con formato\/`dd`\/`yy`, donde dos dígitos `mm` que representan el mes, `dd` es dos dígitos que representan el día, y `yy` es los dos últimos dígitos del año.  Por ejemplo, la cadena `12/05/99` representa el 5 de diciembre de 1999.  El búfer debe ser por lo menos 9 bytes de longitud.  
  
 Si `datestr` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 `_wstrdate` es una versión con caracteres anchos de `_strdate`; el argumento y el valor devuelto de `_wstrdate` son cadenas de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstrdate`|`_strdate`|`_strdate`|`_wstrdate`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strdate`|\<time.h\>|  
|`_wstrdate`|\<time.h o\> wchar.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// strdate.c  
// compile with: /W3  
#include <time.h>  
#include <stdio.h>  
int main()  
{  
    char tmpbuf[9];  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    printf( "OS date: %s\n", _strdate(tmpbuf) ); // C4996  
    // Note: _strdate is deprecated; consider using _strdate_s instead  
}  
```  
  
  **Fecha de SO: 04\/25\/03**   
## Equivalente en .NET Framework  
 [System::DateTime::Parse](https://msdn.microsoft.com/en-us/library/system.datetime.parse.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [mktime, \_mktime32, \_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)