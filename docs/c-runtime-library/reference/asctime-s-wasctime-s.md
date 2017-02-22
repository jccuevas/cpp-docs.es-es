---
title: "asctime_s, _wasctime_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wasctime_s"
  - "asctime_s"
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
  - "asctime_s"
  - "_wasctime_s"
  - "_tasctime_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tasctime_s (función)"
  - "_wasctime_s (función)"
  - "asctime_s (función)"
  - "tasctime_s (función)"
  - "conversión de estructura de tiempo"
  - "hora, convertir"
  - "wasctime_s (función)"
ms.assetid: 17ad9b2b-a459-465d-976a-42822897688a
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# asctime_s, _wasctime_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una estructura en tiempo de `tm` a una cadena de caracteres.  Estas funciones son versiones de [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t asctime_s(   
   char* buffer,  
   size_t numberOfElements,  
   const struct tm *_tm   
);  
errno_t _wasctime_s(   
   wchar_t* buffer,  
   size_t numberOfElements  
   const struct tm *_tm   
);  
template <size_t size>  
errno_t asctime_s(   
   char (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
template <size_t size>  
errno_t _wasctime_s(   
   wchar_t (&buffer)[size],  
   const struct tm *_tm   
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 \[out\] Un puntero a un búfer para almacenar el resultado de la cadena de caracteres.  Esta función utiliza un puntero a una ubicación de memoria válida con un tamaño especificado por `numberOfElements`.  
  
 `numberOfElements`  
 \[in\] El tamaño del búfer usado para almacenar el resultado.  
  
 `_tm`  
 \[in\] Estructura de hora o de fecha.  Esta función utiliza un puntero a un objeto válido de `struct``tm` .  
  
## Valor devuelto  
 Cero si correctamente.  Si hay un error, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, el valor devuelto es un código de error.  Los códigos de error se definen en ERRNO.H.  Para obtener más información, vea [errno \(Constantes\)](../../c-runtime-library/errno-constants.md).  Los códigos de error reales devueltos para cada condición de error se muestran en la tabla siguiente.  
  
### Condiciones de error  
  
|`buffer`|`numberOfElements`|`tm`|Devolución|Valor de `buffer`|  
|--------------|------------------------|----------|----------------|-----------------------|  
|`NULL`|Cualquiera|Cualquiera|`EINVAL`|No modificado|  
|No`NULL` \(señala memoria válido\)|0|Cualquiera|`EINVAL`|No modificado|  
|No `NULL`|0\< talla 26 \<|Cualquiera|`EINVAL`|Cadena vacía|  
|No `NULL`|\>\= 26|`NULL`|`EINVAL`|Cadena vacía|  
|No `NULL`|\>\= 26|Estructura no válida del tiempo o por valores de intervalo para los componentes de tiempo|`EINVAL`|Cadena vacía|  
  
> [!NOTE]
>  Las condiciones de error para `wasctime_s` son similares a `asctime_s` excepto que el límite de tamaño se mide en palabras.  
  
## Comentarios  
 La función de `asctime` convierte una hora almacenada como una estructura a una cadena de caracteres.  El valor de `_tm` se obtiene normalmente de una llamada a `gmtime` o a `localtime`.  Ambas funciones se pueden utilizar para completar una estructura de `tm` , según TIME.H.  
  
|miembro del timeptr|Valor|  
|-------------------------|-----------|  
|`tm_hour`|Horas desde la medianoche \(0\-23\)|  
|`tm_isdst`|Positivo si el horario de verano está vigente; 0 si el horario de verano no está vigente; negativa si el estado de horario de verano es desconocido.  La biblioteca en tiempo de ejecución de C supone las reglas de los Estados Unidos para implementar el cálculo en tiempo \(DST\) de Guardar Daylight.|  
|`tm_mday`|Día del mes \(1\-31\)|  
|`tm_min`|Minutos después de la hora \(0\-59\)|  
|`tm_mon`|Mes \(0\-11; Enero \= 0\)|  
|`tm_sec`|Segundos después de minuto \(0\-59\)|  
|`tm_wday`|Día de la semana \(0\-6; Domingo \= 0\)|  
|`tm_yday`|Día del año \(0\-365; 1 de enero \= 0\)|  
|`tm_year`|Año \(año actual menos 1900\)|  
  
 Cadena de caracteres convierte también se ajusta según la configuración de zonas de la hora local.  Vea [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md), [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md), y las funciones de [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md) para obtener información sobre la configuración de la hora local y la función de [\_tzset](../../c-runtime-library/reference/tzset.md) para obtener información sobre la definición del entorno y las variables globales de la zona horaria.  
  
 El resultado de la cadena generado por `asctime_s` contiene exactamente 26 caracteres y tiene el formato `Wed Jan 02 02:03:55 1980\n\0`.  Se utiliza un reloj de 24 horas.  Todos los campos tienen un ancho constante.  El carácter de nueva línea y el carácter null ocupan las dos últimas posiciones de la cadena.  El valor pasado como segundo parámetro debe ser por lo menos éste grande.  Si es menor, un código de error, `EINVAL`, se devolverá.  
  
 `_wasctime_s` es una versión con caracteres anchos de `asctime_s`.  Por lo demás, `_wasctime_s` y `asctime_s` se comportan de forma idéntica.  
  
### Asignación rutinaria de Genérico\- texto  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tasctime_s`|`asctime_s`|`asctime_s`|`_wasctime_s`|  
  
 En C\+\+, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`asctime_s`|\<time.h\>|  
|`_wasctime_s`|\<time.h o\> wchar.h \<\>|  
  
## Seguridad  
 Si el puntero de búfer no es `NULL` y el puntero no señala a un búfer válido, la función sobrescribirá lo que haya en la ubicación.  Esto puede dar lugar a una infracción de acceso.  
  
 [saturación del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795) puede producirse si el argumento de tamaño pasado es mayor que el tamaño real del búfer.  
  
## Ejemplo  
 Este programa coloca la hora del sistema en `aclock`entero largo, la convierte en la estructura `newtime` y la convierte al formato de cadena para la salida, mediante la función de `asctime_s` .  
  
```  
// crt_asctime_s.c  
#include <time.h>  
#include <stdio.h>  
  
struct tm newtime;  
__time32_t aclock;  
  
int main( void )  
{  
   char buffer[32];  
   errno_t errNum;  
   _time32( &aclock );   // Get time in seconds.  
   _localtime32_s( &newtime, &aclock );   // Convert time to struct tm form.  
  
   // Print local time as a string.  
  
   errNum = asctime_s(buffer, 32, &newtime);  
   if (errNum)  
   {  
       printf("Error code: %d", (int)errNum);  
       return 1;  
   }  
   printf( "Current date and time: %s", buffer );  
   return 0;  
}  
```  
  
  **Fecha y hora actual: Miércoles 14 de mayo de 15: 30:17 2003**   
## Equivalente en .NET Framework  
  
-   <xref:System.DateTime.ToLongDateString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToLongTimeString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToShortDateString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToShortTimeString%2A?displayProperty=fullName>  
  
-   <xref:System.DateTime.ToString%2A?displayProperty=fullName>  
  
## Vea también  
 [Administración del tiempo](../../c-runtime-library/time-management.md)   
 [ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [\_tzset](../../c-runtime-library/reference/tzset.md)