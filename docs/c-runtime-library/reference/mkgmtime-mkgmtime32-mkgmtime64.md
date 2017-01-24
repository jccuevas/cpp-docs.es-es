---
title: "_mkgmtime, _mkgmtime32, _mkgmtime64 | Microsoft Docs"
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
  - "_mkgmtime32"
  - "_mkgmtime64"
  - "_mkgmtime"
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
  - "_mkgmtime64"
  - "mkgmtime32"
  - "_mkgmtime32"
  - "mkgmtime"
  - "mkgmtime64"
  - "_mkgmtime"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "mkgmtime32 (función)"
  - "funciones de tiempo"
  - "mkgmtime (función)"
  - "_mkgmtime (función)"
  - "convertir horas"
  - "mkgmtime64 (función)"
  - "_mkgmtime64 (función)"
  - "_mkgmtime32 (función)"
  - "hora, convertir"
ms.assetid: b4ca2b67-e198-4f43-b3e2-e8ad6bd01867
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mkgmtime, _mkgmtime32, _mkgmtime64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una hora UTC representada por un `tm``struct` a una hora UTC representada por un `time_t` tipo.  
  
## Sintaxis  
  
```  
  
time_t _mkgmtime(  
   struct tm*   
timeptr  
);  
__time32_t _mkgmtime32(  
   struct tm*   
timeptr  
);  
__time64_t _mkgmtime64(  
   struct tm*   
timeptr  
);  
  
```  
  
#### Parámetros  
 `timeptr`  
 Un puntero a la hora UTC como un `struct``tm` para convertir.  
  
## Valor devuelto  
 Una cantidad de tipo `__time32_t` o `__time64_t` que representa el número de segundos transcurridos desde la medianoche del 1 de enero de 1970, hora Universal coordinada \(UTC\). Si la fecha está fuera del intervalo \(vea la sección Comentarios\) o la entrada no se puede interpretar como una hora válida, el valor devuelto será – 1.  
  
## Comentarios  
 El `_mkgmtime32` y `_mkgmtime64` funciones de convierten una hora UTC en un `__time32_t` o `__time64_t` tipo que representa la hora en UTC. Para convertir una hora local en hora UTC, use `mktime`, `_mktime32`, y `_mktime64` en su lugar.  
  
 `_mkgmtime` es una función insertada que se evalúa como `_mkgmtime64`, y `time_t` es equivalente a `__time64_t`. Si necesita que el compilador interprete `time_t`como lo 32 bits anterior `time_t`, puede definir `_USE_32BIT_TIME_T`. No se recomienda porque la aplicación puede fallar después del 18 de enero de 2038 \(el intervalo máximo de 32 bits `time_t`\), y no se permite en absoluto en plataformas de 64 bits.  
  
 El tiempo transcurrida de estructura en cambiará como sigue, de la misma manera como se cambian con el `_mktime` funciones: el `tm_wday` y `tm_yday` campos se establecen en los nuevos valores basados en los valores de `tm_mday` y `tm_year`. Al especificar una estructura de hora de `tm`, establezca el campo `tm_isdst` en:  
  
-   Cero \(0\) para indicar que está vigente la hora estándar.  
  
-   Un valor mayor que 0 para indicar que está vigente el horario de verano.  
  
-   Un valor menor que cero para que el código de la biblioteca en tiempo de ejecución de C calcule si está vigente la hora estándar o el horario de verano.  
  
 La biblioteca de tiempo de ejecución de C, usa la variable de entorno TZ para determinar el horario de verano correcto. Si TZ no se establece, el sistema operativo se consulta para obtener el horario de verano regional correcta el comportamiento de tiempo.`tm_isdst` es un campo obligatorio. Si no se establece, su valor es indefinido y el valor devuelto de `mktime` es imprevisible.  
  
 El intervalo de la `_mkgmtime32` función es desde la medianoche del 1 de enero de 1970, hora UTC a 23:59:59 del 18 de enero de 2038, hora UTC. El intervalo de `_mkgmtime64` es desde la medianoche del 1 de enero de 1970 UTC a 23:59:59 del 31 de diciembre de 3000, UTC. Una fecha fuera de intervalo da como resultado un valor devuelto de – 1. El intervalo de `_mkgmtime` depende de si `_USE_32BIT_TIME_T` se define. Si no define \(predeterminado\) el intervalo es de `_mkgmtime64`; de lo contrario, el intervalo se limita a la gama de 32 bits de `_mkgmtime32`.  
  
 Tenga en cuenta que `gmtime` y `localtime` utilizan un único búfer asignado estáticamente para la conversión. Si se proporciona este búfer a `mkgmtime`, se destruye el contenido anterior.  
  
## Ejemplo  
  
```  
// crt_mkgmtime.c  
#include <stdio.h>  
#include <time.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t now, mytime, gmtime;  
    char buff[30];  
  
    time( & now );  
  
    _localtime64_s( &t1, &now );  
    _gmtime64_s( &t2, &now );  
  
    mytime = mktime(&t1);  
    gmtime = _mkgmtime(&t2);  
  
    printf("Seconds since midnight, January 1, 1970\n");  
    printf("My time: %I64d\nGM time (UTC): %I64d\n\n", mytime, gmtime);  
  
    /* Use asctime_s to display these times. */  
  
    _localtime64_s( &t1, &mytime );  
    asctime_s( buff, sizeof(buff), &t1 );  
    printf( "Local Time: %s\n", buff );  
  
    _gmtime64_s( &t2, &gmtime );  
    asctime_s( buff, sizeof(buff), &t2 );  
    printf( "Greenwich Mean Time: %s\n", buff );  
  
}  
```  
  
## Resultados del ejemplo  
  
```  
Seconds since midnight, January 1, 1970  
My time: 1171588492  
GM time (UTC): 1171588492  
  
Local Time: Thu Feb 15 17:14:52 2007  
  
Greenwich Mean Time: Fri Feb 16 01:14:52 2007  
```  
  
 En el ejemplo siguiente se muestra cómo se rellena la estructura incompleto con los valores calculados del día de la semana y el día del año.  
  
```  
// crt_mkgmtime2.c  
#include <stdio.h>  
#include <time.h>  
#include <memory.h>  
  
int main()  
{  
    struct tm t1, t2;  
    time_t gmtime;  
    char buff[30];  
  
    memset(&t1, 0, sizeof(struct tm));  
    memset(&t2, 0, sizeof(struct tm));  
  
    t1.tm_mon = 1;  
    t1.tm_isdst = 0;  
    t1.tm_year = 103;  
    t1.tm_mday = 12;  
  
    // The day of the week and year will be incorrect in the output here.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("Before calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
    gmtime = _mkgmtime(&t1);  
  
    // The correct day of the week and year were determined.  
    asctime_s( buff, sizeof(buff), &t1);  
    printf("After calling _mkgmtime, t1 = %s t.tm_yday = %d\n",  
            buff, t1.tm_yday );  
  
}  
```  
  
## Salida  
  
```  
Before calling _mkgmtime, t1 = Sun Feb 12 00:00:00 2003  
 t.tm_yday = 0  
After calling _mkgmtime, t1 = Wed Feb 12 00:00:00 2003  
 t.tm_yday = 42  
```  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [asctime\_s, \_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime, \_mktime32, \_mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)