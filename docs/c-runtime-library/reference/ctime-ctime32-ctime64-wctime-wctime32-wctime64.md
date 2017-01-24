---
title: "ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ctime64"
  - "_wctime32"
  - "ctime"
  - "_wctime64"
  - "_ctime32"
  - "_wctime"
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
  - "_wctime64"
  - "_ctime32"
  - "_tctime"
  - "_wctime"
  - "_wctime32"
  - "_tctime64"
  - "_ctime64"
  - "ctime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tctime64 (función)"
  - "_ctime32 (función)"
  - "ctime32 (función)"
  - "_wctime (función)"
  - "wctime64 (función)"
  - "_tctime64 (función)"
  - "_tctime32 (función)"
  - "_ctime64 (función)"
  - "_wctime64 (función)"
  - "ctime (función)"
  - "wctime32 (función)"
  - "ctime64 (función)"
  - "_wctime32 (función)"
  - "_tctime (función)"
  - "tctime32 (función)"
  - "tctime (función)"
  - "wctime (función)"
  - "hora, convertir"
ms.assetid: 2423de37-a35c-4f0a-a378-3116bc120a9d
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convertir un valor de hora en una cadena y ajustar la configuración de la zona horaria local. Existen versiones más seguras de estas funciones; consulte [ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md).  
  
## Sintaxis  
  
```  
char *ctime(   
   const time_t *timer   
);  
char *_ctime32(   
   const __time32_t *timer )  
;  
char *_ctime64(   
   const __time64_t *timer )  
;  
wchar_t *_wctime(   
   const time_t *timer   
);  
wchar_t *_wctime32(   
   const __time32_t *timer  
);  
wchar_t *_wctime64(   
   const __time64_t *timer   
);  
```  
  
#### Parámetros  
 `timer`  
 Puntero a la hora almacenada.  
  
## Valor devuelto  
 Un puntero al resultado de la cadena de caracteres.`NULL` se devolverá si:  
  
-   `time` Representa una fecha anterior a la medianoche del 1 de enero de 1970 UTC.  
  
-   Si utiliza `_ctime32` o `_wctime32` y `time` representa una fecha posterior a las 23:59:59 del 18 de enero de 2038, hora UTC.  
  
-   Si utiliza `_ctime64` o `_wctime64` y `time` representa una fecha posterior a las 23:59:59 del 31 de diciembre de 3000, UTC.  
  
 `ctime` es una función insertada que se evalúa como `_ctime64` y `time_t` es equivalente a `__time64_t`. Si necesita que el compilador interprete `time_t` como el antiguo 32 bits `time_t`, puede definir `_USE_32BIT_TIME_T`. Hacer esto hará que `ctime` se evalúe como `_ctime32`. Esto no se recomienda porque puede producir un error de la aplicación después del 18 de enero de 2038, y no se permite en plataformas de 64 bits.  
  
## Comentarios  
 El `ctime` función convierte un valor de hora almacenado como un [time\_t](../../c-runtime-library/standard-types.md) valor en una cadena de caracteres. El `timer` valor suele obtenerse a partir de una llamada a [tiempo](../../c-runtime-library/reference/time-time32-time64.md), que devuelve el número de segundos transcurrido desde la medianoche \(00: 00:00\) del 1 de enero de 1970, hora universal coordinada \(UTC\). La cadena del valor devuelto contiene exactamente 26 caracteres y tiene el formato:  
  
```  
Wed Jan 02 02:03:55 1980\n\0  
```  
  
 Se utiliza un reloj de 24 horas. Todos los campos tienen un ancho constante. El carácter de nueva línea \('\\n'\) y el carácter nulo \('\\0'\) ocupan las dos últimas posiciones de la cadena.  
  
 La cadena de caracteres convertidos también se ajusta según la configuración de zona horaria local. Consulte la `time`, [\_ftime](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), y [localtime](../../c-runtime-library/reference/localtime-localtime32-localtime64.md) funciones para obtener información sobre la configuración de la hora local y la [\_tzset](../../c-runtime-library/reference/tzset.md) \(función\) para obtener más información acerca de cómo definir el entorno de zona horaria y variables globales.  
  
 Una llamada a `ctime` modifica el búfer asignado estáticamente único utilizado por el `gmtime` y `localtime` funciones. Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.`ctime` comparte un búfer estático con el `asctime` \(función\). Por lo tanto, una llamada a `ctime` destruye los resultados de las llamadas anteriores a `asctime`, `localtime`, o `gmtime`.  
  
 `_wctime` y `_wctime64` son la versión de caracteres anchos de `ctime` y `_ctime64`; devuelve un puntero a la cadena de caracteres anchos. De lo contrario, `_ctime64`, `_wctime`, y `_wctime64` se comportan exactamente igual a `ctime`.  
  
 Estas funciones validan sus parámetros. Si `timer` es un puntero nulo, o si el valor del temporizador es negativo, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, las funciones devuelven `NULL` y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tctime`|`ctime`|`ctime`|`_wctime`|  
|`_tctime32`|`_ctime32`|`_ctime32`|`_wctime32`|  
|`_tctime64`|`_ctime64`|`_ctime64`|`_wctime64`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`ctime`|\<time.h\>|  
|`_ctime32`|\<time.h\>|  
|`_ctime64`|\<time.h\>|  
|`_wctime`|\< time.h \> o \< wchar.h \>|  
|`_wctime32`|\< time.h \> o \< wchar.h \>|  
|`_wctime64`|\< time.h \> o \< wchar.h \>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_ctime64.c  
// compile with: /W3  
/* This program gets the current  
 * time in _time64_t form, then uses ctime to  
 * display the time in string form.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   __time64_t ltime;  
  
   _time64( &ltime );  
   printf( "The time is %s\n", _ctime64( &ltime ) ); // C4996  
   // Note: _ctime64 is deprecated; consider using _ctime64_s  
}  
```  
  
```Output  
La hora es de 13 de febrero del miércoles 16:04:43 2002  
```  
  
## Equivalente en .NET Framework  
  
-   [System::DateTime::GetDateTimeFormats](https://msdn.microsoft.com/en-us/library/system.datetime.getdatetimeformats.aspx)  
  
-   [System::DateTime::ToString](https://msdn.microsoft.com/en-us/library/system.datetime.tostring.aspx)  
  
-   [System::DateTime::ToLongTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.tolongtimestring.aspx)  
  
-   [System::DateTime::ToShortTimeString](https://msdn.microsoft.com/en-us/library/system.datetime.toshorttimestring.aspx)  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)