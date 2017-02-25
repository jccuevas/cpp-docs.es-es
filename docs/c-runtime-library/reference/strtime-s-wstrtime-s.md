---
title: "_strtime_s, _wstrtime_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wstrtime_s"
  - "_strtime_s"
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
  - "_wstrtime_s"
  - "strtime_s"
  - "wstrtime_s"
  - "_strtime_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtime_s (función)"
  - "_wstrtime_s (función)"
  - "copiar hora en búferes"
  - "strtime_s (función)"
  - "hora, copiar"
  - "wstrtime_s (función)"
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _strtime_s, _wstrtime_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copie la hora actual en un búfer.  Éstas son versiones de [\_strtime, \_wstrtime](../../c-runtime-library/reference/strtime-wstrtime.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _strtime_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrtime_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strtime_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrtime_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `buffer`  
 Un búfer, por lo menos 10 bytes de longitud, donde el tiempo se escribirá.  
  
 \[in\] `numberOfElements`  
 Tamaño del búfer.  
  
## Valor devuelto  
 Cero si correctamente.  
  
 Si una condición de error, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  El valor devuelto es un código de error si hay un error.  Los códigos de error se definen en ERRNO.H; vea la tabla siguiente para los errores exactos generados por esta función.  Para obtener más información sobre los códigos de error, vea [constantes de errno](../../c-runtime-library/errno-constants.md).  
  
### Condiciones de error  
  
|`buffer`|`numberOfElements`|Devolución|Contenido de `buffer`|  
|--------------|------------------------|----------------|---------------------------|  
|`NULL`|\(ninguno\)|`EINVAL`|No modificado|  
|No `NULL` \(del búfer válido\)|0|`EINVAL`|No modificado|  
|No `NULL` \(del búfer válido\)|0 \< talla 9 \<|`EINVAL`|Cadena vacía|  
|No `NULL` \(del búfer válido\)|Talla 9 \>|0|Hora actual con formato como se especifica en las notas|  
  
## Problemas de seguridad  
 Se pasa un valor NULL no válido para el búfer producirá una infracción de acceso si el parámetro de `numberOfElements` es mayor que 9.  
  
 Pasar un valor para `numberOfElements` mayor que el tamaño real del búfer dará lugar a la saturación del búfer.  
  
## Comentarios  
 Estas funciones proporcionan versiones más seguras de `_strtime` y de `_wstrtime`.  La función de `_strtime_s` copia la hora local actual en el búfer indicada por *`timestr`.* El tiempo se le da formato a `hh:mm:ss` donde dos dígitos `hh` que representan la hora en la notación de 24 horas, `mm` es dos dígitos que representan los minutos más allá de la hora, y `ss` es dos dígitos que representan segundos.  Por ejemplo, la cadena `18:23:44` representa 23 minutos y 44 segundos más allá 6 de la tarde. El búfer debe ser por lo menos 9 bytes de longitud; el tamaño real es especificado por el segundo parámetro.  
  
 `_wstrtime` es una versión con caracteres anchos de `_strtime`; el argumento y el valor devuelto de `_wstrtime` son cadenas de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignación de rutina de texto genérico:  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstrtime_s`|`_strtime_s`|`_strtime_s`|`_wstrtime_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strtime_s`|\<time.h\>|  
|`_wstrtime_s`|\<time.h o\> wchar.h \<\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// strtime_s.c  
  
#include <time.h>  
#include <stdio.h>  
  
int main()  
{  
    char tmpbuf[9];  
    errno_t err;  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    // Display operating system-style date and time.   
    err = _strtime_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
      exit(1);  
    }  
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );  
    err = _strdate_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );  
  
}  
```  
  
  **Tiempo de SO:            14:37: 49**  
**Fecha de SO:            04\/25\/03**   
## Equivalente en .NET Framework  
  
-   [System::DateTime::ToLongDateString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongdatestring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortDateString](https://msdn.microsoft.com/en-us/library/system.datetime.toshortdatestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime\_s, \_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime, \_mktime32, \_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)